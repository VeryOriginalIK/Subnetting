# Subnetting
IPv4 cím beállítása router interfészeken:
interface GigabitEthernet 0/0
ip address 195.220.123.1 255.255.255.0
no shutdown
IP cím beállítása switch VLAN interfészén:
interface vlan 1
ip address 10.0.0.1 255.0.0.0
no shutdown
Alapértelmezett átjáró megadása switch-en:
ip default-gateway 10.0.0.254

Alapbeállítások routeren, switchen:
Állomásnév beállítása:
hostname eszkoz_neve
Védett mód jelszavának beállítása:
enable secret cisco (titkos jelszó)
enable password cisco (titkosítatlan jelszó)
Konzol bejelentkezés jelszavának megadása:
line con 0
password cisco
login
Telnet bejelentkezés jelszavának megadása:
line vty 0
password cisco
login
Bejelentkezés felhasználónévvel jelszóval:
username admin secret adminjelszo
line vty 0
login local
Jelszótitkosítás bekapcsolása:
service password-encryption
Belépési (banner) üzenet beállítása:
banner motd #Belepes csak engedellyel!#
Interfész leírás megadása Gig, Fa, VLAN interfészeken:
description szoveges leiras
Konfiguráció mentése:
copy run start
w
Konfiguráció mentése TFTP szerverre:
copy run tftp
Konfiguráció megtekintése:
show running-config
Interfészek állapotának megtekintése:
show ip interface brief

SSH konfigurálása:

1. egyedi állomásnév beállítása:
Router(config)#hostname R1-router
2. IP tartománynév beállítása:
R1-router(config)#ip domain name jedlik.eu
3. titkosító kulcs létrehozása:
R1-router(config)#crypto key generate rsa
…  How many bits in the modulus [512]: 1024
4. helyi felhasználó létrehozása:
R1-router(config)#username admin secret Abc123456
5. belépés engedélyezése helyi adatbázis alapján
R1-router(config)#line vty 0
R1-router(config-line)#login local
6. SSH kapcsolódás engedélyezése: 
R1-router(config-line)#transport input ssh
7. SSH 2-es verziójának beállítása: 
R1-router(config)#ip ssh version 2 

statikus forgalomirányítás (IPv4):
ip route 0.0.0.0 0.0.0.0 se0/0/0 
(alapértelmezett statikus útvonal kimenő interfésszel)
ip route 0.0.0.0 0.0.0.0 192.168.1.1 
(alapértelmezett statikus útvonal következő ugrás IP-címmel)
