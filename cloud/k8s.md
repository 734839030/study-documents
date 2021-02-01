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

QA: minikube start 22端口问题，遇到这个问题看这个https://github.com/kubernetes/minikube/issues/8163

```
docker system prune 
minikube delete
minikube start --driver=docker
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

##### Helm 使用（一组deployments,pod ,service的安装集合）

```
# 更换源
helm repo remove stable
helm repo add stable https://kubernetes.oss-cn-hangzhou.aliyuncs.com/charts
helm repo update
helm search
# 添加源例子
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts


# 搜索镜像
 helm search repo kibana
# 安装 例子helm install mykibana stable/kibana --namespace study  ,不加命名空间是defaut
helm install 名字 charname  [--namespace namespace]

# 查看安装
helm list
```

