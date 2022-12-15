# Learn How to Monitor Kubedoom on Grafana

## Installation

1. Tambahkan helm repository Helm kubeinvaders
```bash
$ helm repo add kubeinvaders https://lucky-sideburn.github.io/helm-charts/
```

2. Buat namespace kubeinvaders
```bash
$ kubectl create namespace kubeinvaders
```

3. Buat namespace target
```bash
$ kubectl create namespace netclass
```

4. Install kubeinvaders dengan tambahan konfigurasi tambahan namespace target
```bash
$ helm install kubeinvaders --set-string target_namespace="netclass" \
-n kubeinvaders kubeinvaders/kubeinvaders --set ingress.hostName=netclass.pod --set image.tag=v1.9
```

5. Update helm repository
```bash
$ helm repo update
```

6. Install package helm nginx-ingress
```bash
$ helm install nginx-ingress ingress-nginx/ingress-nginx
```

7. Edit Ingress
```txt
# kubectl.io/ingress.class: "nginx"
```

8. Cek Ingress
```bash
$ kubectl get ingresses.networking.k8s.io -n kubeinvaders
```

9. Tambahkan di dalam /etc/hosts/ dengan IP Ingress
