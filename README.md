> What you will learn here, is what a reverse proxy is, how to set it up, and how you can secure it. I do my best to divide the subject into sections, divided by headers, so feel free to jump over a section, if you feel like it. I recommend reading the entire article one time first, before starting to set it up.

# What is NGINX ?

Nginx (pronounced "engine-x") is a widely used open-source web server and reverse proxy server software. It's designed to handle a variety of tasks related to serving web content, handling incoming traffic, and improving the performance and security of web applications. Originally developed to solve the "C10k problem" (handling 10,000 simultaneous connections), Nginx has evolved into a powerful and versatile tool for modern web development and server management.

# What is Reverse-proxy ?

A reverse proxy is a server or a software application that acts as an intermediary between clients (users or client applications) and backend servers. Unlike a forward proxy, which sits between clients and the internet to relay requests, a reverse proxy sits between clients and servers, receiving requests from clients and forwarding them to the appropriate backend servers.

# Here's how a reverse proxy works:
    1. Client Makes a Request
    2. Reverse Proxy Receives Request
    3. Request Routing
    4. Forwarding the Request
    5. Backend Server Responds
    6. Reverse Proxy Sends Response to Client

Follow below steps to configure Nginx docker with reverse proxy setup.

1. Create a Docker network for the environment.
```
sudo docker network create nginx-docker-network
```
2. For starting nginx we have to first start the over app in custom network then after we have to start nginx.Below command start the demo application.
```
cd ./demo-app
``` 
```
sudo docker-compose up -d
```
3. Once the application is successfully launched, ensure its functionality by checking your cmd. Utilize the following command to verify its operation:
```
curl http://<your-ip-address>:49160
```
If you see hello world then demo app working perfectly.
4. Starting Nginx and Configuring Server Proxy.
To proceed, we'll initiate the Nginx service. Prior to that, it's necessary to make adjustments to the configuration file. Follow these steps:

A. Open the configuration file using the Nano text editor:
```
nano ./conf/nginx.conf
```
B. Within this file, locate the placeholder <your-server-name-here>. Replace it with either your server's IP address or its DNS name. This alteration will enable Nginx to effectively execute the proxy function."
