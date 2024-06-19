# Set Web Proxy Settings via Terminal on MacOS

In order to set a web proxy on MacOS' terminal, we will use `networksetup` utility:
- First get list of network services
```
networksetup -listallnetworkservices
```
It will show a list like this:
```
An asterisk (*) denotes that a network service is disabled.
Thunderbolt Bridge
Wi-Fi
Freedom VPN
V2BOX
v4freedom
FoXray
```
From the output, we know that Wi-Fi is what we're looking for. 
- Next, set web proxy and secure web proxy as follows:
```
networksetup -setwebproxy Wi-Fi 127.0.0.1 19999
networksetup -setsecurewebproxy Wi-Fi 127.0.0.1 19999
```
That's it. You should be able to use the proxy now.
- If you want to turn off the proxy, use the following commands:

```
networksetup -setwebproxystate Wi-Fi Off
networksetup -setsecurewebproxystate Wi-Fi Off
```
Using `On` in the above commands will turn on the proxies.

## Using a Script to Automate Proxy Setting 
TODO




