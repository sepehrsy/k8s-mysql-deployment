# k8s-mysql-deployment
Deployment, Service, Ingress, PVC ...
#### deploy config
```
kubectl -n ns-name -f pvc.yml mysql-config-map.yml mysql-deployment.yml apply
```
### usable commands:
``` 
kubectl -n ns-name  describe pod pod-name
kubectl logs -f -n ns-name pod-name
kubectl exec -it -n ns-name pod-name /bin/bash
```
#### edit deploymnt example:
```
kubectl -n ns-name edit deployments.apps deployment_name
```
#### to edit voulme:
```
	volumeMounts:
        - mountPath: /etc/mysql/my.cnf
          name: mysql-config
          subPath: my.cnf
      volumes:
      - configMap:
          defaultMode: 420
          name: service-name-mysql-cm
        name: mysql-config
```
#### edit cm example:
```
kubectl -n ns-name edit/create cm pod-name
```
#### set LDAP auth to access k8s cluster, on client side:
```
mkdir -p $HOME/.kube
vim $HOME/.kube/config
sudo chown $(id -u):$(id -g) $HOME/.kube/config
mv config $HOME/.kube/config
```
#### to verify auth config:
```
kubectl -n crypto get pods
```



