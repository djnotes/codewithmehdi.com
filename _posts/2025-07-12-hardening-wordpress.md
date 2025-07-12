---
layout: post
title:  "Hardening WordPress"
date:   2025-07-12 15:40:00 +0300
categories: development
---

# Hardening WordPress

There has been many instances of website hijacking for many WordPress site owners. The root cause is wrong permissions set on WordPress core files. Here's a general step by step process to harden your WordPress installation and prevent it from being hijacked by asshole hackers. 

## Steps 

To prevent security vulnerabilities and hijack attacks, it's important to give appropriate permissions to WordPress files. 
The rule of thumb is no file must be given more permission than it needs or you might end up getting screwed. 
My WP hardening involves a several-step process (For NGINX):

- DS=/var/www/html/public_html
- Set ownership to a SSH user: sudo chown -R myuser:www-data \$DS
- Set 755 permissions on directories: find \$DS -type d -exec chmod 755 {} \; 
- Set 744 permissions on files:  find \$DS -type f -exec chmod 744 {} \;
- Allow read, write and execute on uploads: chmod -R 775 \$DS/wp-content/{uploads,themes,plugins,upgrade}

## Additional Notes
-  with these permissions, it is not possible to upgrade WordPress core. It is recommended to perform core upgrade only manually 
under a user with sufficient permissions on the core files, possibly by using WP CLI or manual copy and move operations.
- Despite our hardening efforts, try to stick to keeping user logins secure 
