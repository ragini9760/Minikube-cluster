# Install Docker
sudo apt update
sudo apt install -y docker.io
sudo systemctl enable docker --now
sudo usermod -aG docker $USER && newgrp docker

# Install kubectl & Minikube
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube
sudo apt install -y kubectl

minikube start --driver=docker
minikube status  # Verify all components show "Running"


kubectl apply -f deployment.yaml
kubectl apply -f service.yaml


here we can varify 
kubectl get pods                  # Check running pods
kubectl get deployments           # Verify deployment
kubectl get services              # See service details
minikube service my-service --url # Get access URL

Scale Your Application using replicas

kubectl scale deployment/my-app --replicas=3


kubectl get pods  # Now shows 4 pods

Debugging & Monitoring


kubectl describe pod/<pod-name>    # Detailed pod info
kubectl logs <pod-name>            # View logs
