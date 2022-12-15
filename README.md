# Learn How to Monitor Kubedoom on Grafana

## Prerequisite

1. Tambahkan helm repository Helm kubeinvaders
```bash
$ helm repo add kubeinvaders https://lucky-sideburn.github.io/helm-charts/
```

2. Buat namespace kubeinvaders
```bash
$ kubectl create namespace kubeinvaders
```

## Installation

### KubeDoom Deployment
1. Apply manifest untuk melakukan deployment Game KubeDoom
```bash
kubectl apply -k manifest/
```
2. Jalankan VNC Viewer agar bisa menjalankan game pada port 5901
```bash
$ vncviewer viewer localhost:5901
```
3. Gunakan cheat berikut agar karakter ada pada "GOD MODE"
```bash
$ vncviewer viewer localhost:5901
```bash
idspispopd | idkfa | iddqd
```

### Prometheus & Grafana Deployment
1. Buat Namespace monitoring 
```bash
kubectl create ns monitoring
kubectl create ns 
```
2. Apply monitoring deployment
```bash
kubectl apply -f k8s/ -n monitoring
```
3. Tunggu dan cek pod sudah ready dan siap digunakan
```bash
kubectl get pods -o wide -n monitoring
```

