
### **Docker Commands Cheat Sheet**

#### **Container Management**
- **Run a container:**
  ```bash
  docker run -d -p 80:80 --name my_container my_image
  ```
- **List running containers:**
  ```bash
  docker ps
  ```
- **List all containers (including stopped):**
  ```bash
  docker ps -a
  ```
- **Start/Stop a container:**
  ```bash
  docker start <container_id>
  docker stop <container_id>
  ```
- **Remove a container:**
  ```bash
  docker rm <container_id>
  ```
- **Run a command in a running container:**
  ```bash
  docker exec -it <container_id> /bin/bash
  ```
- **View container logs:**
  ```bash
  docker logs <container_id>
  ```

#### **Image Management**
- **Build an image from a Dockerfile:**
  ```bash
  docker build -t my_image .
  ```
- **List images:**
  ```bash
  docker images
  ```
- **Remove an image:**
  ```bash
  docker rmi <image_id>
  ```
- **Pull an image from Docker Hub:**
  ```bash
  docker pull <image_name>
  ```
- **Push an image to Docker Hub:**
  ```bash
  docker push <image_name>
  ```

#### **Networking**
- **List Docker networks:**
  ```bash
  docker network ls
  ```
- **Create a new network:**
  ```bash
  docker network create my_network
  ```
- **Connect a container to a network:**
  ```bash
  docker network connect my_network <container_id>
  ```
- **Disconnect a container from a network:**
  ```bash
  docker network disconnect my_network <container_id>
  ```

#### **Volumes**
- **List volumes:**
  ```bash
  docker volume ls
  ```
- **Create a volume:**
  ```bash
  docker volume create my_volume
  ```
- **Mount a volume to a container:**
  ```bash
  docker run -d -v my_volume:/data my_image
  ```
- **Remove a volume:**
  ```bash
  docker volume rm my_volume
  ```

#### **Cleaning Up**
- **Remove all stopped containers:**
  ```bash
  docker container prune
  ```
- **Remove all unused images:**
  ```bash
  docker image prune
  ```
- **Remove all unused networks:**
  ```bash
  docker network prune
  ```
- **Remove all unused volumes:**
  ```bash
  docker volume prune
  ```

---

### **Docker Compose Commands Cheat Sheet**

#### **Basic Commands**
- **Start services defined in `docker-compose.yml`:**
  ```bash
  docker-compose up
  ```
- **Start services in detached mode:**
  ```bash
  docker-compose up -d
  ```
- **Stop services:**
  ```bash
  docker-compose stop
  ```
- **Stop and remove containers, networks, and volumes:**
  ```bash
  docker-compose down
  ```

#### **Service Management**
- **Build or rebuild services:**
  ```bash
  docker-compose build
  ```
- **View service logs:**
  ```bash
  docker-compose logs
  ```
- **Scale a service:**
  ```bash
  docker-compose scale web=3
  ```
- **Run a one-time command against a service:**
  ```bash
  docker-compose run <service_name> <command>
  ```

#### **Environment and Configuration**
- **Specify an alternate `docker-compose` file:**
  ```bash
  docker-compose -f <file_name>.yml up
  ```
- **Pass environment variables:**
  ```bash
  docker-compose up -e MY_VAR=value
  ```

---

### **Kubernetes Commands Cheat Sheet**

#### **Cluster Interaction**
- **View cluster information:**
  ```bash
  kubectl cluster-info
  ```
- **View Kubernetes nodes:**
  ```bash
  kubectl get nodes
  ```
- **View detailed information about a node:**
  ```bash
  kubectl describe node <node_name>
  ```

#### **Pod Management**
- **List all pods:**
  ```bash
  kubectl get pods
  ```
- **Create a pod from a YAML file:**
  ```bash
  kubectl apply -f pod.yaml
  ```
- **Delete a pod:**
  ```bash
  kubectl delete pod <pod_name>
  ```
- **View logs of a pod:**
  ```bash
  kubectl logs <pod_name>
  ```
- **Execute a command in a running pod:**
  ```bash
  kubectl exec -it <pod_name> -- /bin/bash
  ```

#### **Service Management**
- **List all services:**
  ```bash
  kubectl get svc
  ```
- **Expose a deployment as a service:**
  ```bash
  kubectl expose deployment <deployment_name> --type=LoadBalancer --name=my-service
  ```
- **Delete a service:**
  ```bash
  kubectl delete svc <service_name>
  ```

#### **Deployment Management**
- **List all deployments:**
  ```bash
  kubectl get deployments
  ```
- **Create a deployment from a YAML file:**
  ```bash
  kubectl apply -f deployment.yaml
  ```
- **Scale a deployment:**
  ```bash
  kubectl scale deployment <deployment_name> --replicas=3
  ```
- **Update a deployment:**
  ```bash
  kubectl set image deployment/<deployment_name> <container_name>=<new_image>
  ```
- **Rollback a deployment:**
  ```bash
  kubectl rollout undo deployment/<deployment_name>
  ```

#### **Namespace Management**
- **List all namespaces:**
  ```bash
  kubectl get namespaces
  ```
- **Create a namespace:**
  ```bash
  kubectl create namespace my-namespace
  ```
- **Delete a namespace:**
  ```bash
  kubectl delete namespace my-namespace
  ```

#### **ConfigMaps and Secrets**
- **Create a ConfigMap from a file:**
  ```bash
  kubectl create configmap my-config --from-file=config.properties
  ```
- **Create a Secret from literal values:**
  ```bash
  kubectl create secret generic my-secret --from-literal=username=user --from-literal=password=pass
  ```
- **View a ConfigMap:**
  ```bash
  kubectl get configmap my-config -o yaml
  ```
- **View a Secret (base64-encoded):**
  ```bash
  kubectl get secret my-secret -o yaml
  ```

#### **Persistent Volumes**
- **List all persistent volumes:**
  ```bash
  kubectl get pv
  ```
- **Create a persistent volume from a YAML file:**
  ```bash
  kubectl apply -f pv.yaml
  ```
- **Create a persistent volume claim from a YAML file:**
  ```bash
  kubectl apply -f pvc.yaml
  ```
- **Delete a persistent volume claim:**
  ```bash
  kubectl delete pvc <pvc_name>
  ```
