***Test your enumeration skills on this boot-to-root machine.***
<img width="1200" height="1200" alt="image" src="https://github.com/user-attachments/assets/32f7172a-5026-4a42-8f3f-9b5f1d960d43" />

*Initial Enumeration*
<img width="1036" height="87" alt="image" src="https://github.com/user-attachments/assets/2f416d64-28f8-4fb2-bbfb-d999b9aa7293" />

*Nmap Scan*
```bash
nmap -T4 -n -sC -sV -Pn -p- 10.49.147.115
```

<img width="672" height="331" alt="image" src="https://github.com/user-attachments/assets/043244f4-de49-4783-81cf-179f0e21f168" />

```bash
$ nmap -T4 -n -sC -sV -Pn -p- 10.49.147.115
Starting Nmap 7.94SVN ( https://nmap.org ) at 2026-02-11 21:31 WITA
Nmap scan report for 10.49.147.115
Host is up (0.090s latency).
Not shown: 65533 closed tcp ports (conn-refused)
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 8.2p1 Ubuntu 4ubuntu0.13 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey:
|   3072 4d:4a:30:5a:2b:05:4b:2b:4e:a7:57:1f:08:b0:6e:b8 (RSA)
|   256 7c:b2:f0:d8:51:ed:39:d5:be:ef:65:4e:aa:8c:f5:73 (ECDSA)
|_  256 06:b9:3a:07:c1:20:76:3a:66:78:43:45:02:d9:fd:66 (ED25519)
80/tcp open  http    Apache httpd 2.4.41 ((Ubuntu))
|_http-title: Publisher's Pulse: SPIP Insights & Tips
|_http-server-header: Apache/2.4.41 (Ubuntu)
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 218.55 seconds
```
*There are two ports open.*

    22/SSH
    80/HTTP
    
*Port 80*
<img width="1365" height="684" alt="image" src="https://github.com/user-attachments/assets/df8f87da-0a23-4fcf-a3cc-bd4078247cb9" />

/spip (Status: 301) — Ini adalah target utama kita.

*Discovering SPIP CMS*

http://10.49.147.115/spip/

<img width="1364" height="679" alt="image" src="https://github.com/user-attachments/assets/8638a683-6464-4f57-bdba-ae9b5d12a163" />



Cek Versi SPIP: Buka http://10.49.147.115/spip/ dan lihat kode sumbernya (Ctrl + U). Pastikan ada tulisan SPIP 4.2.0.

<img width="752" height="603" alt="image" src="https://github.com/user-attachments/assets/f806b386-bb6a-4dbb-a43c-b4e7c428d53a" />

Siapkan RCE (Remote Code Execution): Karena versi 4.2.0 rentan (CVE-2023-27372), kamu bisa masuk ke server tanpa password menggunakan exploit Python.

```
https://github.com/nuts7/CVE-2023-27372
```

Dapatkan Shell:

    Buka terminal baru, jalankan listener: nc -lvnp 443.

    Jalankan exploit Python yang mengarah ke IP target.

<img width="393" height="219" alt="image" src="https://github.com/user-attachments/assets/8b0c3f69-81b7-4879-8cc5-777d64ea3ced" />

    
<img width="668" height="493" alt="image" src="https://github.com/user-attachments/assets/d8a38c1c-a4f6-494a-b41a-2c4b3682e7df" />



