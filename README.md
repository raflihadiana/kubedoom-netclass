# Implementasi Monitoring KubeDoom dalam Cluster

## Brief Introduction

<img src="https://github.com/raflihadiana/net-class/blob/main/picture/doom.jpg" width="350" height="200" /> 

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
```
2. Apply monitoring deployment
```bash
kubectl apply -f k8s/ -n monitoring
```
3. Tunggu dan cek pod sudah ready dan siap digunakan
```bash
kubectl get pods -o wide -n monitoring
```
4. Lakukan port-forward untuk aplikasi monitoring

  Prometheus:
```bash
kubectl port-forward -n monitoring prometheus-deployment-75cff7d89f-w422q 8080:9090
```
  - Akses aplikasi prometheus pada browser dengan URL `localhost:8080`

  Grafana:
```bash
kubectl port-forward -n monitoring grafana-5469c64c7d-ddz4r 3000
```
  - Akses aplikasi grafana pada browser dengan URL `localhost:3000` 
  - Akses aplikasi grafana dengan user: `admin` & pass: `admin`

5. Konfigurasi Data Source dengan IP dari Pod Prometheus
```console
http://<Prometheus Pod IP>:9090
```
6. Buat Panel Dashboard Baru

Konfigurasi Panel JSON ada pada folder `./grafana/nginx-panel.json`. Lalu Save and apply.

### Let's Play The Game!!

Mainkan Game dan Lihat Metrik Pod yang Berjalan di Grafana. Itu artinya aktivitas ini sudah termonitor dengan baik!!
