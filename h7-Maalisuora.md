# H7 - Maalisuora
Tämän viikon kotitehtävässä loin uuden bash-komennon, suoritin vanhan laboratorioharjoituksen (Karvinen, T. 2019) ja asensin valmiiksi tyhjän virtuaalikoneen ensi viikon laboratorioharjoitusta varten.

## A) "Hei maailma" Pythonilla // klo 17.57-
Päätin tehdä tämän Pythonilla. Luon kansion komennolla mkdir heimaailma
Siirryn kansioon ja luon tekstitiedoston komennolla 
        $ nano helloworld.py

![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/e66abe51-18cd-4b90-bda6-c9b355636684)

Tarkistan toimiiko
cat helloworld.py
python3 helloworld.py
![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/ed209b82-6a3b-483c-8c4b-5b475e4aa79c)


## B) Uusi komento // klo 12.00-12.10
Luon uuden tekstitiedoston komennolla `nano moikkamoi.sh`. Lisään tiedostoon `#!/bin/bash` ja `echo "Moikka moi"`.
Komennolla `chmod a+x moivaan.sh` annan kaikille käyttäjille oikeuden komennon käyttämiseen

![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/23fffa89-2368-4fcd-bb74-567126a4be78)

![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/72326c0d-0e6d-4711-8708-f373302933d3)

## C) Laboratorioharjoitus // klo 17.10-17.53

Loin tehtävää varten uuden Linux Debian -virtuaalikoneen, johon tein päivitykset ja asensin tulimuurin & kytkin sen päälle. Asennan koneelle Apache-weppipalvelimen komennolla sudo apt-get -y install apache2. Luon Maijalle käyttäjän komennolla sudo adduser maija. Kirjaudun sisään käyttäjälle maija ja luon uuden kansion mkdir public_html. Tässä vaiheessa päätän kuitenkin kirjautua takaisin omalle käyttäjälleni ja luoda maijan sivut pääkäyttäjän oikeuksin. Luon nano-tekstitiedoston komennolla `sudoedit nano /home/maija/public_html/index.html` ja kirjoitan tiedostoon HTML5-koodia. Sivua ei kuitenkaan löydy.

![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/6bee4d55-95d9-439f-b871-95e50b6b1c14)



## D) Tyhjän virtuaalikoneen asentaminen // klo 10.25-11.00


Aloitan lataamalla Debianin uusimman version koneelleni. Avaan Virtualboxin ja lähden luomaan uutta virtuaalikonetta, jolle annan nimen DebianJanPen.
Annan koneelle RAM-muistia 5000 MB ja kovalevylle 60 GB. Painan "create" ja siirryn Virtualboxissa virtuaalikoneen asetuksiin. Lisäsin lataamani Debian live -levykuvan virtuaaliseen levyasemaan. Käynnistän virtuaalikoneen, ja valitsen boottausvalikossa Live system (amd64).

![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/e0459675-d8e9-4e7c-8ed4-e786e676b72e)


Tarkistan verkkoselaimessa, että verkkoyhteys, näppäimistö jne toimii. Valitsen työpöydältä "Install Debian", ja lähden asentamaan käyttöjärjestelmää. Valitsen kieleksi Amerikan englannin, sijainniksi Suomen sekä suomalaisen näppäimistön. Valitsen myös täpän Erase disk. Luon käyttäjän ja sille vahvan salasanan. Käynnistän asennuksen, ja asennuksen päätyttyä käynnistän koneen uudelleen. 

![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/9d9856f0-2381-4748-b378-88fdc624f2c1)

### Alkutoimet // klo 11.50-11.55
Avaan terminaalin ja haen päivitykset komennolla `sudo apt-get update`. Päivitän kaiken komennolla `sudo apt-get -y dist-upgrade`. Asennan tulimuurin ja laitan sen päälle 
    sudo apt-get -y install ufw
sudo ufw enable

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

Karvinen, T. 12.03.2019. Arvioitava laboratorioharjoitus - alkukevät 2019. Tero Karvisen verkkosivut. Luettavissa: https://terokarvinen.com/2019/03/12/arvioitava-laboratorioharjoitus-linux-palvelimet-ict4tn021-3004-ti-alkukevat-2019-5-op/?fromSearch=laboratorioharjoitus
Luettu 10.03.2024.

Karvinen, T. 22.01.2021. Install Debian on Virtualbox. Luettavissa: https://terokarvinen.com/2021/install-debian-on-virtualbox/ 
Luettu: 10.03.2024.
