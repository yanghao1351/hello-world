```
minikube version
minikube status
minikube start
kubectl get pod,svc -n kube-system
kubectl create deployment hello-node --image=registry.cn-hangzhou.aliyuncs.com/yanghao1351/hello-node:1.0
kubectl get deployments
kubectl get deployment
kubectl get pods
kubectl get pod
kubectl get events
kubectl expose deployment hello-node --type=LoadBalancer --port=8080
kubectl get services
minikube service hello-node
curl -i http://192.168.99.119:30831/
minikube addons list
minikube addons enable heapster
minikube addons disable heapster
minikube stop
minikube delete

kubectl version
kubectl cluster-info
kubectl get nodes


kubectl action resource
kubectl create deployment
kubectl proxy


kubectl get - list resouces
kubectl describe - show detailed information about a resource
kubectl logs - print the logs from a container in a pod
kubectl exec - execute a command on a container in a pod
kubectl exec -ti $POD_NAME bash
kubectl expose deployment hello-node --type=LoadBalancer --port=8080
kubectl expose deployment/hello-node --type="NodePort" --port=8080
kubectl describe services/hello-node
kubectl get pods -l app=hello-node
kubectl lable pod hello-node-85484f7c56-wv4d5 version=0.1
kubectl describe pods hello-node-85484f7c56-wv4d5
kubectl delete service -l app=hello-node
kubectl get rs
kubectl scale deployments/hello-node --replicas=4
kubectl get pods -o wide
kubectl scale deployments/hello-node --replicas=2
kubectl set image deployments/hello-node hello-node=registry.cn-hangzhou.aliyuncs.com/yanghao1351/hello-node:v2
kubectl rollout status deployments/hello-node
kubectl rollout undo deployments/hello-node
```
```
apiVersion: v1
kind: Pod
metadata:
  name: redis
spec:
  containers:
  - name: redis
    image: redis:5.0.4
    command:
      - redis-server
      - "/redis-master/redis.conf"
    env:
    - name: MASTER
      value: "true"
    ports:
    - containerPort: 6379
    resources:
      limits:
        cpu: "0.1"
    volumeMounts:
    - mountPath: /redis-master-data
      name: data
    - mountPath: /redis-master
      name: config
  volumes:
    - name: data
      emptyDir: {}
    - name: config
      configMap:
        name: example-redis-config
        items:
        - key: redis-config
          path: redis.conf
```
```
maxmemory 2mb
maxmemory-policy allkeys-lru
```
