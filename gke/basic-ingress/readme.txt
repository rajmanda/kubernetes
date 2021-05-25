Refer to  - 
Setup Kubernetes Ingress on GKE


https://devops4solutions.medium.com/setup-kubernetes-ingress-on-gke-441691b916
https://cloud.google.com/kubernetes-engine/docs/tutorials/http-balancer

Basic Ingress Testing 

1. Create the Kubernetes Cluster on Google Cloud.
2. Initialize user as a cluster-admin with following command
Reference : https://kubernetes.github.io/ingress-nginx/deploy/#gce-gke
kubectl create clusterrolebinding cluster-admin-binding \
  --clusterrole cluster-admin \
  --user $(gcloud config get-value account)

3. Create ingress controller as described in devops4solutions.
4. kubectl get svc -n ingress-nginx 
   should show 2 services running.
5. kubectl get pods -n ingress-nginx
   should show 3 pods running.
6. kubectl apply -f web.yaml
7. kubectl apply -f basic-ingress.yaml
8. kubectl get ingress 
    once this command shows the public IP. chck that application is working fine
    by vising the ip address on web.

    

