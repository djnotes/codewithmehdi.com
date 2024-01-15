# How to Add a New Admin to WordPress from Database

So, you have access to a site's wordpress database and you want to add a new user with admin rights. Here are the steps: 

1- Create new user
`INSERT INTO wp_users (user_login, user_pass) VALUES ('your_username', 'your_password_hash')`

for obtaining `your_password_hash` search for WordPress hash on the Internet. Some sites do this. Enter your password and get your hash from them. then put the password hash in the above query. 

2- Add user's meta data:
(Imagine user's id in the above talbe is 100)
```
INSERT INTO wp_usermeta (user_id, meta_key, meta_value) VALUES (100, 'wp_user_level', 10);

INSERT INTO wp_usermeta (user_id, meta_key, meta_value) VALUES (100, 'wp_capabilities', 'a:1:{s:13:"administrator";b:1;}');

```
