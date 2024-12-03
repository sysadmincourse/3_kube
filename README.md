# 3, 4 Kubernetes

## Дасгал 1

Дараах хэрэгслүүдийг суулга.
  1. [kubectl суулга](https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/)
  2. minikube суулга. Эхлээд docker суулгасан байх шаардлагатай. Системд бага ачаалал өгөх үүднээс minikube-ийн backend-ийг docker дээр байршуулъя.
  ```shell
  curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube && rm minikube-linux-amd64
  minikube start --driver=docker
  ```
## Дасгал 2

nginx:1.24.0 хувилбараар 3 replica ажиллуулах deployment үүсгэ.
Deployment амжилттай ажилласан эсэхийг дараах командуудаар шалга.
```shell
kubectl get pods
kubectl get deployment
```

## Дасгал 3

Дасгал 2 дээр үүсгэсэн deployment-ийн pod-ийн image-ийг nginx:1.26.2 хувилбараар сольж rollout-ийг нэг нэгээр хий.

Image солигдсон эсэхийг дараах командаар нягтал.
```shell
kubectl describe pod <pod-ийн нэр>
```

## Дасгал 4

8080, 8081 гэсэн портууд дээр хоёр nginx веб сервер дотроо ажиллуулах pod template-тэй replica=4 байх deployment үүсгэн ажиллуул.

## Дасгал 5

Persitent Volume-тэй StatefulSet үүсгэ. Pod-ууд нь nginx веб сервер асаах бөгөөд replica=3 байна.
