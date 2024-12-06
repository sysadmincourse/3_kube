# 3 Kubernetes

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

Persitent Volume-тэй StatefulSet үүсгэ. Pod-ууд нь nginx веб сервер асаах бөгөөд replica=3 байна. Retention policy нь delete байна. Үүний дараагаар ямар pvc, ямар pv-тэй холбогдож ашиглагдаж байгааг хар.
```shell
kubectl get pvc
kubectl get pv
```
Эцэст нь scale=0 болоход ямар ч volume үлдэхгүй устаж байгаад баталгаажуулж хар.

## Дасгал 6

Өмнөх үүсгэсэн stateful сэтүүд дээр service үүсгэж, сервисийн нэрээр хандах боломж өг.

## Дасгал 7

Шинээр nginx deployment үүсгэ. Ингэхдээ index.html болон /etc/nginx/nginx.conf файлын доторхыг configmap ашиглан өөрчил нүү.

## Дасгал 8

Дараах дасгалыг хийнэ үү.
  1 .docker даалгавар дээр хийсэн index.html-ийг сольсон image-ийг gitlab дээр үүсгэсэн рeпoгийн регистерт нэм.
  2. Үүний дараагаар gitlab-д нэвтрэх deployment ssh түлхүүр үүсгээд, үүнийг kubernetes secret объект болгон үүсгэнэ. 
  3. Үүсгэсэн secret-ээ ашиглан өөрийн контейнер image-ээс deployment үүсгэнэ.
  4. Үүсгэсэн deployment дээрээ loadbalancer-тэй шинэ сервес нэмээд ip хаягаар хандаж хар. minikube дээр minikube tunnel асаах шаардлагатай гэдгийг анхаар.
  5. Дээр нэмээд gateway үүсгэн nginx сервистэйгээ холбоорой.

## Дасгал 9

Энэ [tutorial-ийн](https://kubernetes.io/docs/tutorials/stateful-application/mysql-wordpress-persistent-volume/) дагуу wordpress ажиллуул.


