## Laporan Hasil Pratikum 2 - Sistem Administrasi Server 

Nadila Chusnul K - 1202190020 \
Anastasya Rahma Juniarti - 120219058\
Kelompok 10 

Langkah pertama yang akan dilakukan pastikan pengaturan adapter “bridge”. Masuk ansible modul 2

```bash
   cd ~/ansible/modul2-ansible
 ```
 ![A1](aset/G1.jpg)

 Tambahkan “bind9” dan “dnsutils” di roles/php/tasks/main.yml
```bash
   nano roles/php/tasks/main.yml
 ```
![A1](aset/G2.jpg)
![A1](aset/G3.jpg)

Tambahkan perintah di roles/lv/tasks/main.yml

```bash
   nano roles/lv/tasks/main.yml
 ```
 ![A1](aset/G4.jpg)
 ![A1](aset/G5.jpg)
 ![A1](aset/G6.jpg)

Tambahkan restart bind di roles/lv/handlers/main.yml

```bash
   nano  roles/lv/handlers/main.yml
 ```
![A1](aset/G7.jpg)

kemudian run ansible 

```bash
  ansible-playbook -i install-laravel.yml -k 
 ```
![A1](aset/G8.jpg)

Cek apakah sudah benar tercopy file “named.conf.local”, “vm.local”, “1.168.192.in-addr.arpa”, “named.conf.options”, dan “resolv.conf” pada direktory roles/lv/templates

```bash
 nano roles/lv/templates/names.conf.local 
 ```

![A1](aset/G9.jpg)

```bash
 nano roles/lv/templates/vm.local 
 ```

![A1](aset/G10.jpg)

```bash
 nano roles/lv/templates/1.168.192.in-addr.arpa
 ```

![A1](aset/G11.jpg)

```bash
 nano roles/lv/templates/named.conf.options
 ```
![A1](aset/G12.jpg)

```bash
 nano roles/lv/templates/resolv.conf
 ```
![A1](aset/G13.jpg)

Tambahkan “dev.vm.local” pada /etc/hosts

```bash
 nano /etc/hosts
 ```
![A1](aset/G14.jpg)

Masuk pada ubuntu landing 

```bash
 lxc-attach ubuntu_landing
 ```
![A1](aset/G15.jpg)

enter nano vm.local, then add 'www IN CNAME vm.local.'

```bash
 nano /var www IN CNAME vm.local 
 ```
 
![A1](aset/G16.jpg)

Restart lalu exit lxc

![A1](aset/G17.jpg)

Run ansible playbook 

```bash
ansible-playbook -i hosts install-laravel.yml -k
```
![A1](aset/G18.jpg)
![A1](aset/G19.jpg)

Test di browser
```bash
dev.vm.local
```
![A1](aset/G19.jpg)