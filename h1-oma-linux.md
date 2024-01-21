# Oma Linux

## Tiivistys

### Raportista

- Raporttia tulisi kirjoittaa samaan aikaan kun tehdään tehtäviä
- Raportin tulee olla niin selkeä ja kuvaava, että joku toinen voisi suorittaa tehtävän sen perusteella
- Raportin tulee olla huolellisesti kirjoitettu, ja sisältää lähdeviittaukset
  (Karvinen, 04.06.2006)

### Free Software ja neljä vapautta

- Käsitteellä "Free Software" tarkoitetaan käyttäjien oikeutta esimerkiksi kopioida ja muuttaa ohjelmistoa. Tällä ei kuitenkaan tarkoiteta ilmaista ohjelmistoa.
- Ohjelmistoa voidaan kutsua "Free Softwareksi", jos sen käyttäjällä on neljä vapautta
- Vapaus 0: Käyttäjän vapaus suorittaa ohjelma haluamallaan tavalla ja mihin tarkoitukseen tahansa
- Vapaus 1: Käyttäjän oikeus lähdekoodiin sekä vapaus muuttaa ohjelmaa haluamallaan tavalla
- Vapaus 2: Käyttäjän vapaus jakaa kopioita
- Vapaus 3: Käyttäjän vapaus muokattujen versioiden jakeluun
  (Free Software Foundation, Inc. s. a.)

## Linuxin asennus

Tein harjoituksen sunnuntaina 21.01.2024. Käytin harjoituksen tekemiseen Acer Nitro N50-620- työasemaa, Windows 11-käyttöjärjestelmä. (Karvinen, 2023. h1 - Oma Linux)

Klo 19.15. Lähden tutustumaan Teron sivun ohjeisiin liittyen Debianin lataamiseen. Aloitan Debianin lataamisen heidän verkkosivuiltaan. Latasin koneelleni tiedoston debian-live-12.4.0-amd64-xfce.iso. 

### Virtualboxin asennus
Klo 19.32. Olen hetken miettinyt, mikä on homman seuraava vaihe. Tajuan, että minun tulisi asentaa myös Virtualbox koneelleni. Siirryn Virtualboxin sivuille, josta lähden lataamaan Windows-versiota koneelleni. Latauksen käynnistyessä ohjelma pyytää lupaa käyttää konetta, tämä annetaan. Asennusohjelmassa muutama nextin klikkaus, ja päästään asentamaan. Ohjelma ilmoittaa, että se joutuu katkaisemaan netin hetkeksi. Lataus sujui nopeasti. (Oracle VM Virtualbox, 2023)


Klo 19.40. Avaan Virtualboxin, ja valitsen ohjelman yläreunasta Machine -> New. Valitsen alareunasta täpän Expert mode. Annan virtuaalikoneelle nimen "JanPen". Avaan kohdan Hardware, ja muistin kooksi 4000 MB. Tämän jälkeen avaan kohdan Hard Disk, ja täppä "Create a Virtual hard disk now". Muistia 60GB. Painan Finish. 


Klo. 19.52. Valitsen Virtualboxissa juuri luomani koneen, ja Settings -> Storage. Controller: IDE alapuolelta valitsen Empty. Oikealla puolella Attributes alapuolella lukee Optical Drive. Tämän vieressä on pieni levyn kuva, josta klikkaamalla aukeaa Optical Disk Selector. Täällä painan Host Drive 'D:'. Ja tämän jälkeen ok, ja suljen näkymän. 

### Virtuaalikoneen käynnistäminen
Klo. 20.00. Lähden boottaamaan juuri luomaani virtuaalikonetta JanPen tuplaklikkaamalla sitä. Valitsen Boot menusta ylimmän vaihtoehdon, eli Live system (amd64). Tämä kohta hieman jännittää, sillä näyttää hieman erilaiselta kuin ohjeissa. Linuxin työpöytä tulee näkyviin. Vasemmassa yläreunassa on täppä "Applications" jonka painamisen jälkeen valitaan Web Browser. Kokeilin hakukoneella hakusanaa kissa, ja haku onnistui. Suljen hakukoneen. 


![bootloader](https://github.com/bhd471/linux-palvelimet/assets/148760837/351901c7-0c36-4ed9-bb23-3d72d6e95b0a)



### Debianin lataaminen ja ongelma näytön skaalautumisen kanssa
Klo. 20.08. Valitsen työpöydältä "Install Debian", ja saan ilmoituksen tuntemattomasta lähteestä. Suostun lataamaan tästä huolimatta. Valitsen kielekseni American English, maaksi Suomen. Seuraavaksi täytyy valita näppäimistö asetukset. Näppäimistömalliksi Generic 105-key PC, Finnish ja Default. Seuraavassa kohdassa valitsen Erase Disk, ja boot loader location on Master boot record. Seuraavaksi täytän kokonimeni, ja valitsen sisäänkirjautumiseen nimen janika. Annan koneen nimeksi kissa. Valitsen pitkän salasanan joka sisältää erikoismerkkejä ja numeroita. 

![nimivalinnat](https://github.com/bhd471/linux-palvelimet/assets/148760837/a6d63422-92e2-413a-8eb9-dd33826f6dc4)


Tämän jälkeen saan yhteenvedon juuri valitsemistani asetuksista. Tässä vaiheessa törmään outoon ongelmaan: Miten saan asennuksen käynnistettyä? 




Klo. 21.00. Pitkän miettimisen jälkeen tajusin, että virtuaalikone ei näy kokonaisuudessaan jostain syystä ruudullani. Löysin asennuksen käynnistysnappulan oikeasta alareunasta, mutta en aluksi tajunnut tätä. Lopulta sain asennuksen suoritettua onnistuneesti loppuun. Käynnistin koneen uudelleen. 

(Karvinen Tero, Install Debian, 2023)

![ei_toimi](https://github.com/bhd471/linux-palvelimet/assets/148760837/6d7d66eb-75dd-4b5d-8e6f-93d1397163f0)

Tässä kuvassa voi nähdä, kuinka vähän Install-painikkeesta on näkyvissä näytön skaalautumisen takia. 

### Lähdeluettelo
  Karvinen, T. 04.06.2006. Raportin kirjoittaminen. Luettavissa:
https://terokarvinen.com/2006/raportin-kirjoittaminen-4/ 
Luettu: 21.01.2024.

  Free Software Foundation Inc. s. a. What is Free Software? Luettavissa: 
  https://www.gnu.org/philosophy/free-sw.html
  Luettu: 21.01.2024.

  Karvinen, T. 2023. Install Debian on Virtualbox. Luettavissa:
  https://terokarvinen.com/2021/install-debian-on-virtualbox/
  Luettu: 21.01.2024.

  Oracle. 2023. Download Virtualbox. Luettavissa: 
  https://www.virtualbox.org/wiki/Downloads
  Luettu: 21.01.2024.

 

  
