### Deploy MongoDB and Mongo Express into local K8s cluster

### Technologies Used:

Kubernetes, Docker, MongoDB, Mongo Express

### Project Description:

1- Setup local K8s cluster with Minikube.

2-Deploy MongoDB and MongoExpress with configuration and credentials extracted into ConfigMap and Secret.

### Deployment Usage Instructions:

###### Step 1: Create mongo_secret.yaml file

1-generate base 64 encrypted username and password

```
echo -n "username" | base64
```

```
echo -n "password" | base64
```

2-create mongo secret by yaml file

```
kubectl apply -f mongo_secret.yaml
```

```
kubectl get secret
```

###### Step 2: Create mongo.yaml file for deployment component

1-create mongodb deployment

```
kubectl apply -f mongo.yaml
```

2-check status

```
kubectl get all
```

```
kubectl describe pod [pod_name]
```

###### Step 3: Add mongo service logic into mongo.yaml file and create mongo internal service

```
kubectl apply -f mongo.yaml
```

###### Step 4:Create mongo configmap file and create mongo express component

```
kubectl apply -f mongoExpress_configmap.yaml
```

###### Step 5: Add mongo-express service logic into mongoexpress.yaml file and create mongo-express external service

```
kubectl apply -f mongoExpress_configmap.yaml
```

###### Step 7: Get external service ip via minikube service

```
kubectl get service
```

![image](image/Screenshot%202023-03-02%20at%207.44.11%20pm.png)

```
minikube service mongo-express-service
```

![iamge](image/Screenshot%202023-03-02%20at%207.44.04%20pm.png)
