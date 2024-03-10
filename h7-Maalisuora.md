# H7 - Maalisuora
Tämän viikon
## B) Uusi komento klo 12.00
Luon uuden tekstitiedoston komennolla `nano moikkamoi.sh`. Lisään tiedostoon `#!/bin/bash` ja `echo "Moikka moi"`.
Komennolla `chmod a+x moivaan.sh` annan kaikille käyttäjille oikeuden

![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/23fffa89-2368-4fcd-bb74-567126a4be78)

![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/72326c0d-0e6d-4711-8708-f373302933d3)

## D) Virtuaalikoneen asentaminen

Klo 10.25
Aloitan lataamalla Debianin uusimman version koneelleni. Avaan Virtualboxin ja lähden luomaan uutta virtuaalikonetta, jolle annan nimen DebianJanPen.
Annan koneelle RAM-muistia 5000 MB ja kovalevylle 60 GB. Painan "create" ja siirryn Virtualboxissa virtuaalikoneen asetuksiin. Lisäsin lataamani Debian live -levykuvan virtuaaliseen levyasemaan. Käynnistän virtuaalikoneen, ja valitsen boottausvalikossa Live system (amd64).

![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/e0459675-d8e9-4e7c-8ed4-e786e676b72e)


Tarkistan verkkoselaimessa, että verkkoyhteys, näppäimistö jne toimii. Valitsen työpöydältä "Install Debian", ja lähden asentamaan käyttöjärjestelmää. Valitsen kieleksi Amerikan englannin, sijainniksi Suomen sekä suomalaisen näppäimistön. Valitsen myös täpän Erase disk. Luon käyttäjän ja sille vahvan salasanan. Käynnistän asennuksen, ja asennuksen päätyttyä käynnistän koneen uudelleen. Klo 11.00

![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/9d9856f0-2381-4748-b378-88fdc624f2c1)

### Alkutoimet // klo 11.50-11.55
Avaan terminaalin ja haen päivitykset komennolla `sudo apt-get update`. Päivitän kaiken komennolla `sudo apt-get -y dist-upgrade`. Asennan tulimuurin ja laitan sen päälle 
    sudo apt-get -y install ufw
$ sudo ufw enable

### Oma käyttöympäristö
Oman koneen speksit:

- Acer Nitro N50-620 työasema
- Windows 11 käyttöjärjestelmä
- Intel Core i5-prosessori
- NVIDIA GeForce RTX 3060 Ti-näytönohjain
- 16 Gt RAM-muistia
- 1 TB tallennustilaa

VM speksit:

- Debian 12 Bookworm 64-bit
- Base memory 4000 MB
- Storage 60 GB

### Lähdeluettelo 

Karvinen, T. H7 - Maalisuora. Tero Karvisen verkkosivut. Luettavissa: https://terokarvinen.com/2024/linux-palvelimet-2024-alkukevat/ 
Luettu 10.03.2024.
Karvinen, T. 22.01.2021. Install Debian on Virtualbox. Luettavissa: https://terokarvinen.com/2021/install-debian-on-virtualbox/ 
Luettu: 10.03.2024.
