Refer to  - 
Setup Kubernetes Ingress on GKE


https://devops4solutions.medium.com/setup-kubernetes-ingress-on-gke-441691b916
https://cloud.google.com/kubernetes-engine/docs/tutorials/http-balancer

Basic Ingress Testing 

1. Create the Kubernetes Cluster on Google Cloud.
2. Create ingress controller as described in devops4solutions.
3. kubectl get svc -n ingress-nginx 
   should show 2 services running.
4. kubectl get pods -n ingress-nginx
   should show 3 pods running.
5. kubectl apply -f web.yaml
6. kubectl apply -f basic-ingress.yaml
7. kubectl get ingress 
    once this command shows the public IP. chck that application is working fine
    by vising the ip address on web.

    

