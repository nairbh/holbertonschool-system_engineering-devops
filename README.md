Web infrastructure design

## Learning Objectives


## What is a server?
A server is a computer or system that provides services or resources to other computers, known as clients, over a network. In the context of web infrastructure, a server refers to a physical or virtual machine that hosts and delivers web applications and content to users.

## What is the role of the domain name?
A domain name is a unique address that identifies a website on the internet. It serves as a user-friendly and memorable way to access web resources. The role of a domain name is to provide a human-readable name that can be associated with the IP address of the server hosting the website. It enables users to access the website using a recognizable name (e.g., www.foobar.com) instead of the IP address.

##  What type of DNS record is www in www.foobar.com?
The "www" in www.foobar.com is a subdomain. It is typically used as a common prefix to indicate the World Wide Web service of a domain. In DNS (Domain Name System), a subdomain is a way to organize and differentiate various services or sections of a website. It is associated with an A or CNAME record that maps it to an IP address or another domain name.

## What is the role of the web server?
The web server is responsible for handling HTTP requests from clients (such as web browsers) and serving web content in response. It receives requests for web pages, files, or other resources, processes those requests, and sends the corresponding responses back to the clients. The web server manages the communication between the client and the web application running on it.

## What is the role of the application server?
The application server is responsible for executing the backend logic and processing the dynamic components of a web application. It hosts the application code and provides the necessary environment to run and manage the application. The application server handles business logic, database interactions, and other application-specific tasks, generating dynamic content that the web server can deliver to clients.

## What is the role of the database?
The database stores and manages the structured data used by the web application. It is responsible for efficiently storing, retrieving, and manipulating data requested by the application. The database allows the web application to persist and manage information such as user profiles, product data, and other relevant data for the application's functionality.

## What is the server using to communicate with the computer of the user requesting the website?
The server communicates with the computer of the user requesting the website using the HTTP (Hypertext Transfer Protocol) protocol. When a user types a URL or clicks on a link, the client's web browser sends an HTTP request to the server, specifying the resource it wants to access. The server processes the request and sends back an HTTP response containing the requested resource or an appropriate error message.

## Issues with this infrastructure:

## Single Point of Failure (SPOF):
Having a single server means that if it fails or experiences issues, the entire website becomes unavailable. There is no redundancy or backup server to handle traffic if the primary server fails, leading to a potential loss of service.

## Downtime during maintenance:
Performing maintenance tasks such as deploying new code or updating the web server requires restarting the server. During this maintenance window, the website may experience downtime, causing temporary unavailability to users.

## Scalability limitations:
With only one server, the infrastructure may struggle to handle a significant increase in incoming traffic. As the traffic grows, the server's resources can become overwhelmed, resulting in slower response times and potential performance issues. Scaling the infrastructure to handle higher traffic requires additional servers and load balancing mechanisms.

It's important to address these issues by implementing solutions like load balancing, redundancy, and fault tolerance to ensure high availability, scalability, and resilience in the web infrastructure.
