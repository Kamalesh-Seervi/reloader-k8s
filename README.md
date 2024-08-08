## Tools required:

- minikube
- reloader
- simple nginx app

## Minikube setup:

- Install the minikube and run the below command to start the kube.
```
minikube start
```
- For minikube dashboard:
```
minikube dashboard
```

## Reloader by stakater setup:

- Below is the manifests for reloader
```
kubectl apply -f https://raw.githubusercontent.com/stakater/Reloader/master/deployments/kubernetes/reloader.yaml
```
- I have added a annotation in `app_deployment.yaml` under metadata.
```
metadata:
  name: my-app
  annotations:
    reloader.stakater.com/auto: "true"
```
## App setup 

- Run the below commands to set the app
```
kubectl apply -f config_map.yaml
```
```
kubectl apply -f secret.yaml
```
```
kubectl apply -f app_deployment.yaml
```
```
kubectl apply -f service.yaml
```
- Access your application using Minikube's service command:
```
minikube service my-service
```
<img width="1552" alt="image" src="https://github.com/user-attachments/assets/1ea36a6d-f806-4748-bfaa-7232a9c2c7e5">

## Testing of the reloader

- Now go to the dashboard and change either secret or configmap data the pod will restarted automatically.

- From below diagram we can see that the app is create 27 mins ago now lets change and see the secret or configmap.

<img width="1162" alt="image" src="https://github.com/user-attachments/assets/7f4f6b8e-f9d0-4a01-8414-33845ce5a0f6">

- Now lets change and see the secret or configmap.

<img width="1162" alt="image" src="https://github.com/user-attachments/assets/3f8753de-8a9c-4338-ba18-62bd3a68951d">

- So now you can see that the pod has recently restarted.

<img width="1162" alt="image" src="https://github.com/user-attachments/assets/4e7861c0-7c2b-46e7-b817-0a00c5a8da0b">





