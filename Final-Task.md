# Final-Task

## A. Cloud Computing

Pada Final Task kali ini, dimulai dengan cloud computing, dimana server yang kita buat, kita lakukan konfigurasi untuk mematikan Password Autenthication, dan meng-copy ```id_rsa.pub``` local kita ke file ```authorized_key``` yang ada pada Server, disini kita menggunakan *ansible-playbook*.

<img src="Dokumentasi/Dokumentasi-CC/1.png">

## B. SSH

Selanjutnya, kita generate *SSH* baru pada local kita, kemudian, *SSH* inilah yang nantinya akan kita gunakan untuk semua keperluan kita seperti push repo github, CI/CD, dll.

<img src="Dokumentasi/Dokumentasi-SSH/1.png">

Kemudian, kita akan membuat konfigurasi *SSH*, ini dilakukan agar memudahkan kita dalam mengakses server-server yang kita punya, nantinya server dapat kita akses tanpa harus mengetik alamat IP, melainkan menggunakan alias.

<img src="Dokumentasi/Dokumentasi-SSH/2.png">

<img src="Dokumentasi/Dokumentasi-SSH/3.png">

<img src="Dokumentasi/Dokumentasi-SSH/4.png">

<img src="Dokumentasi/Dokumentasi-SSH/5.png">

Berikutnya, kita copy *directory SSH* yang sudah kita generate di awal tadi.

<img src="Dokumentasi/Dokumentasi-SSH/6.png">

<img src="Dokumentasi/Dokumentasi-SSH/7.png">

<img src="Dokumentasi/Dokumentasi-SSH/8.png">

```bash
scp -r /lokasi/.ssh/kita username@IP:/lokasi/copy/diserver
```

## C. Repository

Pada tahap ini, kita diminta untuk membuat *Repository*, 3 *branch (development,staging,production)*.

1. Konfigurasikan server terlebih dahulu.

<img src="Dokumentasi/Dokumentasi-Repository/1.png">

2. Copy isi ```id_rsa.pub``` untuk membuat *SSH Keys* di github, agar kita bisa mengakses menggunakan *SSH*.

<img src="Dokumentasi/Dokumentasi-Repository/2.png">

<img src="Dokumentasi/Dokumentasi-Repository/3.png">

3. Clone aplikasi yang akan kita push ke *Repository* kita dan juga hapus file ```.git``` kemudian kita ganti dengan yang baru.

<img src="Dokumentasi/Dokumentasi-Repository/4.png">

<img src="Dokumentasi/Dokumentasi-Repository/5.png">

4. Buat *Repository* pada github kita, lalu tambahkan remote pada aplikasi yang kita clone tadi untuk melakukan push. 

<img src="Dokumentasi/Dokumentasi-Repository/6.png">

<img src="Dokumentasi/Dokumentasi-Repository/7.png">

<img src="Dokumentasi/Dokumentasi-Repository/8.png">

<img src="Dokumentasi/Dokumentasi-Repository/12.png">

<img src="Dokumentasi/Dokumentasi-Repository/13.png">

<img src="Dokumentasi/Dokumentasi-Repository/14.png">

<img src="Dokumentasi/Dokumentasi-Repository/15.png">

<img src="Dokumentasi/Dokumentasi-Repository/16.png">

5. Buat branch baru dan push ke branch tersebut.

<img src="Dokumentasi/Dokumentasi-Repository/9.png">

<img src="Dokumentasi/Dokumentasi-Repository/10.png">

<img src="Dokumentasi/Dokumentasi-Repository/11.png">

<img src="Dokumentasi/Dokumentasi-Repository/17.png">

<img src="Dokumentasi/Dokumentasi-Repository/18.png">

<img src="Dokumentasi/Dokumentasi-Repository/19.png">

## D. Deployment

Pada tahap ini, kita akan melakukan beberapa persiapan untuk deployment menggunakan CI/CD.

1. Install Dokcer menggunakan *ansible-playbook*.

<img src="Dokumentasi/Dokumentasi-Deployment/1.png">

2. Buat 2 directory untuk nantinya kita melakukan CI/CD pada 2 branch.

<img src="Dokumentasi/Dokumentasi-Deployment/2.png">

<img src="Dokumentasi/Dokumentasi-Deployment/3.png">

3. Lakukan perubahan pada beberapa konfigurasi aplikasi. Baik *Frontend* maupun *Backend*.

<img src="Dokumentasi/Dokumentasi-Deployment/4.png">

<img src="Dokumentasi/Dokumentasi-Deployment/13.png">

<img src="Dokumentasi/Dokumentasi-Deployment/6.png">

4. Buat Dockerfile, di perlukan untuk membuild image yang nantinya akan di jalankan pada container.

<img src="Dokumentasi/Dokumentasi-Deployment/5.png">

<img src="Dokumentasi/Dokumentasi-Deployment/7.png">

<img src="Dokumentasi/Dokumentasi-Deployment/14.png">

<img src="Dokumentasi/Dokumentasi-Deployment/17.png">

5. Buat file ```docker-compose.yml``` .

<img src="Dokumentasi/Dokumentasi-Deployment/8.png">

<img src="Dokumentasi/Dokumentasi-Deployment/9.png">

<img src="Dokumentasi/Dokumentasi-Deployment/18.png">

<img src="Dokumentasi/Dokumentasi-Deployment/19.png">

6. Install database menggunakan *ansible-playbook*.

<img src="Dokumentasi/Dokumentasi-Deployment/10.png">

<img src="Dokumentasi/Dokumentasi-Deployment/11.png">

## E. CI/CD dengan Jenkins

Setelah kita melakukan persiapan deployment, tibalah sekarang untuk melakukan deploy aplikasi menggunakan CI/CD.

1. Install Jenkins menggunakna *ansible-playbook*.

<img src="Dokumentasi/Dokumentasi-CICD/1.png">

2. Buka logs container Jenkins untuk melihat *Administrator Password* yang digunakan untuk installasi Jenkins.

<img src="Dokumentasi/Dokumentasi-CICD/2.png">

<img src="Dokumentasi/Dokumentasi-CICD/3.png">

3. Kita di arahkan untuk memilih install plugin Jenkins, disini kita bisa memilih Customize atau Recommended. Untuk saat ini kita pilih Customize.

<img src="Dokumentasi/Dokumentasi-CICD/4.png">

Kita install plugin SSH Agent, karena kita akan menggunakan SSH untuk Pipeline Script.

<img src="Dokumentasi/Dokumentasi-CICD/5.png">

4. Buat User dari Jenkins dan kita bisa tekan tombol next saja pada step berikutnya.

<img src="Dokumentasi/Dokumentasi-CICD/6.png">

<img src="Dokumentasi/Dokumentasi-CICD/7.png">

<img src="Dokumentasi/Dokumentasi-CICD/8.png">
Ket : Tampilan Jenkins

5. Buat Credential, Pilih Manage Jenkins->Manage Credentials.

<img src="Dokumentasi/Dokumentasi-CICD/9.png">

<img src="Dokumentasi/Dokumentasi-CICD/10.png">

<img src="Dokumentasi/Dokumentasi-CICD/11.png">

6. Setelan untuk Credential, Bagian Kind kita pilih *SSH Username with private key*. Kemudian copy id_rsa dari server aplikasi kita.

<img src="Dokumentasi/Dokumentasi-CICD/12.png">

<img src="Dokumentasi/Dokumentasi-CICD/13.png">

<img src="Dokumentasi/Dokumentasi-CICD/14.png">

<img src="Dokumentasi/Dokumentasi-CICD/15.png">

7. Tambahkan Webhook pada Repository Github kita. Ini dilakukan agar nantinya ketika kita melakukan push, build CI/CD akan berjalan otomatis.

<img src="Dokumentasi/Dokumentasi-CICD/16.png">

<img src="Dokumentasi/Dokumentasi-CICD/17.png">

<img src="Dokumentasi/Dokumentasi-CICD/18.png">

8. Buat Job baru, dan lakukan konfigurasi, seperti memasukkan SSH Repository Github, branch, dll.

<img src="Dokumentasi/Dokumentasi-CICD/19.png">

<img src="Dokumentasi/Dokumentasi-CICD/20.png">

<img src="Dokumentasi/Dokumentasi-CICD/21.png">

9. Install Plugin untuk Discord Notifier.

<img src="Dokumentasi/Dokumentasi-CICD/22.png">

10. Melakukan Setup Discord Notifier, buat sebuah server discord. Masuk ke Setting->Integrations->Create Webhooks, lalu Copy Webhook URL.

<img src="Dokumentasi/Dokumentasi-CICD/23.png">

<img src="Dokumentasi/Dokumentasi-CICD/24.png">

<img src="Dokumentasi/Dokumentasi-CICD/25.png">

11. Masuk ke job yang sudah kita buat, kemudian kita edit untuk melakukan generate link job notif dari Jenkins. Configure Job Scroll ke paling bawah, klik Pipeline Syntax

<img src="Dokumentasi/Dokumentasi-CICD/26.png">

<img src="Dokumentasi/Dokumentasi-CICD/27.png">

Link yang sudah di Generate kita masukkan ke Jenkinsfile Pipeline Script yang kita buat.

12. Buat Jenskinsfile Pipeline Script. Lakukan pada Frontend dan Backend.

<img src="Dokumentasi/Dokumentasi-CICD/28.png">

13. Lalu kita push aplikasi ke Repository kita dan juga branchnya. Karena kita sudah memasang Webhook pada Repository, maka Build akan berjalan dengan otomatis.

<img src="Dokumentasi/Dokumentasi-CICD/29.png">

<img src="Dokumentasi/Dokumentasi-CICD/30.png">

<img src="Dokumentasi/Dokumentasi-CICD/31.png">

<img src="Dokumentasi/Dokumentasi-CICD/32.png">

<img src="Dokumentasi/Dokumentasi-CICD/33.png">

## F. Monitoring

Selanjutnya Monitoring. Ada 3 hal yang kita perlukan untuk Memonitoring Server, yaitu Node Exporter, Prometheus, dan Grafana.

1. Install Node Exporter pada server yang akan kita monitor menggunakan *ansible-playbook*.

<img src="Dokumentasi/Dokumentasi-Monitoring/1.png">

2. Install juga Prometheus dan Grafana pada server monitoring menggunakan *ansible-playbook*.

<img src="Dokumentasi/Dokumentasi-Monitoring/2.png">

3. Check apakah Prometheus sudah menangkap metrics dari server yang kita install Node Exporter.

<img src="Dokumentasi/Dokumentasi-Monitoring/3.png">

<img src="Dokumentasi/Dokumentasi-Monitoring/4.png">

4. Akses Grafana menggunakan Domain yang kita buat.

<img src="Dokumentasi/Dokumentasi-Monitoring/5.png">

<img src="Dokumentasi/Dokumentasi-Monitoring/6.png">

5. Buat data source untuk pembuatan dashboard.

<img src="Dokumentasi/Dokumentasi-Monitoring/7.png">

<img src="Dokumentasi/Dokumentasi-Monitoring/8.png">

6. Kita perlu Template dashboard dari dokumentasi website [Grafana](https://grafana.com/grafana/dashboards/?src=ggl-s&mdm=cpc&camp=nb-hashicorp-vault-bmm&cnt=130557757818&trm=vault%20grafana%20dashboard&device=c&gclid=Cj0KCQiA45qdBhD-ARIsAOHbVdHvRoPbbZkTIkMkZAnc1xjIF4NltDeSeSIppjNHcYLomfT2Vg-yV_oaAqPGEALw_wcB).

<img src="Dokumentasi/Dokumentasi-Monitoring/9.png">

<img src="Dokumentasi/Dokumentasi-Monitoring/10.png">

<img src="Dokumentasi/Dokumentasi-Monitoring/11.png">

<img src="Dokumentasi/Dokumentasi-Monitoring/12.png">

<img src="Dokumentasi/Dokumentasi-Monitoring/13.png">

<img src="Dokumentasi/Dokumentasi-Monitoring/14.png">

## G. Webserver

Setelah semuanya sudah berjalan, selanjutnya kita akan membuat Reverse Proxy untuk semua aplikasi tadi.

1. Buat Domain dan pasang IP Gateway.

<img src="Dokumentasi/Dokumentasi-Webserver/1.png">

2. Install Nginx menggunakan *ansible-playbook*.

<img src="Dokumentasi/Dokumentasi-Webserver/2.png">

3. Copy file konfigurasi Reverse Proxy menggunakan *ansible-playbook*.

<img src="Dokumentasi/Dokumentasi-Webserver/3.png">

4. Install Certbot untuk mendapatkan SSL Certificate. Step lengkapnya ada pada Website [Certbot](https://certbot.eff.org/instructions?ws=nginx&os=ubuntufocal).

<img src="Dokumentasi/Dokumentasi-Webserver/4.png">

<img src="Dokumentasi/Dokumentasi-Webserver/5.png">

<img src="Dokumentasi/Dokumentasi-Webserver/6.png">

5. Setup Credentials sesuai dengan plugin. Disini kita menggunakan Cloudflare.

<img src="Dokumentasi/Dokumentasi-Webserver/7.png">

<img src="Dokumentasi/Dokumentasi-Webserver/8.png">

<img src="Dokumentasi/Dokumentasi-Webserver/9.png">

6. Request Certificate.

<img src="Dokumentasi/Dokumentasi-Webserver/10.png">

<img src="Dokumentasi/Dokumentasi-Webserver/11.png">

<img src="Dokumentasi/Dokumentasi-Webserver/12.png">

<img src="Dokumentasi/Dokumentasi-Webserver/13.png">

<img src="Dokumentasi/Dokumentasi-Webserver/14.png">

<img src="Dokumentasi/Dokumentasi-Webserver/15.png">

Sekian dokumentasi saya pada Final Task Bootcamp Dumbways, Kurang lebihnya saya mohon maaf.

Terima Kasih.