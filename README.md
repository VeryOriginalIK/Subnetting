# Subnetting
IPv4 cím beállítása router interfészeken:
1. interface GigabitEthernet 0/0
2. ip address 195.220.123.1 255.255.255.0
3. no shutdown
IP cím beállítása switch VLAN interfészén:
1. interface vlan 1
2. ip address 10.0.0.1 255.0.0.0
3. no shutdown
Alapértelmezett átjáró megadása switch-en:
1. ip default-gateway 10.0.0.254

Alapbeállítások routeren, switchen:

Állomásnév beállítása:
1. hostname eszkoz_neve
Védett mód jelszavának beállítása:
1. enable secret cisco (titkos jelszó)
2. enable password cisco (titkosítatlan jelszó)
Konzol bejelentkezés jelszavának megadása:
1. line con 0
2. password cisco
3. login
Telnet bejelentkezés jelszavának megadása:
1. line vty 0
2. password cisco
3. login
Bejelentkezés felhasználónévvel jelszóval:
1. username admin secret adminjelszo
2. line vty 0
3. login local
Jelszótitkosítás bekapcsolása:
1. service password-encryption
Belépési (banner) üzenet beállítása:
1. banner motd #Belepes csak engedellyel!#
2. Interfész leírás megadása Gig, Fa, VLAN interfészeken:
3. description szoveges leiras
Konfiguráció mentése:
1. copy run start
2. w
Konfiguráció mentése TFTP szerverre:
1. copy run tftp
Konfiguráció megtekintése:
1. show running-config
Interfészek állapotának megtekintése:
1. show ip interface brief

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
