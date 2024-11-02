[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/1zoHyFGp)
| Name           | NRP        | Kelas     |
| ---            | ---        | ----------|
| Junathan Richie | 5025231019 | Jaringan Komputer ( C ) |
| Bradley Widjaja | 5025231036 | Jaringan Komputer ( C ) |

## Put your topology config image here!

![image](https://github.com/user-attachments/assets/a25caa4e-c572-4113-9089-ea06c7b324db)


<br>

> Template testing report: https://docs.google.com/document/d/17T0fsnh_4zZTrG-lELDJ88intrc9mkwCzZ_s-23JLCc/edit?usp=sharing

## Put your testing report here! 
> The report is sent in PDF format, uploaded to Drive, and set to public view.

`https://drive.google.com/file/d/1fa6ltbakKSI4FtCkF_41SpzX6E5zQl9o/view?usp=sharing`

## Soal 0

> Pada perlombaan akhir tahun kali ini, semua worker dan client ikut serta di dalamnya sebagai perwakilan dari masing-masing asrama. Persiapan yang dilakukan untuk perlombaan ini adalah dengan setup semua network configuration yang sesuai dengan tabel peran diatas. Khusus untuk client menggunakan konfigurasi dari DHCP Server.

> _For the end-of-year competition, all the workers and clients participate, representing their respective houses. The preparation includes setting up the network configuration as per the table above, with clients using DHCP Server configuration_

**Answer**

- Dumbledore:

  ```
  auto eth0
  iface eth0 inet dhcp
  
  auto eth1
  iface eth1 inet static
  	address 10.154.1.1
  	netmask 255.255.255.0
  
  auto eth2
  iface eth2 inet static
  	address 10.154.2.1
  	netmask 255.255.255.0
  
  auto eth3
  iface eth3 inet static
  	address 10.154.3.1
  	netmask 255.255.255.0
  
  auto eth4
  iface eth4 inet static
  	address 10.154.4.1
  	netmask 255.255.255.0
  
  auto eth5
  iface eth5 inet static
  	address 10.154.5.1
  	netmask 255.255.255.0
  
  auto eth6
  iface eth6 inet static
  	address 10.154.6.1
  	netmask 255.255.255.0
  
  up iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE -s 10.154.0.0/16
  ```

- SeverusSnape:

  ```
  auto eth0
  iface eth0 inet static
  	address 10.154.3.2
  	netmask 255.255.255.0
  	gateway 10.154.3.1
  ```

- McGonagall:

  ```
  auto eth0
  iface eth0 inet static
  	address 10.154.3.3
  	netmask 255.255.255.0
  	gateway 10.154.3.1
  ```

- Hagrid:

  ```
  auto eth0
  iface eth0 inet static
  	address 10.154.4.2
  	netmask 255.255.255.0
  	gateway 10.154.4.1
  ```

- Voldemort:

  ```
  auto eth0
  iface eth0 inet static
  	address 10.154.4.3
  	netmask 255.255.255.0
  	gateway 10.154.4.1
  ```

- Dementor:

  ```
  auto eth0
  iface eth0 inet static
  	address 10.154.4.4
  	netmask 255.255.255.0
  	gateway 10.154.4.1
  ```

- HarryPotter:

  ```
  auto eth0
  iface eth0 inet static
  	address 10.154.1.2
  	netmask 255.255.255.0
  	gateway 10.154.1.1

  ```

- RonWeasley:

  ```
  auto eth0
  iface eth0 inet static
  	address 10.154.1.3
  	netmask 255.255.255.0
  	gateway 10.154.1.1
  ```

- HermioneGranger:

  ```
  auto eth0
  iface eth0 inet static
  	address 10.154.1.4
  	netmask 255.255.255.0
  	gateway 10.154.1.1

  ```

- LunaLovegood:

  ```
  auto eth0
  iface eth0 inet static
  	address 10.154.6.4
  	netmask 255.255.255.0
  	gateway 10.154.6.1
  ```

- FiliusFlitwick:

  ```
  auto eth0
  iface eth0 inet static
  	address 10.154.6.3
  	netmask 255.255.255.0
  	gateway 10.154.6.1
  ```

- ChoChang:

  ```
  auto eth0
  iface eth0 inet static
  	address 10.154.6.2
  	netmask 255.255.255.0
  	gateway 10.154.6.1
  ```

- DracoMalfoy:

  ```
  auto eth0
  iface eth0 inet dhcp
  ```

- AstoriaGreengrass:

  ```
  auto eth0
  iface eth0 inet dhcp
  ```

- SusanBones:

  ```
  auto eth0
  iface eth0 inet dhcp
  ```

- HannahAbbott:

  ```
  auto eth0
  iface eth0 inet dhcp
  ```

## Soal 1

> Melakukan registrasi subdomain untuk PHP worker bernama gryffindor.hogwarts.yyy.com yang mengarah ke alamat IP load balancer Voldemort dan untuk laravel worker bernama ravenclaw.hogwarts.yyy.com yang mengarah ke alamat IP load balancer Dementor. Seluruh domain ini berkumpul dalam suatu ruang atau folder bernama hogwarts

> _Registering subdomains for the PHP workers named gryffindor.hogwarts.yyy.com, pointing to the IP Voldemort load balancer, and for the Laravel workers named ravenclaw.hogwarts.yyy.com, pointing to the IP Dementor load balancer. All domains are gathered in a folder named "hogwarts."_

**Answer:**

- Screenshot <br>
  ![image](https://github.com/user-attachments/assets/1907f398-4b8c-457a-8641-82947e664dd1)


- Configuration

  ```
  apt-get update && apt-get install bind9

  #!/bin/bash
  
  mkdir -p /etc/bind/hogwarts
  
  cp /etc/bind/db.local /etc/bind/hogwarts/hogwarts.C30.com
  cp /etc/bind/db.local /etc/bind/hogwarts/3.154.10.in-addr.arpa
  cat <<EOL > /etc/bind/named.conf.local
  zone "hogwarts.C30.com" {
          type master;
          file "/etc/bind/hogwarts/hogwarts.C30.com";
  };
  EOL
  
  cat <<EOL > /etc/bind/hogwarts/hogwarts.C30.com
  ;
  ; BIND data file for local loopback interface
  ;
  \$TTL    604800
  @       IN      SOA     hogwarts.C30.com. root.hogwarts.C30.com. (
                  2024110101    ; Serial
                  604800        ; Refresh
                  86400         ; Retry
                  2419200       ; Expire
                  604800 )      ; Negative Cache TTL
  @               IN      NS     hogwarts.C30.com.
  @               IN      A      10.154.3.3
  www             IN      CNAME  hogwarts.C30.com.
  gryffindor      IN      A      10.154.4.3
  ravenclaw       IN      A      10.154.4.4
  EOL

  cat <<EOL > /etc/bind/hogwarts/3.154.10.in-addr.arpa
  \$TTL    604800
  @       IN      SOA     hogwarts.C30.com. root.hogwarts.C30.com. (
                  2024110101    ; Serial
                  604800        ; Refresh
                  86400         ; Retry
                  2419200       ; Expire
                  604800 )      ; Negative Cache TTL
  3.154.10.in-addr.arpa.         IN      NS      hogwarts.C30.com.
  3                               IN      PTR     hogwarts.C30.com.
  EOL
  
  cat <<EOL > /etc/bind/named.conf.options
  options {
          directory "/var/cache/bind";
          forwarders {
                  192.168.122.1;
          };
          //dnssec-validation auto;
          allow-query{any;};
          auth-nxdomain no;
          listen-on-v6 { any; };
  };
  EOL
  ```

- Explanation <br>
  Setup konfigurasi bind9 untuk mendaftarkan subdomain gryffindor dan ravenclaw yang mengarah ke loadbalancer
 

<br>

## Soal 2

> Memberikan ketentuan khusus untuk DracoMalfoy dan AstoriaGreengrass yang mendapat range IP dari [Prefix IP].2.64 - [Prefix IP].2.65 dan [Prefix IP].2.100 - [Prefix IP].2.101

> Selain itu, untuk HannahAbbott dan SusanBones mendapat range IP dari [Prefix IP].5.50 - [Prefix IP].5.51 dan [Prefix IP].5.155 - [Prefix IP].5.156.


> _Special provisions are given to DracoMalfoy and AstoriaGreengrass, who are assigned the IP range from [Prefix IP].2.64 - [Prefix IP].2.65 and [Prefix IP].2.100 - [Prefix IP].2.101._

> _Additionally, HannahAbbott and SusanBones are assigned the IP range from [Prefix IP].5.50 - [Prefix IP].5.51 and [Prefix IP].5.155 - [Prefix IP].5.156._

**Answer:**

- Screenshot
  <br>HannahAbbott <br>
  ![image](https://github.com/user-attachments/assets/4e9b31ee-5406-44a7-9f02-ed81f6f15a23)
  <br>SusanBones <br>
  ![image](https://github.com/user-attachments/assets/c3afb33b-515f-4bd9-8ba2-e1a7e095bb08)
  <br>AstoriaGreengrass <br>
  ![image](https://github.com/user-attachments/assets/df96135e-b5d7-4b78-a986-ba60e7b0b24d)
  <br>DracoMalfoy <br>
  ![image](https://github.com/user-attachments/assets/8ac7b119-5c74-449e-889c-bcd2eb27ca06)


- Configuration <br>
  di SeverusSnape (DHCP Server)
  ```
  apt-get update
  apt-get install -y isc-dhcp-server
  echo INTERFACESv4="eth0" > /etc/default/isc-dhcp-server
  cat <<EOL > /etc/dhcp/dhcpd.conf
  subnet 10.154.2.0 netmask 255.255.255.0 {
      range 10.154.2.64 10.154.2.65;
      range 10.154.2.100 10.154.2.101;
      option broadcast-address 10.154.2.255;
      option routers 10.154.2.1;
      option domain-name-servers 10.154.3.3;
  }
  
  subnet 10.154.5.0 netmask 255.255.255.0 {
      range 10.154.5.50 10.154.5.51;
      range 10.154.5.155 10.154.5.156;
      option broadcast-address 10.154.5.255;
      option routers 10.154.5.1;
      option domain-name-servers 10.154.3.3;
  }
  subnet 10.154.3.0 netmask 255.255.255.0 {
      range 10.154.3.10 10.154.3.20;
      option broadcast-address 10.154.3.255;
      option routers 10.154.3.1;
      option domain-name-servers 10.154.3.3;
  }
  EOL
  ```
  di dumbledore
  ```
  cat <<EOL > /etc/default/isc-dhcp-relay
  SERVERS="10.154.3.2"
  INTERFACES="eth1 eth2 eth3 eth4 eth5 eth6"
  OPTIONS=
  EOL
  echo net.ipv4.ip_forward=1 > /etc/sysctl.conf
  ```
- Explanation <br>
  Atur konfigurasi di DHCP server ke subnet yang terhubung dengan client ditambah ethernet yang terhubung dengan DHCP server tersendiri (10.154.3.0)


<br>

## Soal 3

> Khusus untuk HermioneGranger yang berada di switch 1 mendapat range IP dari
[Prefix IP].1.10 - [Prefix IP].1.15 dan [Prefix IP].1.20 - [Prefix IP].1.25

> Khusus untuk ChoChang yang berada di switch 6 mendapat range IP dari 
[Prefix IP].6.10 - [Prefix IP].6.15 dan [Prefix IP].6.20 - [Prefix IP].6.25


> _HermioneGranger, who is on switch 1, is assigned the IP range from [Prefix IP].1.10 - [Prefix IP].1.15 and [Prefix IP].1.20 - [Prefix IP].1.25._

> _ChoChang, who is on switch 6, is assigned the IP range from [Prefix IP].6.10 - [Prefix IP].6.15 and [Prefix IP].6.20 - [Prefix IP].6.25._

**Answer:**

- Screenshot
  <br>
  HermioneGranger
  <br>
  ![image](https://github.com/user-attachments/assets/3023f7ec-b8b5-410c-819a-376d60768b25)
  <br>
  ChoChang
  <br>
  ![image](https://github.com/user-attachments/assets/9cb2ea37-3701-4401-9596-6e68443464ba)
  <br>
  
- Configuration
  <br> Di SeverusSnape (DHCP Server) 
  ```
  cat <<EOL > /etc/dhcp/dhcpd.conf
  subnet 10.154.2.0 netmask 255.255.255.0 {
      range 10.154.2.64 10.154.2.65;
      range 10.154.2.100 10.154.2.101;
      option broadcast-address 10.154.2.255;
      option routers 10.154.2.1;
      option domain-name-servers 10.154.3.3;
  }
  
  subnet 10.154.5.0 netmask 255.255.255.0 {
      range 10.154.5.50 10.154.5.51;
      range 10.154.5.155 10.154.5.156;
      option broadcast-address 10.154.5.255;
      option routers 10.154.5.1;
      option domain-name-servers 10.154.3.3;
  }
  subnet 10.154.3.0 netmask 255.255.255.0 {
      option broadcast-address 10.154.3.255;
      option routers 10.154.3.1;
      option domain-name-servers 10.154.3.3;
  }
  subnet 10.154.1.0 netmask 255.255.255.0 {
          range 10.154.1.10 10.154.1.15;
          range 10.154.1.20 10.154.1.25;
          option routers 10.154.1.1;
          option broadcast-address 10.154.1.255;
          option domain-name-servers 10.154.3.3;
  }
  subnet 10.154.6.0 netmask 255.255.255.0 {
          range 10.154.6.10 10.154.6.15;
          range 10.154.6.20 10.154.6.25;
          option broadcast-address 10.154.6.255;
          option routers 10.154.6.1;
          option domain-name-servers 10.154.3.3;
  }
  EOL
  ```
  Ubah network configuration di HermioneGranger dan ChoChang menjadi
  ```
  auto eth0
  iface eth0 inet dhcp
  ```
- Explanation <br>
  Tambahkan subnet 10.154.1.0 untuk HermioneGranger dan subnet 10.154.6.0 untuk ChoChang pada dhcpd.conf. Setelah itu, ubah konfigurasi pada Hermione dan ChoChang agar IP nya mengikuti DHCP

<br>

## Soal 4

> Menetapkan batasan waktu untuk DHCP server dalam peminjaman alamat IP untuk client melalui switch 2 selama 5 menit sedangkan client yang melalui switch 5 selama 20 menit. Untuk switch 1 dan switch 6 memiliki batas waktu 10 menit. Alokasi waktu maksimal peminjaman alamat IP selama 100 menit. 

> _The DHCP server's lease time for IP addresses is set as follows: Clients connected through switch 2 have a lease time of 5 minutes, Clients connected through switch 5 have a lease time of 20 minutes, Switches 1 and 6 have a lease time of 10 minutes, The maximum lease time for IP addresses is set at 100 minutes._

**Answer:**

- Screenshot
  <br>
  HermioneGranger
  <br>
  ![image](https://github.com/user-attachments/assets/cb8c4a52-92d8-43fd-ba6e-9adb3502e896)
  <br>
  DracoMalfoy (Switch 2)
  <br>
  ![image](https://github.com/user-attachments/assets/61fae154-2da2-4fa8-8d0a-70403f921a86)
  <br>
  SusanBones (Switch 5)
  <br>
  ![image](https://github.com/user-attachments/assets/8a77213c-256f-43e4-820e-adc5994dc601)
  <br>
  ChoChang
  <br>
  ![image](https://github.com/user-attachments/assets/33c1b684-9f2d-4b60-832a-ef74faea6c0a)
  <br>

- Configuration

  ```
  cat <<EOL > /etc/dhcp/dhcpd.conf
  subnet 10.154.2.0 netmask 255.255.255.0 {
      range 10.154.2.64 10.154.2.65;
      range 10.154.2.100 10.154.2.101;
      option broadcast-address 10.154.2.255;
      option routers 10.154.2.1;
      option domain-name-servers 10.154.3.3;
      default-lease-time 300;
      max-lease-time 6000;
  
  }
  
  subnet 10.154.5.0 netmask 255.255.255.0 {
      range 10.154.5.50 10.154.5.51;
      range 10.154.5.155 10.154.5.156;
      option broadcast-address 10.154.5.255;
      option routers 10.154.5.1;
      option domain-name-servers 10.154.3.3;
      default-lease-time 1200;
      max-lease-time 6000;
  }
  subnet 10.154.3.0 netmask 255.255.255.0 {
      option broadcast-address 10.154.3.255;
      option routers 10.154.3.1;
      option domain-name-servers 10.154.3.3;
  }
  subnet 10.154.1.0 netmask 255.255.255.0 {
          range 10.154.1.10 10.154.1.15;
          range 10.154.1.20 10.154.1.25;
          option routers 10.154.1.1;
          option broadcast-address 10.154.1.255;
          option domain-name-servers 10.154.3.3;
          default-lease-time 600;
          max-lease-time 6000;
  }
  subnet 10.154.6.0 netmask 255.255.255.0 {
          range 10.154.6.10 10.154.6.15;
          range 10.154.6.20 10.154.6.25;
          option broadcast-address 10.154.6.255;
          option routers 10.154.6.1;
          option domain-name-servers 10.154.3.3;
          default-lease-time 600;
          max-lease-time 6000;
  }
  EOL
  service isc-dhcp-server restart
  ```

- Explanation <br>
  Tambahkan default-lease-time dan max-lease-time sesuai dengan yang ditentukan. Konfigurasi tersebut dibuat dalam satuan detik. 

<br>

## Soal 5

> Memastikan bahwa semua CLIENT, HermioneGranger, dan ChoChang harus menggunakan konfigurasi dari DHCP server, menerima DNS dari Professor McGonagall dan dapat akses internet. Khusus untuk HermioneGranger dan ChoChang mendapatkan IP Statis dari DHCP dengan [Prefix IP].x.14. hint: fixed address


> _Ensure that all CLIENT, HermioneGranger, and ChoChang use DHCP server configurations, receive DNS from Professor McGonagall, and can access the internet. HermioneGranger and ChoChang must receive static IPs from DHCP with the address [Prefix IP].x.14 (hint: fixed address)._

**Answer:**

- Screenshot
  <br>
  HermioneGranger
  <br>
  ![image](https://github.com/user-attachments/assets/d63e5463-cc6b-4d57-88f8-3930474795f3)
  <br>
  ChoChang
  <br>
  ![image](https://github.com/user-attachments/assets/d3fdf585-94cd-4b73-84a8-81168af8e978)

- Configuration

  ```
  cat <<EOL > /etc/dhcp/dhcpd.conf
	subnet 10.154.2.0 netmask 255.255.255.0 {
	    range 10.154.2.64 10.154.2.65;
	    range 10.154.2.100 10.154.2.101;
	    option broadcast-address 10.154.2.255;
	    option routers 10.154.2.1;
	    option domain-name-servers 10.154.3.3;
	    default-lease-time 300;
	    max-lease-time 6000;
	
	}
	
	subnet 10.154.5.0 netmask 255.255.255.0 {
	    range 10.154.5.50 10.154.5.51;
	    range 10.154.5.155 10.154.5.156;
	    option broadcast-address 10.154.5.255;
	    option routers 10.154.5.1;
	    option domain-name-servers 10.154.3.3;
	    default-lease-time 1200;
	    max-lease-time 6000;
	}
	subnet 10.154.3.0 netmask 255.255.255.0 {
	    option broadcast-address 10.154.3.255;
	    option routers 10.154.3.1;
	    option domain-name-servers 10.154.3.3;
	}
	subnet 10.154.1.0 netmask 255.255.255.0 {
	        range 10.154.1.10 10.154.1.15;
	        range 10.154.1.20 10.154.1.25;
	        option routers 10.154.1.1;
	        option broadcast-address 10.154.1.255;
	        option domain-name-servers 10.154.3.3;
	        default-lease-time 600;
	        max-lease-time 6000;
	}
	subnet 10.154.6.0 netmask 255.255.255.0 {
	        range 10.154.6.10 10.154.6.15;
	        range 10.154.6.20 10.154.6.25;
	        option broadcast-address 10.154.6.255;
	        option routers 10.154.6.1;
	        option domain-name-servers 10.154.3.3;
	        default-lease-time 600;
	        max-lease-time 6000;
	}
	host HermioneGranger {
	        hardware ethernet 02:fe:6a:6b:0d:7d;
	        fixed-address 10.154.1.14;
	}
	host ChoChang {
	        hardware ethernet 3a:0e:d8:38:e4:38;
	        fixed-address 10.154.6.14;
	}
	
	EOL
	service isc-dhcp-server restart
	echo nameserver 10.154.3.3 > /etc/resolv.conf
  ```

- Explanation
  <br>
	set agar host HermioneGranger dan ChoChang memiliki fixed-address dengan setting hardware ethernetnya

<br>

## Soal 6

> Dimulai dari asrama Gryffindor yang menjadi PHP worker, mereka harus melakukan deployment untuk website berikut menggunakan PHP 7.4.

> _The Gryffindor house, represented by the PHP workers, must deploy the following website using PHP 7.4._

**Answer:**

- Screenshot

 ![image](https://github.com/user-attachments/assets/e127ad71-8a0c-4648-b3ed-1eb5fbf092d0)
![image](https://github.com/user-attachments/assets/c302d0b1-6641-4ec7-b36c-c991bf69fee2)
![image](https://github.com/user-attachments/assets/79e89a9d-956e-43b2-8984-df4a4ebc30f4)
![image](https://github.com/user-attachments/assets/9f3af924-11a7-4965-b22d-e50afe524a03)
![image](https://github.com/user-attachments/assets/6ebc1889-e036-4814-8b17-cb46d75eae87)
![image](https://github.com/user-attachments/assets/bc7604ba-d376-4f88-8d00-d777369747a5)




- Configuration
  <br>
  ```sh
  wget -O php.zip "https://drive.google.com/uc?export=download&id=17R4Zcxm3emHq21WdMJzSfCxO8FHqvATM"
	apt-get update
	apt-get install php7.4 php7.4-fpm
	apt-get install nginx -y
	apt-get install zip
	unzip php.zip -d /var/www/html
	cat <<EOL > /etc/nginx/sites-available/default
	##
	# You should look at the following URL's in order to grasp a solid understanding
	# of Nginx configuration files in order to fully unleash the power of Nginx.
	# https://www.nginx.com/resources/wiki/start/
	# https://www.nginx.com/resources/wiki/start/topics/tutorials/config_pitfalls/
	# https://wiki.debian.org/Nginx/DirectoryStructure
	#
	# In most cases, administrators will remove this file from sites-enabled/ and
	# leave it as reference inside of sites-available where it will continue to be
	# updated by the nginx packaging team.
	#
	# This file will automatically load configuration files provided by other
	# applications, such as Drupal or Wordpress. These applications will be made
	# available underneath a path with that package name, such as /drupal8.
	#
	# Please see /usr/share/doc/nginx-doc/examples/ for more detailed examples.
	##
	
	# Default server configuration
	#
	server {
	        listen 80 default_server;
	        listen [::]:80 default_server;
	
	        # SSL configuration
	        #
	        # listen 443 ssl default_server;
	        # listen [::]:443 ssl default_server;
	        #
	        # Note: You should disable gzip for SSL traffic.
	        # See: https://bugs.debian.org/773332
	        #
	        # Read up on ssl_ciphers to ensure a secure configuration.
	        # See: https://bugs.debian.org/765782
	        #
	        # Self signed certs generated by the ssl-cert package
	        # Don't use them in a production server!
	        #
	        # include snippets/snakeoil.conf;
	
	        root /var/www/html;
	
	        # Add index.php to the list if you are using PHP
	        index index.html index.htm index.nginx-debian.html;
	
	        server_name _;
	
	        location / {
	                # First attempt to serve request as file, then
	                # as directory, then fall back to displaying a 404.
                  try_files \$uri \$uri/ /index.php?\$query_string;
  	        }
	
	        # pass PHP scripts to FastCGI server
	        #
	        location ~ \.php$ {
	                include snippets/fastcgi-php.conf;
	        #
	        #       # With php-fpm (or other unix sockets):
	        #       fastcgi_pass unix:/var/run/php/php7.4-fpm.sock;
	        #       # With php-cgi (or other tcp sockets):
	        #       fastcgi_pass 127.0.0.1:9000;
	        }
	
	        # deny access to .htaccess files, if Apache's document root
	        # concurs with nginx's one
	        #
	        #location ~ /\.ht {
	        #       deny all;
	        #}
	}
	
	
	# Virtual Host configuration for example.com
	#
	# You can move that to a different file under sites-available/ and symlink that
	# to sites-enabled/ to enable it.
	#
	#server {
	#       listen 80;
	#       listen [::]:80;
	#
	#       server_name example.com;
	#
	#       root /var/www/example.com;
	#       index index.html;
	#
	#       location / {
	#               try_files $uri $uri/ =404;
	#       }
	#}
	EOL
  ```

- Explanation

  download file dan taruh index.php di

	```
	/var/www/html untuk masing - masing member gryffindor
	move semua unzip ke directory tersebut
	
	nano /etc/nginx/sites-available/default di semua gryffindor
	index index.php index.html index.htm index.nginx-debian.html; dan uncomment beberapa hal:
	location ~ \.php$ {
		include snippets/fastcgi-php.conf;
	#
	#   # With php-fpm (or other unix sockets):
		fastcgi_pass unix:/var/run/php/php7.2-fpm.sock;
	#   # With php-cgi (or other tcp sockets):
	#   fastcgi_pass 127.0.0.1:9000;
	}
	service php7.4-fpm start
	service nginx start
	```

<br>

## Soal 7

> Khusus perlombaan ini, Voldemort sudah jinak dan dia menjadi load balancer untuk para penghuni asrama Gryffindor yang menjadi worker PHP. Aturlah agar Voldemort dapat membagi pekerjaan kepada worker PHP secara optimal. Sebagai pengetesan awal, terapkan algoritma round robin dan lakukan test index.php menggunakan apache benchmark dengan 1000 request dan 100 request/second. Lakukan test sebanyak 3 kali lalu hitung rata-rata dan standar deviasi dari time/request

> _Voldemort, who is now reformed, becomes the load balancer for the Gryffindor PHP workers. Optimize Voldemort to distribute tasks to the PHP workers. For the initial test, apply the round-robin algorithm and test it to the index.php page using Apache Benchmark with 1,000 requests and 100 requests/second. Do the test 3 times and calculate the mean and standard deviation of time/request._

**Answer:**

- Screenshot

![image](https://github.com/user-attachments/assets/aa2492ab-eec7-494b-b395-e64ab7ee4406)

  ![image](https://github.com/user-attachments/assets/4cb22118-6003-48e2-9d84-7619de576727)
  ![image](https://github.com/user-attachments/assets/6585ef10-21e2-4208-bf26-c850d5bcd73d)
  
![image](https://github.com/user-attachments/assets/1ad72c6d-63e2-41e5-b7e4-cf9a600241fd)
![image](https://github.com/user-attachments/assets/f75615e8-61e0-402b-9f8d-b246a814e052)
![image](https://github.com/user-attachments/assets/c186fa93-d044-464e-8855-3798dfbe40b2)
![image](https://github.com/user-attachments/assets/09ec4771-7804-435f-b19f-8a8c616c2d0d)
![image](https://github.com/user-attachments/assets/43f8e8cf-70f3-4710-98bd-eacc8ffb7e71)



- Configuration
  di Voldemort
  ```
  ./connectInet.sh
	apt-get update
	apt-get install nginx -y
	apt-get install htop -y
	cat <<EOL > /etc/nginx/sites-available/rr
	#Default menggunakan Round Robin di voldemort
	upstream backend  {
	server 10.154.1.2; #IP harry potter
	server 10.154.1.3; #IP ron
	server 10.154.1.14; #IP hermione
	}
	
	server {
	listen 80;
	server_name gryffindor.hogwarts.C30.com;
	
	        location / {
	                proxy_pass http://backend;
	                proxy_set_header        X-Real-IP \$remote_addr;
	                proxy_set_header        X-Forwarded-For \$proxy_add_x_forwarded_for;
	                proxy_set_header        Host \$http_host;
	        }
	
	error_log /var/log/nginx/lb_error.log;
	access_log /var/log/nginx/lb_access.log;
	
	}
	
	EOL
	unlink /etc/nginx/sites-enabled/default
	ln -s /etc/nginx/sites-available/rr /etc/nginx/sites-enabled/
	service nginx restart
	echo nameserver 10.154.3.3 > /etc/resolv.conf
  ```
  di salah satu client
  ```
  ./connectInet.sh
	apt-get update && apt-get install apache2-utils
	apt-get install apache2-utils
	./DNS.sh
	ab -n 1000 -c 100 http://gryffindor.hogwarts.C30.com/index.php
  ```
- Explanation <br>
	Atur konfigurasi pada load balancer ketiga worker. Setelah itu, uji dengan apache benchmark. 

<br>

## Soal 8

> Dalam penilaian akhir tahun ini, dibutuhkan algoritma terbaik, cobalah tes 3 algoritma load balancer dengan menggunakan jmeter. Jmeter perlu melakukan login, akses home, dan terakhir logout. Lakukan test dengan 300 thread dan 3 sec ramp up period. Lakukan test sebanyak 3 kali per algoritma, lalu hitung rata-rata dan standar deviasi dari response time. (username: wingardium, password: leviosa)


> _For the final assessment, try three different load-balancing algorithms using JMeter with 300 threads and a 3-second ramp-up period. Jmeter have to be able to login, access homepage, and logout. Do the test 3 times for each algorithm, then calculate the mean and standard deviation of response time. (username: wingardium, password: leviosa)_

**Answer:**

- Screenshot
  ![image](https://github.com/user-attachments/assets/058ff21e-180e-4d54-ab39-7cff6850be24)

  
- Configuration
  ![image](https://github.com/user-attachments/assets/a6fd8d13-7e43-4b40-89c3-105b270c93c6)
  ![image](https://github.com/user-attachments/assets/249ba851-f330-4fcb-9edc-856422db0e3a)
  ![image](https://github.com/user-attachments/assets/167b3a6a-a89b-41c8-a37d-9784872f255f)
  
- Explanation

  <br>
  Set Jmeter dengan 1 post ke login.php, 2 get ke home.php dan logout.php, ubah algoritma yang sesuai

<br>

## Soal 9

> Tidak semua IP dapat akses asrama Gryffindor melalui IP Load balancer Voldemort. Untuk itu, berikan akses pada load balancer Voldemort. Autentikasi akan memerlukan username: “jarkom” dan password: “modul3”. Simpan file autentikasi pada  /etc/nginx/secretchamber 

> _Not all IPs can access Gryffindor's house through Voldemort’s load balancer. Grant access to the Voldemort load balancer. Authentication will require username: “jarkom” and password: “modul3”. Save the authentication file in /etc/nginx/secretchamber._

**Answer:**

- Screenshot

  ![image](https://github.com/user-attachments/assets/b21456e5-cd03-42d7-a91e-82e6c6cd50f2)
  ![image](https://github.com/user-attachments/assets/b227d5af-f2ef-444e-8018-4ff4c7f82352)
  ![image](https://github.com/user-attachments/assets/eac5886c-b923-44c6-91b7-dc5e0f948de4)
![image](https://github.com/user-attachments/assets/4be38374-5443-426e-8a49-97272a386b42)
![image](https://github.com/user-attachments/assets/2b405477-2959-4b15-9a51-2e0de9ae3b81)
![image](https://github.com/user-attachments/assets/06673fe3-e97d-4087-9b75-4f0ee31b7a76)
![image](https://github.com/user-attachments/assets/6e74ee33-bf17-477a-80cd-a31a28a94b64)

- Configuration

  ```
	apt-get update && apt-get install apache2-utils
	htpasswd -c /etc/nginx/secretchamber jarkom
	password: modul3
	
	nano /etc/nginx/sites-available/rr
	upstream backend  {
	server 10.154.1.2; #IP harry potter
	server 10.154.1.3; #IP ron
	server 10.154.1.14; #IP hermione
	}
	
	server {
	listen 80;
	server_name gryffindor.hogwarts.C30.com;
	
	    	location / {
			auth_basic "Restricted Access";
	auth_basic_user_file /etc/nginx/secretchamber;
	            	proxy_pass http://backend/index.php;
	            	proxy_set_header	X-Real-IP $remote_addr;
	            	proxy_set_header	X-Forwarded-For $proxy_add_x_forwarded_for;
	            	proxy_set_header	Host $http_host;
	    	}
	
	error_log /var/log/nginx/lb_error.log;
	access_log /var/log/nginx/lb_access.log;
	
	}

  ```

- Explanation

  Menambahkan htpasswd untuk melakukan autentikasi kepada user dan pada ```/etc/nginx/sites-available/rr``` menambahkan ```auth_basic "Restricted Access";``` dan
	```auth_basic_user_file /etc/nginx/secretchamber;```

<br>

## Soal 10

> Setelah menambahkan autentikasi ke Gryffindor, coba testing ulang dengan menggunakan JMeter (algoritma round robin) serta skenario, thread, dan ramp up period yang sama seperti no 8 (300 thread, 3 sec ramp up period, login-home-logout). Kali ini, coba juga jumlah worker yang berbeda: 3 worker, 2 worker, dan 1 worker. 

> _After adding authentication to Gryffindor, retest using JMeter (round-robin algorithm) with the same scenario, thread, and ramp up period as number 8 (300 thread, 3 sec ramp up period, login-home-logout). This time, test with different numbers of workers: 3 workers, 2 workers, and 1 worker._

**Answer:**

- Screenshot
  ![image](https://github.com/user-attachments/assets/2645230e-1b7a-4dbb-a5df-c080bf39cf03)
  ![image](https://github.com/user-attachments/assets/b2bc33e5-b38f-4632-9c6f-dadb3cdcf0a6)
  ![image](https://github.com/user-attachments/assets/07d8c35d-b017-4a02-9ce1-32a8a8179af7)

- Configuration

  ![image](https://github.com/user-attachments/assets/16e163d2-fa44-4c6b-961e-69bf5064f318)


- Explanation <br>
  Pada jmeter ditambah bagian authorization HTTP manager untuk mengolah authorization. Jumlah worker yang dinyalakan sesuai dengan yang ingin diuji

<br>

## Soal 11

> Hogwarts juga bekerjasama dengan ITS dalam perlombaan ini. Untuk itu, setiap request pada Voldemort yang mengandung /informatika pada akhir url akan di proxy passing menuju halaman https://www.its.ac.id/informatika/id/beranda/ 

> _Hogwarts has also partnered with ITS for this competition. Any request to Voldemort containing /informatika at the end of the URL should be proxied to the page at https://www.its.ac.id/informatika/id/beranda/._


**Answer:**

- Screenshot
  ![image](https://github.com/user-attachments/assets/5a4137a0-bdd3-4dd2-b6e2-ec8931a2347e)
  
- Configuration

  ```
  echo 'upstream backend  {
	server 10.154.1.2; #IP harry potter
	server 10.154.1.3; #IP ron
	server 10.154.1.14; #IP hermione
	}
	
	server {
	listen 80;
	server_name gryffindor.hogwarts.C30.com;
	
	        location / {
	                auth_basic "Restricted Access";
	auth_basic_user_file /etc/nginx/secretchamber;
	                proxy_pass http://backend/index.php;
	                proxy_set_header        X-Real-IP $remote_addr;
	                proxy_set_header        X-Forwarded-For $proxy_add_x_forwarded_for;
	                proxy_set_header        Host $http_host;
	        }
	
	        location  /informatika {
	        proxy_pass https://www.its.ac.id/informatika/id/beranda/; 
	}
	
	
	
	error_log /var/log/nginx/lb_error.log;
	access_log /var/log/nginx/lb_access.log;
	
	}
	' > /etc/nginx/sites-available/rr
	
	service nginx restart
	service php7.4-fpm restart
  ```

- Explanation <br>
  Tambah folder location /informatika yang mengarahkan ke website informatika

<br>

## Soal 12

> Selain butuh autentikasi dalam pengaksesan asrama Gryffindor melalui LB Voldemort, juga perlu dibatasi dengan pembatasan IP.  LB Voldemort hanya boleh diakses oleh client dengan IP [Prefix IP].2.64, [Prefix IP].2.100, [Prefix IP].5.50, dan [Prefix IP].5.155. hint: (fixed in dulu clientnya) 


> _In addition to requiring authentication for access to Gryffindor through Voldemort’s load balancer, IP restrictions also need to be enforced. Voldemort's load balancer can only be accessed by clients with IPs: [Prefix IP].2.64, [Prefix IP].2.100, [Prefix IP].5.50, and [Prefix IP].5.155. (hint: fixed client IPs first)._

**Answer:**

- Screenshot
  ![image](https://github.com/user-attachments/assets/d8dfdcc2-9560-41a4-ab3f-906e96f21ea9)

- Configuration
  ```
  echo 'upstream backend  {
	server 10.154.1.2; #IP harry potter
	server 10.154.1.3; #IP ron
	server 10.154.1.14; #IP hermione
	}
	
	server {
	listen 80;
	server_name gryffindor.hogwarts.C30.com;
	allow 10.154.2.64;
	allow 10.154.2.100;
	allow 10.154.5.50;
	allow 10.154.5.155;
	deny all;
	
	        location / {
	                auth_basic "Restricted Access";
	auth_basic_user_file /etc/nginx/secretchamber;
	                proxy_pass http://backend/index.php;
	                proxy_set_header        X-Real-IP $remote_addr;
	                proxy_set_header        X-Forwarded-For $proxy_add_x_forwarded_for;
	                proxy_set_header        Host $http_host;
	        }
	
	        location  /informatika {
	        proxy_pass https://www.its.ac.id/informatika/id/beranda/; 
	}
	
	
	
	error_log /var/log/nginx/lb_error.log;
	access_log /var/log/nginx/lb_access.log;
	
	}
	' > /etc/nginx/sites-available/rr
	
	service nginx restart
	service php7.4-fpm restart
  ```

- Explanation
  <br>
	Tambahkan allow pada ip user yang diperbolehkan dan deny all ip lain

<br>

## Soal 13

> Pengaturan database yang dibutuhkan dalam perlombaan ini wajib diatur di Hagrid. Pastikan pengaturan database tersebut dapat diakses oleh Lunalovegood, FiliusFlitwick, dan ChoChang dengan menggunakan username: kelompokyyy dan password: passwordyyy 

> _Database setup for this competition is managed by Hagrid. Ensure that this database can be accessed by LunaLovegood, FiliusFlitwick, and ChoChang using the username: "kelompokyyy" and password: "passwordyyy”_

**Answer:**

- Screenshot
  <br>
  ![image](https://github.com/user-attachments/assets/03f3edd9-ba39-46cc-887d-bfa722fd4a87)


- Configuration

  ```
  apt-get update && apt-get install mariadb-server -y

	service mysql start
	mysql
	
	CREATE USER 'kelompokC30'@'%' IDENTIFIED BY 'passwordC30';
	CREATE USER 'kelompokC30'@'localhost' IDENTIFIED BY 'passwordC30';
	CREATE DATABASE dbkelompokC30;
	GRANT ALL PRIVILEGES ON *.* TO 'kelompokC30'@'%';
	GRANT ALL PRIVILEGES ON *.* TO 'kelompokC30'@'localhost';
	FLUSH PRIVILEGES;
	
	nano /etc/mysql/my.cnf
	
	[mysqld]
	skip-networking=0
	skip-bind-address
	
	service mysql restart
	
	di lunalovegood
	apt-get install mariadb-client -y

	mariadb --host=10.154.4.2 --port=3306 --user=kelompokC30 --password
  ```

- Explanation <br>
	Persiapkan server mariaDB lalu jalankan. Buat user dan database sesuai yang diminta

<br>

## Soal 14

> Selain itu, untuk Lunalovegood, FiliusFlitwick, dan ChoChang memiliki website sesuai dengan https://github.com/lodaogos/laravel-jarkom-modul-3/tree/main  berikut. Jangan lupa melakukan instalasi PHP8.0 dan Composer! Pastikan database di Hagrid sudah ada isinya sekarang dan server Laravel sudah running di localhost!

> _Additionally, LunaLovegood, FiliusFlitwick, and ChoChang have websites following this GitHub link: Laravel Jarkom Modul 3. Install PHP 8.0 and Composer! Make sure Hagrid's data storage is populated, and the Laravel servers are running on localhost!_

**Answer:**

- Screenshot

  ![image](https://github.com/user-attachments/assets/943b8ab9-af99-4108-a979-b7523c4fcd0b)
	![image](https://github.com/user-attachments/assets/a8ff96a6-fbfa-4fdc-9fc6-7005d5271f8e)
	<br>

- Configuration

  ```
  apt-get update
	apt-get install software-properties-common
	add-apt-repository ppa:ondrej/php
	
	apt-get update
	
	apt-get install php8.0-mbstring php8.0-xml php8.0-cli php8.0-common php8.0-intl php8.0-opcache php8.0-readline php8.0-mysql php8.0-fpm php8.0-curl unzip wget -y
	
	apt-get install nginx -y
	
	wget https://getcomposer.org/download/2.0.13/composer.phar
	chmod +x composer.phar
	mv composer.phar /usr/bin/composer
	
	apt-get install git -y
	
	git clone https://github.com/lodaogos/laravel-jarkom-modul-3.git
  
	composer update
	composer install
	
	cp .env.example .env
	
	nano env
	
	edit bagian
	DB_CONNECTION=mysql
	DB_HOST=10.154.4.2
	DB_PORT=3306
	DB_DATABASE=dbkelompokC30
	DB_USERNAME=kelompokC30
	DB_PASSWORD=passwordC30
	
	php artisan migrate:fresh
	php artisan db:seed --class=MusicsTableSeeder
  	php artisan key:generate
	php artisan jwt:secret
  cat <<EOL > /etc/nginx/sites-available/implementasi
	server {
	
	    listen 8001;
	
	    root /var/www/laravel-jarkom-modul-3/public;
	
	    index index.php index.html index.htm;
	    server_name _;
	
	    location / {
	            try_files \$uri \$uri/ /index.php?\$query_string;
	    }
	
	    # pass PHP scripts to FastCGI server
	    location ~ \.php$ {
	    include snippets/fastcgi-php.conf;
	    fastcgi_pass unix:/var/run/php/php8.0-fpm.sock;
	    }
	
	location ~ /\.ht {
	            deny all;
	    }
	
	    error_log /var/log/nginx/implementasi_error.log;
	    access_log /var/log/nginx/implementasi_access.log;
	}
	EOL
	ln -s /etc/nginx/sites-available/implementasi /etc/nginx/sites-enabled/
	chown -R www-data.www-data /var/www/laravel-jarkom-modul-3/storage
	service php8.0-fpm start
	service nginx restart
  ```

- Explanation

  `Put your explanation in here`

<br>

## Soal 15

> Lakukan testing endpoint /register sebanyak 100 request dengan 10 request/second di salah satu worker menggunakan apache benchmark dari SusanBones! Kenapa failed 99x? Jelaskan! 

> _Test the /register endpoint with 100 requests and 10 requests per second on one of the workers using Apache Benchmark from SusanBones! Why did 99 tests fail? Explain!_

**Answer:**

- Screenshot <br>
  ![image](https://github.com/user-attachments/assets/79f0a87d-f85c-407d-855d-1368a891df61)


- Configuration
  soal15.json
  ```
  {
    "username": "username",
    "password": "password"
	}
  ```
  soal15.sh
  ```ab -n 100 -c 10 -p ~/soal15.json -T application/json http://10.154.6.4:8001/api/auth/register```

- Explanation <br>
	Request hanya 1 yang berhasil karena register harus berupa username yang unik. Pada kasus di atas, hanya request pertama saja yang berhasil (tidak ada duplikasi nama)

<br>

## Soal 16

> Lakukan juga testing pada endpoint /login sebanyak 100 request dengan 10 request/second di salah satu worker menggunakan apache benchmark dari SusanBones! Dapatkan token melalui responsenya juga!

> _Test the /login endpoint with 100 requests and 10 requests per second on one of the workers using Apache Benchmark from SusanBones! Collect the token from the response!_

**Answer:**

- Screenshot
  ![image](https://github.com/user-attachments/assets/6cdea94f-e653-4303-a9e6-3639d9eb18c0)

- Configuration <br>
	soal16.json
	```
 	{
    "username": "username",
    "password": "password"
	}
 	```
 	soal16.sh
  ```
  ab -n 100 -c 10 -p ~/soal16.json -T application/json http://10.154.6.4:8001/api/auth/login
  ```

- Explanation <br>
	login dikirimkan dengan mengirimkan username dan password yang telah di-register sebelumnya.

<br>

## Soal 17

> Coba testing pada endpont /me sebanyak 100 request dengan 10 request/second di salah satu worker menggunakan apache benchmark dari SusanBones! Periksa responsenya apakah sudah sesuai dengan yang diloginkan? 

> _Test the /me endpoint with 100 requests and 10 requests per second on one of the workers using Apache Benchmark from SusanBones! Check if the response matches the logged-in user!_

**Answer:**

- Screenshot
  
  ![image](https://github.com/user-attachments/assets/706ae362-fb91-487d-8d38-6a9fd4b1877c)
  ![image](https://github.com/user-attachments/assets/f11e01be-6519-4b8d-9b23-634a23cf5828)


- Configuration
  soal17.sh
  ```
  # Mendapatkan token
	TOKEN=$(curl -s -X POST -H "Content-Type: application/json" -d '{"username":"username","password":"password"}' http://10.154.6.4:8001/api/auth/login | grep -o '"token":"[^"]*' | sed 's/"token":"//')
	# Menampilkan token
	echo "Token: $TOKEN"
	# Melakukan pengujian menggunakan Apache Benchmark
	ab -n 100 -c 10 -H "Authorization: Bearer $TOKEN" http://10.154.6.4:8001/api/me
  ```

- Explanation <br>
	Request ke endpoint /me didapatkan dengan menggunakan token yang didapat setelah login. Token ini dikirimkan pada bagian authorization.

<br>

## Soal 18

> Mendekati tugas akhir perlombaan ini, mari seimbangkan kekuatan LunaLovegood, FiliusFlitwick, dan ChoChang untuk bekerja sama secara adil! Buatkan load balancer Laravel dengan Dementor dan implementasikan Proxy Bind untuk mengaitkan IP dari ketiga worker tersebut!

> _As the competition nears its end, balance the workload of LunaLovegood, FiliusFlitwick, and ChoChang! Create a Laravel load balancer using Dementor and implement Proxy Bind to link the IPs of the three workers!_

**Answer:**

- Screenshot
  ![image](https://github.com/user-attachments/assets/d4366fec-6d4c-4ce4-8334-5526832005e5)

- Configuration
	di dementor:
  ```
	apt-get update && apt-get install nginx
	
	touch /etc/nginx/sites-available/laravel_lb
	
	nano /etc/nginx/sites-available/laravel_lb
	
	upstream laravel {
	    	server 10.154.6.4:8001;
	    	server 10.154.6.3:8002;
	    	server 10.154.6.14:8003;
	}
	
	server {
	    	listen 80;
	    	server_name ravenclaw.hogwarts.C30.com;
	
	    	location / {
	 				proxy_pass http://laravel;
					proxy_set_header Host $host;
					proxy_set_header X-Real-IP $remote_addr; 
					proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for; proxy_set_header X-Forwarded-Proto $scheme;
	    	}
          location /app1/{
                proxy_bind 10.154.6.4
                proxy_pass http://10.154.6.4
        }
        location /app2/{
                proxy_bind 10.154.6.3
                proxy_pass http://10.154.6.3
        }
        location /app3/{
                proxy_bind 10.154.6.14
                proxy_pass http://10.154.6.14
        }

				  error_log /var/log/nginx/lb_error.log;
				  access_log /var/log/nginx/lb_access.log;
	}
	
	unlink /etc/nginx/sites-enabled/default
	
	ln -s /etc/nginx/sites-available/laravel_lb /etc/nginx/sites-enabled/
	
	service nginx restart
  ```
	di client
	```
 	echo nameserver 10.154.3.3 > /etc/resolv.conf
	curl http://ravenclaw.hogwarts.C30.com
  ```
 	atau testing dengan cara seperti no 16 tetapi ke load balancer untuk melihat hasil htop
- Explanation <br>
  Di dementor setup nginx agar menerapkan proxy bind dan lakukan load balancer agar membagi beban ke tiga worker

<br>

## Soal 19

> Untuk menguatkan para Laravel Worker, coba implementasikan PHP-FPM pada LunaLovegood, FiliusFlitwick, dan ChoChang. Untuk testing kinerja naikkan: 
pm.max_children
pm.start_servers
pm.min_spare_servers
pm.max_spare_servers
sebanyak tiga percobaan dan lakukan analisis testing menggunakan apache benchmark sebanyak 100 request dengan 10 request/second atau menggunakan jmeter dengan 100 threads! (Pilih 1 metode testing)

> _To strengthen the Laravel workers, implement PHP-FPM on LunaLovegood, FiliusFlitwick, and ChoChang. For performance testing, adjust: pm.max_children, pm.start_servers, pm.min_spare_servers, pm.max_spare_servers. Run the tests three times and analyze the performance by using Apache Benchmark with 100 requests at a rate of 10 requests per second or using JMeter with 100 threads! (Choose 1 testing method)_

**Answer:**

- Screenshot

  `Put your screenshot in here`

- Configuration
  ```
  cat <<EOL > /etc/php/8.0/fpm/pool.d/laravel.conf
	[laravel_site]
	user = laravel_user
	group = laravel_user
	listen = /var/run/php8.0-fpm-laravel-site.sock
	listen.owner = www-data
	listen.group = www-data
	php_admin_value[disable_functions] = exec,passthru,shell_exec,system
	php_admin_flag[allow_url_fopen] = off
	
	; Choose how the process manager will control the number of child processes.
	
	pm = dynamic
	pm.max_children = 5
	pm.start_servers = 2
	pm.min_spare_servers = 1
	pm.max_spare_servers = 3
	pm.process_idle_timeout = 10s
	
	;contoh diatas konfigurasi untuk mengatur jumalh proses PHP-FPM yang berjalan
	EOL
	
	groupadd laravel_user
	useradd -g laravel_user laravel_user
	
	service php8.0-fpm restart
  ```

- Explanation

  `Put your explanation in here`

<br>

## Soal 20

> Yey terakhir. Menurut Professor Dumbledore, sepertinya menggunakan PHP-FPM tidak cukup untuk meningkatkan performa worker-worker. Implementasikan Least-Conn pada Dementor. Lakukan analisis pada testing kinerja menggunakan apache benchmark sebanyak 100 request dengan 10 request/second atau menggunakan jmeter dengan 100 threads! (Pilih 1 metode testing)

> _Finally, Professor Dumbledore suggests that PHP-FPM might not be enough to improve the workers' performance. Implement the Least-Conn algorithm on Dementor. Analyze the performance by using Apache Benchmark with 100 requests at a rate of 10 requests per second or using JMeter with 100 threads! (Choose 1 testing method)_

**Answer:**

- Screenshot

  `Put your screenshot in here`

- Configuration

  `Put your configuration in here`

- Explanation

  `Put your explanation in here`

<br>
  
## Problems

## Revisions (if any)
