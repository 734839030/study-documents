### 参考文档

https://kubernetes.io/zh/docs/home/

#### 使用minikube 搭建单机集群

https://minikube.sigs.k8s.io/docs/start/

##### 先安装minikube

```
#启动minikube 
minikube start
# 打开管理端
minikube dashboard
```

##### 自测使用

1. 在管理端右上角创建deployment
2. 创建service,默认服务暴露是LoadBalancer,在模拟环境还需要执行minikube tunnel 暴露主ip和服务端口

##### 安装kubectl

https://kubernetes.io/zh/docs/tasks/tools/install-kubectl/

```
# 查看pod
kubelctl get pods [-A(全部空间)] [--namespace 指定命名空间] [-o wide]
# 查看服务
kubectl get services [-A(全部空间)] [--namespace 指定命名空间] [-o wide]
kubectl get nodes [-A(全部空间)] [--namespace 指定命名空间] [-o wide]
kubectl get rs [-A(全部空间)] [--namespace 指定命名空间] [-o wide]

# 进入pod
kubectl exec -it podId -- /bin/bash
```

