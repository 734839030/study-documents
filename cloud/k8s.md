### 参考文档

https://kubernetes.io/zh/docs/home/

#### 使用minikube 搭建单机集群

https://minikube.sigs.k8s.io/docs/start/

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
kubectl exec -it podId -n namespace  -- /bin/bash
# 查看pod 日志
kubectl logs -f podName -n namespace
# 获取全部资源
kubectl get all -n namespace -o wide
```

##### 编排

kind 说明yaml模板 https://kubernetes.io/zh/docs/tutorials/services/

yaml 参数大全:https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.20/#daemonset-v1-apps

##### 安装minikube

```
# linux 下需要建立用户
useradd kube
passwd kube
# 为了方便设置免密sudo
vim /etc/sudoers 
# 添加到docker 组
usermod -g docker kube
# 切换到kube
su - kube
#启动minikube 
minikube start
# 打开管理端
minikube dashboard
# 日志
minikube logs
# ip
minikube ip
# 查看服务的地址
minikube service --url serviceName  -n namespace
```

QA1: minikube start 22端口问题，遇到这个问题看这个https://github.com/kubernetes/minikube/issues/8163

```
# 查看安装时候错误日志
minikube start --alsologtostderr -v=1
minikube delete
minikube start
```

QA2:coredns pod crashloopback

```
# 先删除
minikube delete
minikube start --network-plugin=cni --cni=bridge
```



##### 自测使用

1. 在管理端右上角创建deployment
2. 创建service,默认服务暴露是LoadBalancer,在模拟环境还需要执行`minikube tunnel` 暴露主ip和服务端口

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

