![331125_630361](https://user-images.githubusercontent.com/124582867/229380110-7673c718-e712-4ac6-aa56-c816d5535188.png)

Web infrastructure design

## Learning Objectives


## What is a server?
- A server is a computer or system that provides services or resources to other computers, known as clients, over a network. In the context of web infrastructure, a server refers to a physical or virtual machine that hosts and delivers web applications and content to users.

## What is the role of the domain name?
- A domain name is a unique address that identifies a website on the internet. It serves as a user-friendly and memorable way to access web resources. The role of a domain name is to provide a human-readable name that can be associated with the IP address of the server hosting the website. It enables users to access the website using a recognizable name (e.g., www.foobar.com) instead of the IP address.

##  What type of DNS record is www in www.foobar.com?
- The "www" in www.foobar.com is a subdomain. It is typically used as a common prefix to indicate the World Wide Web service of a domain. In DNS (Domain Name System), a subdomain is a way to organize and differentiate various services or sections of a website. It is associated with an A or CNAME record that maps it to an IP address or another domain name.

## What is the role of the web server?
- The web server is responsible for handling HTTP requests from clients (such as web browsers) and serving web content in response. It receives requests for web pages, files, or other resources, processes those requests, and sends the corresponding responses back to the clients. The web server manages the communication between the client and the web application running on it.

## What is the role of the application server?
- The application server is responsible for executing the backend logic and processing the dynamic components of a web application. It hosts the application code and provides the necessary environment to run and manage the application. The application server handles business logic, database interactions, and other application-specific tasks, generating dynamic content that the web server can deliver to clients.

## What is the role of the database?
- The database stores and manages the structured data used by the web application. It is responsible for efficiently storing, retrieving, and manipulating data requested by the application. The database allows the web application to persist and manage information such as user profiles, product data, and other relevant data for the application's functionality.

## What is the server using to communicate with the computer of the user requesting the website?
- The server communicates with the computer of the user requesting the website using the HTTP (Hypertext Transfer Protocol) protocol. When a user types a URL or clicks on a link, the client's web browser sends an HTTP request to the server, specifying the resource it wants to access. The server processes the request and sends back an HTTP response containing the requested resource or an appropriate error message.

## Issues with this infrastructure:

## Single Point of Failure (SPOF):
- Having a single server means that if it fails or experiences issues, the entire website becomes unavailable. There is no redundancy or backup server to handle traffic if the primary server fails, leading to a potential loss of service.

## Downtime during maintenance:
- Performing maintenance tasks such as deploying new code or updating the web server requires restarting the server. During this maintenance window, the website may experience downtime, causing temporary unavailability to users.

## Scalability limitations:
- With only one server, the infrastructure may struggle to handle a significant increase in incoming traffic. As the traffic grows, the server's resources can become overwhelmed, resulting in slower response times and potential performance issues. Scaling the infrastructure to handle higher traffic requires additional servers and load balancing mechanisms.

- It's important to address these issues by implementing solutions like load balancing, redundancy, and fault tolerance to ensure high availability, scalability, and resilience in the web infrastructure.

###  Distributed web infrastructure

## Additional elements and their purpose:
1- Load Balancer: The load balancer is added to distribute incoming traffic across multiple servers to improve performance, scalability, and availability. It helps evenly distribute requests among the web servers and ensures that no single server is overwhelmed with traffic.
- Firewall: A firewall is essential for security purposes. It acts as a barrier between the server and the internet, controlling incoming and outgoing network traffic based on predefined security rules. It helps protect against unauthorized access, malicious attacks, and other security threats.
HTTPS: HTTPS (HTTP Secure) is a protocol that adds an extra layer of security by encrypting the communication between the web server and the client's browser. It ensures that data transmitted between the server and the user is encrypted and protected from interception or tampering.

2- Load balancer distribution algorithm:
The load balancer can be configured with various distribution algorithms, such as Round Robin, Least Connections, or IP Hashing. Each algorithm has its own way of distributing traffic. For example:
- Round Robin: Requests are distributed equally among the servers in a cyclic manner.
- Least Connections: Requests are sent to the server with the fewest active connections.
- IP Hashing: The client's IP address is used to determine which server should handle the request.
3- Active-Active vs. Active-Passive setup:
- Active-Active: In an Active-Active setup, multiple servers are actively serving traffic simultaneously. They share the load and can handle requests independently. This setup provides better scalability and availability as all servers are actively participating in serving requests.
- Active-Passive: In an Active-Passive setup, one server (active) handles the incoming traffic while the other server (passive) remains idle or serves as a backup. If the active server fails, the passive server takes over. This setup provides redundancy and failover capabilities but may underutilize resources during normal operation.
4- Primary-Replica (Master-Slave) database cluster:
- In a Primary-Replica database cluster, the primary node (master) is responsible for handling write operations and maintaining the current state of the database. The replica nodes (slaves) replicate the data from the primary node and handle read operations. The primary node receives write requests, updates its state, and then replicates the changes to the replica nodes. This setup improves performance, allows for high availability, and provides data redundancy.

5- Difference between Primary and Replica nodes:

- Primary Node: The primary node is the main node responsible for processing write operations and maintaining the current state of the database. It receives write requests, updates the data, and replicates the changes to the replica nodes. The primary node ensures data consistency and integrity.
- Replica Node: The replica nodes replicate the data from the primary node and handle read operations. They serve as backups and can take over as the primary node in case of failure. Replica nodes are used for scaling read operations, improving performance, and providing fault tolerance.

6- Issues with the infrastructure:

- Single Point of Failure (SPOF): The infrastructure still has potential single points of failure, such as the single load balancer, single firewall, and single database primary node. If any of these components fail, it can cause service disruption.
- Security issues: The lack of a firewall and HTTPS poses security risks. Without a firewall, the infrastructure is vulnerable to unauthorized access and malicious attacks. The absence of HTTPS leaves the communication between the server and the client's browser unencrypted, making it susceptible to interception and data tampering.
7- No monitoring: The absence of a monitoring system prevents real-time visibility into the health and performance of the infrastructure. Without monitoring, it becomes challenging to detect and address issues promptly, leading to potential downtime or degraded performance.
- It's important to address these issues by implementing redundancy, fault tolerance, security measures, and a robust monitoring system to ensure high availability, scalability, security, and efficient operation of the web infrastructure.

###  Secured and monitored web infrastructure

1- additional elements and the specific issues with the infrastructure:

## Additional elements and their purpose:
1- Load Balancer: The load balancer is added to distribute incoming traffic across multiple servers to improve performance, scalability, and availability. It helps evenly distribute requests among the web servers and ensures that no single server is overwhelmed with traffic.
- Firewall: A firewall is added for security purposes. It acts as a barrier between the server and the internet, controlling incoming and outgoing network traffic based on predefined security rules. It helps protect against unauthorized access, malicious attacks, and other security threats.
- HTTPS: HTTPS (HTTP Secure) is used to serve the traffic securely over an encrypted connection. It ensures that the data transmitted between the server and the client's browser is encrypted, preventing unauthorized access, data interception, and tampering.
Monitoring: Monitoring is used to track the performance, availability, and health of the infrastructure components. It helps identify issues, monitor resource utilization, detect anomalies, and ensure optimal system performance.
- Monitoring Tool: The monitoring tool collects data by periodically querying various metrics from the infrastructure components such as CPU usage, memory usage, network traffic, disk utilization, response times, and error rates. It aggregates and visualizes this data for analysis and alerting.
2- Monitoring web server QPS:
To monitor the web server's QPS (Queries Per Second), you can configure the monitoring tool to collect metrics related to incoming requests and calculate the average number of queries per second over a specific time period. This can be achieved by monitoring metrics such as request count, response time, and throughput. By analyzing these metrics, you can track the performance of your web server and ensure it can handle the expected load.

3- Issues with the infrastructure:

- Terminating SSL at the load balancer level: Terminating SSL at the load balancer means that the SSL/TLS encryption and decryption process happens at the load balancer instead of the web server. This can be an issue because it adds extra overhead to the load balancer, affecting its performance and scalability. Additionally, it may limit the ability to perform advanced web server-specific tasks such as handling client certificates or accessing client IP addresses.
- Having only one MySQL server capable of accepting writes: Having a single MySQL server capable of accepting write operations introduces a single point of failure and limits the system's ability to handle high write loads. If the MySQL server fails, it can result in data loss or service downtime. It's recommended to implement a replication setup with multiple MySQL servers to ensure data redundancy, fault tolerance, and scalability.
- Having servers with all the same components (database, web server, and application server): This might be a problem because it lacks component isolation and increases the impact of a failure. If a specific component, such as the database, experiences issues, it can affect all servers in the infrastructure. It's beneficial to distribute the components across multiple servers, allowing for better fault isolation, improved performance, and scalability.


###  Scale up

## Additional elements and their purpose:
1- Load Balancer (HAproxy): The load balancer is added to distribute incoming traffic across multiple servers in a cluster. It improves scalability, availability, and performance by evenly distributing requests among the servers. The load balancer acts as a single entry point for clients and forwards the requests to the appropriate backend servers (web servers or application servers) based on predefined load-balancing algorithms.
- Split Components: The infrastructure is split into separate servers for web server, application server, and database. This separation allows for better resource utilization, scalability, and fault isolation. Each component can be optimized and scaled independently based on its specific requirements. It also improves security by limiting access to specific servers based on the component's role.
2- Explanation for adding each additional element:
- Load Balancer: The load balancer is added to handle the increased traffic and distribute it efficiently among multiple servers. It ensures that no single server is overwhelmed and provides high availability by redirecting requests to healthy servers in case of failures.
- Separate Servers for Components: By separating the components onto their own servers, it allows for better resource management and scalability. Each component can be optimized and scaled independently based on its specific needs. For example, the web server can focus on handling HTTP requests and serving static content, while the application server can focus on processing business logic and dynamic content. The separate database server allows for dedicated resources and improved performance for database operations.

- Overall, these additional elements in the infrastructure help improve scalability, availability, and performance by distributing the workload across multiple servers and allowing each component to be optimized individually. It ensures efficient resource utilization and better fault tolerance.

### Authors

<div align="center">
    <a href="https://github.com/nairbh">
        <img src="https://zupimages.net/up/23/21/rskr.jpeg" alt="Nairbh" width="150" height="150" style="border-radius: 50%;">
    </a>
    <br>
    <a href="https://github.com/nairbh" style="color: blue;"><strong>Nairbh</strong></a>
</div>
