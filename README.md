# aws_lb_controller-astro
How to install Software on EKS + AWS LoadBalancer controller

!! NOTE: AWS LoadBalancer controller acts as ingress controller and creates LB for every ingress object, you dont need to have separate ingress controller for example Nginx, Traefik, etc

!! NOTE: If you need to use TLS (and we do for our endpoints), the certificate must be issued by ACM
	(AWS Load Balancer Controller can be used without ACM certificate, but only for plain HTTP (non-TLS) )

	1. HTTPS (TLS) using ALB does require a valid ACM certificate in the same region as your cluster.
	2. ALB does not support Kubernetes TLS secrets for HTTPS.
	3. Only ACM certificates can be attached to ALB listeners for HTTPS.
	4. It doesnt work with self signed certs/let's encrypt, etc in case we need to use TLS
	5. Each endpoint(ingress) has a separate LB and DNS for that LB, not very rational

