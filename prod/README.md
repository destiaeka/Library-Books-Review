# 🚀 Book Review Web — Production Deployment Guide
## 🐳 Dockerfile — Struktur & Penjelasan

---
![topology](image/topology.jpg)
---

Berikut adalah contoh struktur `Dockerfile` yang digunakan untuk membangun image aplikasi:

```dockerfile
# Gunakan image dasar Node.js untuk tahap build
FROM node:18-alpine AS builder

# Tentukan working directory di dalam container
WORKDIR /app

# Salin package.json dan install dependensi
COPY package*.json ./
RUN npm install

# Salin seluruh source code dan build project
COPY . .
RUN npm run build

# Tahap kedua untuk image yang ringan (Nginx)
FROM nginx:alpine

# Salin hasil build dari tahap sebelumnya ke direktori Nginx
COPY --from=builder /app/dist /usr/share/nginx/html

# Expose port default Nginx
EXPOSE 80

# Jalankan Nginx
CMD ["nginx", "-g", "daemon off;"]
```

## 🏗️ Build & Push Docker Image
1. Build Image Secara Lokal
```
docker build -t destiaeka/booksreview:latest .
```
2. Jalankan Container
```
docker run -d --name booksreview -p 80:80 destiaeka/booksreview:latest
```
3. Push ke Docker Hub
```
docker push destiaeka/booksreview:latest
```

## ☸️ Kubernetes Manifest

Untuk deployment di cluster K3s, digunakan dua file utama:
- Deployment → Menjalankan Pod dengan image container
- Service → Mengekspos aplikasi agar bisa diakses dari luar cluster
Untuk expose saya menggunakan ingress

Untuk menjalankan file manifest masukkan perintah berikut:
```
kubectl apply -f deployment.yml
kubectl apply -f service.yml
kubectl apply -f ingress.yml
```
```
[ides@103-160-37-103 ~]$ kubectl get all
NAME                                          READY   STATUS    RESTARTS   AGE
pod/booksreview-deployment-7d7b5b6f64-6b69j   1/1     Running   0          26s
pod/booksreview-deployment-7d7b5b6f64-fxrkg   1/1     Running   0          27s
pod/booksreview-deployment-7d7b5b6f64-p5m84   1/1     Running   0          26s

NAME                          TYPE        CLUSTER-IP     EXTERNAL-IP   PORT(S)   AGE
service/booksreview-service   ClusterIP   10.43.60.68    <none>        80/TCP    27s
service/kubernetes            ClusterIP   10.43.0.1      <none>        443/TCP   21h

NAME                                     READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/booksreview-deployment   3/3     3            3           28s
```
```
[ides@103-160-37-103 ~]$ kubectl get ingress
NAME                  CLASS     HOSTS                     ADDRESS          PORTS   AGE
booksreview-ingress   traefik   ingress.destiaeka.local   103.160.37.103   80      43s
```

## ⚙️ CI/CD Workflow (GitHub Actions + Lovable Cloud)
Proyek ini terintegrasi dengan GitHub Actions untuk mengotomatisasi proses:
- Build image Docker
- Push ke Docker Hub
- Deploy otomatis ke cluster Kubernetes