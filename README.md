# Implementasi Monitoring KubeDoom dalam Kubernetes Cluster

## Prerequisite

1. Kubernetes Cluster telah di setting
2. VNC Client sudah di install

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
4. 

### Let's Play The Game!!
