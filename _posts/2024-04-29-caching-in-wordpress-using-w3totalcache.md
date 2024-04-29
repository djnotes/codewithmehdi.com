# Caching in WordPress using W3 Total Cache

Caching in web applications is important because there are many requests sent to the server all the time and without good caching mechanisms, the performance of the site and users' browsing experience will not be optimal.

## W3 Total Cache
W3 Total Cache is a plugin that allows you to configure several types of caching mechanisms for your site. Once installed, it will show you a wizard guiding you through the configuration steps. The wizard consists of several parts the follow next.

### Page Cache
This speeds up Time to First Byte. There are several options e.g. Disk,Disk: Enhanced, Redis, etc. The recommended one is Disk: Enhanced as in my case, it shows the least amount of time in ms (22.49). 

### Database Cache
Database cache allows caching queries. The difference between the default database performance and cached ones is not significant, so we should leave it as None. 

### Object Cache
This cache allows reusing objects cached by WordPress during page renders. I choose Memcached here because it takes only 1.77 ms

### Browser Cache
This is an important setting that allows setting cache headers for assets, saving browsers from downloading assets like CSS and JS files on each page render. So, you should set it to Enabled.

### Image Optimization
Check Enable WebP Converter to convert image files to lightweight web-friendly format WebP, thus improve performance.

### Lazy Load
Check Lazy Load Images option to reduce page loads by deferring image loads until they are needed.
