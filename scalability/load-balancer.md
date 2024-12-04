# Load Balancers

## AWS Load Balancers

### Application Load Balancer (ALB)
- Operates at the application layer (OSI model layer 7).
- Ideal for HTTP and HTTPS traffic.
- Supports advanced routing, SSL termination, and WebSocket.

### Network Load Balancer (NLB)
- Operates at the transport layer (OSI model layer 4).
- Designed for high performance and low latency.
- Suitable for TCP, UDP, and TLS traffic.

### Classic Load Balancer (ELB)
- Operates at both the application and transport layers.
- Legacy load balancer, supports HTTP, HTTPS, TCP, and SSL.
- Suitable for simple load balancing of traffic across multiple EC2 instances.

## Open Source Load Balancers

### HAProxy
- High-performance TCP/HTTP load balancer.
- Supports SSL termination, sticky sessions, and advanced routing.
- Widely used in the industry for its reliability and performance.

### NGINX
- Can function as a web server, reverse proxy, and load balancer.
- Supports HTTP, HTTPS, TCP, and UDP load balancing.
- Known for its high performance, stability, and rich feature set.

## Azure Load Balancers

### Azure Load Balancer
- Operates at the transport layer (OSI model layer 4).
- Provides high availability and network performance.
- Supports inbound and outbound scenarios, low latency, and high throughput.

### Azure Application Gateway
- Operates at the application layer (OSI model layer 7).
- Provides application-level routing and load balancing.
- Supports SSL termination, URL-based routing, and Web Application Firewall (WAF).

## Google Cloud Load Balancers

### HTTP(S) Load Balancer
- Operates at the application layer (OSI model layer 7).
- Global load balancing for HTTP and HTTPS traffic.
- Supports SSL termination, URL-based routing, and auto-scaling.

### TCP/UDP Load Balancer
- Operates at the transport layer (OSI model layer 4).
- Provides regional load balancing for TCP and UDP traffic.
- Suitable for applications requiring high performance and low latency.

### Internal Load Balancer
- Operates at the transport layer (OSI model layer 4).
- Provides internal load balancing within a VPC.
- Ideal for distributing traffic among internal services.
