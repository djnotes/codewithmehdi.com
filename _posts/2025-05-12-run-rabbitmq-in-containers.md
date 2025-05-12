---
layout: post
title:  "Running RabbitMQ in Linux Containers"
date:   2025-05-12 16:13:00 +0300
categories: development
---

# Run RabbitMQ in Linux Containers
RabbitMQ can be used for task queue management in applications that need some time to perform something. With containers, it's quite easy to start a group of RabbitMQ containers, some as workers, some as producers. Here, I will show how to create a setup with a single worker and a single producer. The worker will wait for messages from the queue and the producer will send messages to the worker through a queue.

*Note*: I will be using Podman to create and manage containers
0- Create env.ini with the following contents:   

```
[rabbitmq]
RABBITMQ_DEFAULT_USER=myuser
RABBITMQ_DEFAULT_PASS=mypass
RABBITMQ_DEFAULT_VHOST=rabbit1
```

1- Create Podman network:

```
podman create network rb
```

2- Create Worker container:

```
podman run -d --hostname rabbit1 --name rabbit1 -p 8080:15672 --env-file env.ini --network rb  docker.io/library/rabbitmq:3-management
```

3- Create producer container:

```
podman run -d --hostname rabbit2 --name rabbit2 --env-file env.ini --network rb docker.io/library/rabbitq:3
```

4- Enter the worker and install pika:

```
podman exec -ti rabbit1 bash
apt update && apt install -y python3-pika nano
```

5- Enter worker code:
While in the container, do:
```
mkdir code
cd code
nano server.py

#!/usr/bin/env python
import pika
import time

credentials = pika.PlainCredentials('myuser', 'mypass')
params = pika.ConnectionParameters('rabbit1', 5672, 'rabbit1', credentials)
connection = pika.BlockingConnection(
    params
)

channel = connection.channel()

channel.queue_declare(queue='task_queue', durable=True)
print(' [*] Waiting for messages. To exit press CTRL+C')


def callback(ch, method, properties, body):
    print(f" [x] Received {body.decode()}")
    time.sleep(body.count(b'.'))
    print(" [x] Done")
    ch.basic_ack(delivery_tag=method.delivery_tag)


channel.basic_qos(prefetch_count=1)
channel.basic_consume(queue='task_queue', on_message_callback=callback)

channel.start_consuming()

# Run the code
python3 server.py
```

6- Go inside producer container:

```
podman exec -ti rabbit2 bash
apt update && apt install -y python3-pika nano

mkdir code 
cd code
nano client.py


#!/usr/bin/env python
import pika
import sys

credentials = pika.PlainCredentials('myuser', 'mypass')
params = pika.ConnectionParameters('rabbit1', 5672, 'rabbit1', credentials)
connection = pika.BlockingConnection(
    params
)
channel = connection.channel()

channel.queue_declare(queue='task_queue', durable=True)

# Create a list of files to simulate list of operations
files = [
    'file1.mp3', 'file2.mp3', 'file3.mp3'
]

i = 0
while True:
    message = files[i%len(files)] # iterate over the list of files to simulate operations
    i = i+1
    channel.basic_publish(
        exchange='',
        routing_key='task_queue',
        body=message,
        properties=pika.BasicProperties(
            delivery_mode=pika.DeliveryMode.Transient
        ))
    print(f" [x] Sent {message}")
connection.close()

# Run the producer
python3 client.py
```

## See the management panel:

If you did all the above steps, then the management panel is available at the following address: 

```
http://localhost:8080
```

Once you opened the page, you will be asked for username and password. Enter `myuser` and `mypass`, the same values entered in env.ini file, respectively for this. After being authenticated, you will be able to see Overview, Connections, Channels, Exchanges, Queues and Streams and Admin sections, each of which contains valuable information.