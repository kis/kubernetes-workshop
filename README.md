Kubectl / Create Kubernetes Deployment
https://kubernetes.io/docs/tutorials/hello-minikube/

Kubernetes cluster
https://learnk8s.io/nodejs-kubernetes-guide

There are several ways to create a Kubernetes cluster:
* Using a managed Kubernetes service like Google Kubernetes Service (GKE), Azure Kubernetes Service (AKS), or Amazon Elastic Kubernetes Service (EKS)
* Installing Kubernetes yourself on cloud or on-premises infrastructure with a Kubernetes installation tool like kubeadm or kops
* Creating a Kubernetes cluster on your local machine with a tool like Minikube, MicroK8s, or k3s

————
BEFORE IT

App runs on 3000 port

——————
# Dockerfile
FROM node:10.0.0-alpine
COPY . ./app
WORKDIR /app
RUN npm install
CMD ["npm", "start"]
——————

docker build -t myapp .
docker run -it -p 8080:3000  myapp

docker-compose up -d

Docker hub
push to 
https://ropenscilabs.github.io/r-docker-tutorial/04-Dockerhub.html
https://hub.docker.com/repository/docker/kiqs/myapp/general

Or push to quay

Docker ps
Docker images
docker tag bb38976d03cf kiqs/verse_gapminder:firsttry
docker push kiqs/verse_gapminder

docker pull quay.mckinsey-solutions.com/kyryl_stopkin/my-app

docker tag e4461cb0f04d quay.mckinsey-solutions.com/kyryl_stopkin/my-compose-app_web
docker push quay.mckinsey-solutions.com/kyryl_stopkin/my-compose-app_web

docker tag —— quay.mckinsey-solutions.com/kyryl_stopkin/my-compose-app_backend
docker push quay.mckinsey-solutions.com/kyryl_stopkin/my-compose-app_backend


PORT 3000
—————

kubectl create deployment myapp --image=docker.io/kiqs/myapp
kubectl create -f kyryl-stopkin-secret.yml
kubectl create -f solution.yml
kubectl apply -f helm-rbac.yaml
kubectl delete -f solution.yml
		
kubectl get secrets

docker login -u="kyryl_stopkin" -p="6NCXCaeo99VtjgowAqIFBh9RK/28nL3bY+1VHu51AT2XeJJkPeopUVejDOxrp87o" quay.mckinsey-solutions.com

kubectl get deployments
kubectl get services
kubectl get pods
kubectl get po
kubectl get events
kubectl config view
kubectl expose deployment my-compose-app --type=LoadBalancer --port=3000
kubectl expose deployment my-compose-app --type=LoadBalancer
kubectl delete service my-compose-app
kubectl delete deployment my-compose-app

kubectl proxy
kubectl cluster-info
kubectl exec zk-0 cat /usr/etc/zookeeper/log4j.properties
kubectl exec -ti kube-foo-app-7669fdc456-qtlxd bash
kubectl logs <pod> <container_name>
kubectl logs zk-0 --tail 20
kubectl scale deployment frontend --replicas=2

Specify port in solution.yml
This exposes service from deployment

————

CHECK NEXT TIME

minikube start --vm-driver=hyperkit
minikube start --vm-driver=hyperkit --cpus=4 --memory=4096 --disk-size=30g
minikube start --vm-driver=hyperkit --cpus=4 --memory=4096 --disk-size=30g --kubernetes-version=1.15.4
minikube addons enable ingress
minikube service list
minikube service list | grep my
minikube service my-compose-app
minikube delete
minikube dashboard
minikube ip

——
https://www.baeldung.com/kubernetes-helm

kubectl apply -f helm-rbac.yaml

Couldn’t find a tiller

minikube delete
minikube start --vm-driver=hyperkit --cpus=4 --memory=4096 --disk-size=30g --kubernetes-version=1.15.4
helm init

helm create kub-web-chart

helm template ./my-app
helm install --name my-app-web ./my-app-web
helm ls --all my-app
helm ls

helm upgrade my-app-web ./my-app-web
helm rollback hello-world 1
helm delete --purge my-app-web

——
Delete deployment then upgrade help app

——

imagePullSecrets:
        - name: {{ .Values.image.pullSecretName }}

Before containers

minikube service list
helm upgrade my-app-web ./my-app-web