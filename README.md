# Instructions
Deploy a backend-frontend app using Kubernetes. 

Backend: application that listens to a port and sends some response if a message comes there. Must be replicated.

Frontend: application that sends incoming requests to the backend.

Frontend must have an IP that can be used outside the cluster. Use Kubernetes Services. 
# Starting

1. Install minikube
   ```
   $ curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
   $ sudo install minikube-linux-amd64 /usr/local/bin/minikube
   ```
2. Install K8s Utility
   ```
   curl -LO https://storage.googleapis.com/kubernetes-release/release/`curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt`/bin/linux/amd64/kubectl

   chmod +x kubectl

   sudo mv kubectl /usr/local/bin/
   ```
3. Start Minkube and define static ip for Cluster
   For the correct operation of fronend
   Use ip as in the line below
   ```
   minikube start --driver docker --static-ip 192.168.49.2
   ```
5. Apply Manifests
 kubectl apply -f client-deployment.yaml -f client-service.yaml -f  server-deployment.yaml -f server-service.yaml
   
6. Open site
   http://192.168.49.2:30080/
