https://kubernetes.io/docs/concepts/workloads/controllers/deployment/

```

# $ kubectl set image deployment/myapp-replicaset  nginx=nginx:1.16.1
deployment.apps/myapp-replicaset image updated
# $ kubectl get deployment/myapp-replicaset
NAME               READY   UP-TO-DATE   AVAILABLE   AGE
myapp-replicaset   3/3     1            3           14m
# $ kubectl rollout status -w deployment/myapp-replicaset
Waiting for deployment "myapp-replicaset" rollout to finish: 1 out of 3 new replicas have been updated...
Waiting for deployment "myapp-replicaset" rollout to finish: 1 out of 3 new replicas have been updated...
Waiting for deployment "myapp-replicaset" rollout to finish: 1 out of 3 new replicas have been updated...
Waiting for deployment "myapp-replicaset" rollout to finish: 2 out of 3 new replicas have been updated...
Waiting for deployment "myapp-replicaset" rollout to finish: 2 out of 3 new replicas have been updated...
Waiting for deployment "myapp-replicaset" rollout to finish: 2 out of 3 new replicas have been updated...
Waiting for deployment "myapp-replicaset" rollout to finish: 1 old replicas are pending termination...
Waiting for deployment "myapp-replicaset" rollout to finish: 1 old replicas are pending termination...
deployment "myapp-replicaset" successfully rolled out

$ kubectl set image deployment/myapp-replicaset  nginx=nginx:1.14.2 --record
Flag --record has been deprecated, --record will be removed in the future
$ kubectl rollout history deployment/myapp-replicaset 
deployment.apps/myapp-replicaset 
REVISION  CHANGE-CAUSE
1         <none>
2         <none>
3         <none>
4         <none>
5         kubectl set image deployment/myapp-replicaset nginx=nginx:1.14.2 --record=true

```

