```

## Delete replicationcontroller

$ kubectl delete replicationcontroller myapp-rc
replicationcontroller "myapp-rc" deleted


## Delete Replicaset


kubectl delete rs myapp-replicaset
replicaset.apps "myapp-replicaset" deleted


## Create Deployment
kubectl create -f deployment.yaml 
deployment.apps/myapp-replicaset created
$ kubectl get deployments
NAME               READY   UP-TO-DATE   AVAILABLE   AGE
myapp-replicaset   3/3     3            3           10s
kubectl get rs
NAME                          DESIRED   CURRENT   READY   AGE
myapp-replicaset-68754995cf   3         3         3       15s
kubectl get pods
NAME                                READY   STATUS    RESTARTS   AGE
myapp-replicaset-68754995cf-4jlf8   1/1     Running   0          18s
myapp-replicaset-68754995cf-rxffx   1/1     Running   0          18s
myapp-replicaset-68754995cf-vzqht   1/1     Running   0          18s


## Defining a Service
A Service in Kubernetes is a REST object, similar to a Pod. Like all of the REST objects, you can POST a Service definition to the API server to create a new instance. The name of a Service object must be a valid RFC 1035 label name.

For example, suppose you have a set of Pods where each listens on TCP port 9376 and contains a label app=MyApp:

apiVersion: v1
kind: Service
metadata:
  name: my-service
spec:
  selector:
    app: MyApp
  ports:
    - protocol: TCP
      port: 80
      targetPort: 9376
      
This specification creates a new Service object named "my-service", which targets TCP port 9376 on any Pod with the app=MyApp label.

Kubernetes assigns this Service an IP address (sometimes called the "cluster IP"), which is used by the Service proxies (see Virtual IPs and service proxies below).

The controller for the Service selector continuously scans for Pods that match its selector, and then POSTs any updates to an Endpoint object also named "my-service".


## kubectl get deployment

NAME               READY   UP-TO-DATE   AVAILABLE   AGE
myapp-replicaset   3/3     3            3           128m


## $ kubectl expose deployment myapp-replicaset --type=NodePort --name=ex-nginx-service --port=80

service/ex-nginx-service exposed

## $ kubectl get svc

NAME               TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)        AGE
ex-nginx-service   NodePort    10.111.28.186   <none>        80:31027/TCP   14s
kubernetes         ClusterIP   10.96.0.1       <none>        443/TCP        2d6h
  
## $ minikube service --url ex-nginx-service
  
http://192.168.59.100:31027.   ---- access this url from browser.
  
  
  
 #### Service type LOADBALANCER
  
  
 LOADBALANCER https://kubernetes.io/docs/tutorials/hello-minikube/

```

