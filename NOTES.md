## Minikube Bootstrap

We need the ingress controller for routing. 

```sh
minikube addons enable ingress
```

Now we can see it:

```sh
         kubectl get pods -n ingress-nginx
         NAME                                        READY   STATUS      RESTARTS   AGE
         ingress-nginx-admission-create-wqbqb        0/1     Completed   0          15m
         ingress-nginx-admission-patch-g58p7         0/1     Completed   0          15m
here --> ingress-nginx-controller-596f8778bc-bwx65   1/1     Running     0          15m
```

See the service:

```sh
kubectl get svc -n ingress-nginx
NAME                                 TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)                      AGE                                                                        ingress-nginx-controller             NodePort    10.110.88.249   <none>        80:31435/TCP,443:30602/TCP   16m
ingress-nginx-controller-admission   ClusterIP   10.100.205.25   <none>        443/TCP                      16m
```

The NodePort is the one we use to route to. That is port 30602. Combined with the minikube IP:

```sh
minikube ip
192.168.49.2
```

We could route the from the host using 192.168.49.2:30602.
