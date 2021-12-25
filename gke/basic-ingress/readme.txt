Refer to  - 
Setup Kubernetes Ingress on GKE

https://devops4solutions.medium.com/setup-kubernetes-ingress-on-gke-441691b916
https://cloud.google.com/kubernetes-engine/docs/tutorials/http-balancer

Basic Ingress Testing 

1. Create the Kubernetes Cluster on Google Cloud.
2. Create ingress controller as described in devops4solutions.
   On GKE, we will run the below command which will create an ingress controller on our cluster
   kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v0.43.0/deploy/static/provider/cloud/deploy.yaml 

3. Initialize user as a cluster-admin with following command
Reference : https://kubernetes.github.io/ingress-nginx/deploy/#gce-gke
kubectl create clusterrolebinding cluster-admin-binding \
  --clusterrole cluster-admin \
  --user $(gcloud config get-value account)


5. kubectl get svc -n ingress-nginx 
   should show 2 services running.
   NAME                                 TYPE           CLUSTER-IP   EXTERNAL-IP     PORT(S)                      AGE
  ingress-nginx-controller             LoadBalancer   10.8.8.162   34.72.168.139   80:31226/TCP,443:30009/TCP   65s
  ingress-nginx-controller-admission   ClusterIP      10.8.0.40    <none>          443/TCP                      65s
 
6. kubectl get pods -n ingress-nginx
   should show 3 pods running.
   NAME                                        READY   STATUS      RESTARTS   AGE
   ingress-nginx-admission-create-vmjhp        0/1     Completed   0          2m3s
   ingress-nginx-admission-patch-w7xzl         0/1     Completed   0          2m2s
   ingress-nginx-controller-56c75d774d-dc8xz   1/1     Running     0          2m8s

7. kubectl apply -f web.yaml
8. kubectl apply -f basic-ingress.yaml
9. kubectl get ingress 
    once this command shows the public IP. chck that application is working fine
    by vising the ip address on web.

    

