## a) Koko juttu

Klo 13.30. 
Aloin tutkimaan tehtävänantoa.

- Avaan VirtualBoxin
- New -> Create virtual machine
- Nimeän koneen miumauksi
- Valitsen käyttöjärjestelmäksi Debian 12
- 
  ![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/707f6cf5-b0bd-4197-a00b-fbb87d40d7ca)


- Hardware -> Base Memory: 4000 MB
- Hard Disk -> valitaan täppä Create a virtual hard disk now -> Hard disk size: 60 GB
- Painetaan finish -> Virtuaalikone on nyt luotu

- ![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/526bdc41-e008-4bec-bd2c-bf2ee8e60d83)
- ![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/408b63c0-7496-457d-b559-1b1006a5fe46)

- Siirryn koneen asetuksiin -> Storage -> Controller: IDE alapuolella tyhjä CDROM  -> Painetaan siitä, oikealla aukeaa valikko -> Optical Drive: Choose virtual optical disk file .. -> Valitaan "debian-live-12.4.0-amd64-xfce.iso" -> Painetaan OK

- Käynnistetään luotu virtuaalikone tuplaklikkaamalla sitä
- Boottaus valikko aukeaa, valitaan Live system (amd64), omassa valikossa ylimpänä

- ![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/6a81c83e-9742-4766-809f-4ab49397e6d0)

- Live-työpöytä aukeaa -> avataan vasemmasta yläreunasta Applications -> Web browser ja testataan verkon toimintaa hakemalla janikapenttinen.com -> Toimii
- 
![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/eed5ce60-dadb-41b0-9d10-f5f5a9a4c3bd)

![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/a8b9ad54-5416-432d-8b7d-845e76cf1139)

- Suljen selaimen

- Tuplaklikkaan työpöydältä kuvaketta Install Debian
- Työpödälle aukeaa ponnahdusikkuna, joka varoittaa
-
- ![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/29d35437-6588-4818-ba69-371aa8e7a684)


- Ensimmäisenä latausikkunaan tulee näkyviin kielivalikko -> Valitaan kieleksi American English -> Next
- Location: Valitaan Suomi kartalta -> Next
- Näppäimistön valinta -> Valitaan Finnish ja Default -> Alapuolella kenttä jossa testataan näppäimistön toimivuutta
- Partitions -> Valitaan Erase disk
- Luodaan käyttäjä -> Täyttetään oma kokonimi, käyttäjä jolla kirjaudutaan sisään, valitaan koneelle nimi ja luodaan vahva salasana
- Yhteenveto
-   ![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/0a6c4d36-7ea6-475b-8d63-b7d64b83d64d)
- Painetaan Install
- Käynnistetään kone uudelleen

Klo 14.07 - asennus on valmistunut ja virtuaalikone on käynnistetty uudelleen

Aloitetaan alkutoimien tekeminen // klo 14.15

- Avataan terminaali työpöydän alareunasta ja suoritetaan komento `sudo apt-get update`, joka päivittää listan mahdollisista saatavilla olevista päivityksistä
- Käytettäessä `sudo` komentoja, terminaali saattaa pyytää käyttäjän salasanaa, jolloin kirjoittaessa teksti ei tule terminaaliin näkyviin. Tästä ei kannata hämmentyä
- Päivitetään kaikki komennolla `sudo apt-get -y dist-upgrade`. Tässä meni n. 3-4 min.
- Ladataan koneelle tulimuuri komennolla `sudo apt-get -y install ufw`
- Tulimuuri päälle `sudo ufw enable`
  ![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/da49967c-6050-4b5a-948b-a5acbe8f51da)

- Käynnistetään kone uudelleen
  

Asennetaan Apache // klo 14.27

- Avataan terminaali ja suoritetaan komento `sudo apt-get -y install apache2`, joka asentaa Apache-weppipalvelimen koneelle
- Korvataan testisivu komennolla `echo "Moikka"|sudo tee /var/www/html/index.html`
  ![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/08974c93-29ed-459e-ad89-ada19c42719c)

  - Luodaan uusi kansio name based virtual hostia varten komennolla `mkdir webbi`
  - Aletaan luomaan name based virtual hostia
  - Komennolla `sudoedit /etc/apache2/sites-available/janikap.example.com.conf` luodaan uusi nano-tekstitiedosto, johon täytetään Virtual Host-tiedot, jotka näkyvät alapuolella olevassa kuvassa
  - ![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/6cc1f30c-6409-4de0-81ec-7d4782e8e257)
 
  - Komennolla `sudo a2ensite janikap.example.com`
  - Komennolla `sudo systemctl restart apache2` käynnistetään weppipalvelin uudelleen
  - Siirrytään hakemistoon `cd /etc/apache2/sites-available/`
  - Sammutetaan default-palvelin `sudo a2dissite 000-default.conf`
  - Käynnistetään apache restart- komennolla uudelleen

  Luodaan sivu tavallisena käyttäjänä // Klo 14.55

  - Komennolla `mkdir -p /home/janikap/webbi/janikap.example.com/`
  - Lisätään teksti sivulle `echo heippa > /home/janikap/webbi/janikap.example.com/index.html`

  Tilanne sivulla tällä hetkellä:
  ![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/a1fb56db-e23d-401a-b4b3-8bcd4cf5e4f0)

  Lähdetään selvittämään mistä ongelma johtuu // Klo. 15.05

  - Suoritan terminaalissa komennon `sudo tail -10 /var/log/apache2/error.log
  - Ensimmäisenä silmään pistää kirjoitusvirhe "/home/janikap/webbi/janikap.exaple.com"
  - Kirjoitusvirhe löytyi Virtual Host-asetuksista DocumentRootista
  - Käynnistän apache-palvelimen uudelleen restart-komennolla
  - Sivun ongelma ei kuitenkaan johtunut tästä, joten suuntaan uudelleen tutkimaan lokitiedostoja
   Klo 15.30 // Päädyn jatkamaan tehtävän suorittamista toisena ajankohtana
    
![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/3b09807d-5906-4a37-8c6e-2984860679e3)

  
  

  - ![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/70cdd249-ddac-41b3-8c86-1c549f52226c)

 

  



![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/96b9376e-dfdf-42df-b7b8-bd3ed51e89a6)

![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/50aba0b8-f7ba-410c-849b-449daed5dcae)



### Oma käyttöympäristö

Käytin tehtävän suorittamiseen Acer Nitro N50-620 työasemaa, jolla on Windows 11 käyttöjärjestelmä. Työasemassani on Intel Core i5-prosessori, NVIDIA GeForce RTX 3060 Ti-näytönohjain, 16 Gt RAM-muistia sekä 1 TB tallennustilaa.


### Lähdeluettelo

Karvinen, T. H5 - Koko juttu, Linux-palvelimet kurssi. Tero Karvisen verkkosivut. Luettavissa: https://terokarvinen.com/2024/linux-palvelimet-2024-alkukevat/ Luettu 15.02.2024.
