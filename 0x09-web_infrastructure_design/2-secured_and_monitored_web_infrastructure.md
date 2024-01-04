```
User Request
     |
     v
Firewall --> Load Balancer (HAproxy) --> Firewall
     |                 |
     +-----------------+
     |                 |
     v                 v
Firewall --> Web Server (Nginx) --> Firewall --> Monitoring Client
     |                 |
Application Server --> SSL Certificate
     |                 |
     v                 v
Database (MySQL) --> Monitoring Client
```

**Why are we adding these elements?**

1. **Firewalls**: Firewalls are added to protect internal networks and servers from threats on the internet. They block unauthorized access while permitting outward communication.

2. **SSL Certificate**: This is used to serve traffic over HTTPS, which encrypts the data between the client and the server. This prevents man-in-the-middle attacks and the exposure of sensitive information.

3. **Monitoring Clients**: These are used to collect data about the system and its performance. This data can be used to identify issues, understand user behavior, and optimize the system.

**Monitoring Tool Data Collection**

Monitoring tools collect data in various ways, including logs, system metrics, and application performance data. If you want to monitor your web server's Queries Per Second (QPS), you would typically look at the access logs of your web server.

**Issues with this Infrastructure**

1. **Terminating SSL at the Load Balancer**: This can be an issue because it means unencrypted traffic is sent between the load balancer and the servers. If someone gains access to that network, they could read or alter the data.

2. **Single MySQL Server Accepting Writes**: This can be a bottleneck. If there are too many write requests, the database may not be able to handle them all in a timely manner. It also means that if the database goes down, all write operations fail.

3. **Same Components on All Servers**: This can be a problem because it means all servers are potential targets for all types of attacks. It also means that an issue with one component (like a memory leak in the application server) could affect all servers.
