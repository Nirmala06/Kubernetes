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



