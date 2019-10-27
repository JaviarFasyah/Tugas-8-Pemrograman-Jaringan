# Tugas-8-Pemrograman-Jaringan
### Javiar Fasyah         1301164477  
### Hilmi Triandi N		    1301164286  
### Fahrur Rozi Syarbini	1301164213  
  
  
Untuk bisa membuat container docker pada aplikasi dengan bahasa Go, aplikasi perlu dibuat dalam lingkungan module, tidak di dalam lingkungan GOPATH. Caranya adalah dengan membuat sebuah direktori baru pada direktori HOME, berpindah ke direktori baru tersebut, dan ketik “go mod init <nama aplikasi>” lalu enter. Perintah tersebut menghasilkan sebuah file go.mod, jangan lupa untuk download kembali package pihak ketiga yang dibutuhkan (go get <link package>). Setelah selesai download, akan terdapat file go.sum yang mencantumkan package-package pihak ketiga yang digunakan aplikasi.  
Setelah itu, jangan lupa membuat Docker file sebelum membuat image pada docker, aplikasi akan di-build didalam image tersebut. Buat image dengan perintah “docker build –t <nama image> .” dan semua tahapan-tahapan yang ada di Dockerfile akan dilaksanakan (termasuk membuild aplikasinya). Setelah selesai, container bisa menggunakan image tersebut dengan perintah “docker run --net=host –it <nama image>.” Parameter “--net=host” digunakan agar aplikasi bisa berkomunikasi dengan database yang masih berada di host, nomor port tidak perlu dispesifikasikan jika menggunakan parameter tersebut. Parameter “-it” berarti ia berjalan tidak di background, bisa diganti dengan “-d” jika ingin bekerja di background. Container pun beroperasi dengan baik.
![docker_0.png](/screenshot/8_docker_0.png)  
![docker_1.png](/screenshot/8_docker_1.png)  
Hasil running:  
![docker_2.png](/screenshot/8_docker_2.png)  
  
Pada kubernetes, container bisa dibuat secara local dengan menggunakan minikube yang memanfaatkan virtual machine yang telah terinstall pada host. Setelah minikube sudah terinstall pada virtual machine dan berjalan, maka pembuatan image lokal bisa dilakukan dengan memasuki lingkungan virtual machine minikube “$eval(minikube docker-env).” Setalah itu kita bisa membuat image dengan “docker build –t <nama aplikasi> .” dan menunggu proses selesai.  
  Sebelum membuat deployment dan service, tag  terlebih dahulu image dengan “docker tag <id repository> <nama aplikasi>:<versi>” untuk menghindari error pulling image. Barulah kita mendeploy dengan “kubectl create deployment <nama deployment> --image=<nama image aplikasi>:<versi>.” Untuk bisa mengaksesnya, kita perlu mengeksposnya dengan “kubectl  expose deployment <nama deployment> --type=NodePort --port=<port>,” dan selanjutnya “kubectl get pod.” Dari sini bisa diketahui alamat untuk mengakses deployment dengan “minikube <nama deployment> --url,” namun sayang terjadi error yang tidak diketahui saat ingin membuka alamat aksesnya.
