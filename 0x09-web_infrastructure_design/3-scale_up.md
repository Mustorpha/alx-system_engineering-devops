```
User Request
     |
     v
Load Balancer (HAproxy) Cluster
     |
     +-----------------+-----------------+-----------------+
     |                 |                 |                 |
     v                 v                 v
Web Server (Nginx)  Application Server  Database (MySQL)
(Server 1)          (Server 2)          (Server 3)
```

**Why are we adding these elements?**

1. **Additional Server**: We add an additional server to distribute the load and to provide redundancy. If one server fails, the other can still serve user requests, reducing the risk of downtime.

2. **Load Balancer (HAproxy) Cluster**: This distributes incoming requests to the servers to ensure no single server becomes a bottleneck. Configuring it as a cluster with another load balancer provides high availability and failover support.

3. **Split Components**: Splitting the web server, application server, and database each into their own server allows each component to be scaled, maintained, and secured independently. This can lead to better performance, easier troubleshooting, and increased security.

**Web Server vs Application Server**

A **web server** serves static content to a client's browser over HTTP. Examples of static content include HTML pages, CSS stylesheets, and JavaScript files. A web server can also act as a reverse proxy server for HTTP requests to an application server.

An **application server** serves dynamic content by running an application and generating content on-the-fly to send to the web server. This content is usually in the form of HTML pages generated from templates and data from a database.
