# envoy-generic-forward-proxy
Configure Envoy as Generic Forward Proxy for web traffic

Envoy is a high performance, small footprint edge and service proxy written in C++. It was developed at Lyft and is increasingly being 
used in microservice deployments as a sidecar process with each service. It adds resilience and observability to the services. It is an 
equally capable Edge proxy, where it acts as primary load balancer for traffic entering via the internet.  

However, most common deployments would involve deploying Envoy as edge proxy for a microservices backend, with a sidecar envoy proxy 
running hand-in-hand with each service. What if you wanted to use envoy as a front proxy for generic web traffic? This is an interesting 
deployment model, where you could use the extensible framework of envoy to add new capabilities or use existing capabilities such as 
rate-limiting or RBAC. 

This repository includes a simple envoy configuration to get you exactly that. It uses the ORIGINAL_DST Cluster type + iptables to get the
downstream address. The envoy configuration in conjunction with an iptables REDIRECT rule enables Envoy to run as a generic web proxy
