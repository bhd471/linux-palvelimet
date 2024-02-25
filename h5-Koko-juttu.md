# Koko juttu

Asennetaan uusi virtuaalikone, jolle tehdään alkutoimet, asennetaan Apache-weppipalvelin sekä SSH-palvelin. Luodaan etusivu palvelimelle, viritellään julkinen SSH-avain.
#### Alan suorittamaan tehtävää // 15.02.2024 Klo 13.30. 


- Avaan VirtualBoxin
- New -> Create virtual machine
- Nimeän koneen miumauksi
- Valitsen käyttöjärjestelmäksi Debian 12
  
  ![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/707f6cf5-b0bd-4197-a00b-fbb87d40d7ca)


- Hardware -> Base Memory: 4000 MB
- Hard Disk -> valitaan täppä Create a virtual hard disk now -> Hard disk size: 60 GB
- Painetaan finish -> Virtuaalikone on nyt luotu

 ![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/526bdc41-e008-4bec-bd2c-bf2ee8e60d83)


- Siirryn koneen asetuksiin -> Storage -> Controller: IDE alapuolella tyhjä CDROM  -> Painetaan siitä, oikealla aukeaa valikko -> Optical Drive: Choose virtual optical disk file .. -> Valitaan "debian-live-12.4.0-amd64-xfce.iso" -> Painetaan OK

- Käynnistetään luotu virtuaalikone tuplaklikkaamalla sitä
- Boottaus valikko aukeaa, valitaan Live system (amd64), omassa valikossa ylimpänä

- ![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/6a81c83e-9742-4766-809f-4ab49397e6d0)

- Live-työpöytä aukeaa -> avataan vasemmasta yläreunasta Applications -> Web browser ja testataan verkon toimintaa hakemalla janikapenttinen.com -> Toimii
  
![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/eed5ce60-dadb-41b0-9d10-f5f5a9a4c3bd)

![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/a8b9ad54-5416-432d-8b7d-845e76cf1139)

- Suljen selaimen

- Tuplaklikkaan työpöydältä kuvaketta Install Debian
- Työpödälle aukeaa ponnahdusikkuna, painetaan Mark Executable

 ![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/29d35437-6588-4818-ba69-371aa8e7a684)


- Ensimmäisenä latausikkunaan tulee näkyviin kielivalikko -> Valitaan kieleksi American English -> Next
- Location: Valitaan Suomi kartalta -> Next
- Näppäimistön valinta -> Valitaan Finnish ja Default -> Alapuolella kenttä jossa testataan näppäimistön toimivuutta
- Partitions -> Valitaan Erase disk
- Luodaan käyttäjä -> Täyttetään oma kokonimi, käyttäjä jolla kirjaudutaan sisään, valitaan koneelle nimi ja luodaan vahva salasana
- Yhteenveto
  - ![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/0a6c4d36-7ea6-475b-8d63-b7d64b83d64d)
- Painetaan Install
- Käynnistetään kone uudelleen

#### Asennus on valmistunut ja virtuaalikone on käynnistetty uudelleen // Klo 14.07
->
#### Aloitetaan alkutoimien tekeminen // klo 14.15

- Avataan terminaalin työpöydän alareunasta ja suoritetaan komento `sudo apt-get update`, joka päivittää listan mahdollisista saatavilla olevista päivityksistä
- Käytettäessä `sudo` komentoja, terminaali saattaa pyytää käyttäjän salasanaa, jolloin kirjoittaessa teksti ei tule terminaaliin näkyviin. Tästä ei kannata hämmentyä
- Päivitetään kaikki komennolla `sudo apt-get -y dist-upgrade`. Tässä meni n. 3-4 min.
- Ladataan koneelle tulimuuri komennolla `sudo apt-get -y install ufw`
- Tulimuuri päälle `sudo ufw enable`
  ![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/da49967c-6050-4b5a-948b-a5acbe8f51da)

- Käynnistetään kone uudelleen
  

#### Asennetaan Apache // klo 14.27

- Avataan terminaali ja suoritetaan komento `sudo apt-get -y install apache2`, joka asentaa Apache-weppipalvelimen koneelle
- Korvataan testisivu komennolla `echo "Moikka"|sudo tee /var/www/html/index.html`
  ![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/08974c93-29ed-459e-ad89-ada19c42719c)

  - Luodaan uusi kansio name based virtual hostia varten komennolla `mkdir webbi`
  - Aletaan luomaan name based virtual hostia
  - Komennolla `sudoedit /etc/apache2/sites-available/janikap.example.com.conf` luodaan uusi nano-tekstitiedosto, johon täytetään Virtual Host-tiedot, jotka näkyvät alapuolella olevassa kuvassa
  - ![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/6cc1f30c-6409-4de0-81ec-7d4782e8e257)
 
  - Komennolla `sudo a2ensite janikap.example.com` otetaan sivu käyttöön
  - Komennolla `sudo systemctl restart apache2` käynnistetään weppipalvelin uudelleen
  - Siirrytään hakemistoon `cd /etc/apache2/sites-available/`
  - Sammutetaan default-palvelin `sudo a2dissite 000-default.conf`
  - Käynnistetään apache restart- komennolla uudelleen

  #### Luodaan sivu tavallisena käyttäjänä // Klo 14.55

  - Komennolla `mkdir -p /home/janikap/webbi/janikap.example.com/`luodaan hakemisto
  - Lisätään teksti sivulle `echo heippa > /home/janikap/webbi/janikap.example.com/index.html`

  Tilanne sivulla tällä hetkellä:
  ![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/a1fb56db-e23d-401a-b4b3-8bcd4cf5e4f0)

 #### Lähdetään selvittämään mistä ongelma johtuu // Klo. 15.05

  - Suoritan terminaalissa komennon `sudo tail -10 /var/log/apache2/error.log
  - Ensimmäisenä silmään pistää kirjoitusvirhe "/home/janikap/webbi/janikap.exaple.com"
  - Kirjoitusvirhe löytyi Virtual Host-asetuksista DocumentRootista
  - Käynnistän apache-palvelimen uudelleen restart-komennolla
  - Sivun ongelma ei kuitenkaan johtunut tästä, joten suuntaan uudelleen tutkimaan lokitiedostoja
  
  #### Päädyn jatkamaan tehtävän suorittamista toisena ajankohtana // Klo 15.30


  #### Tehtävän suorittaminen jatkuu // 25.02.2024 klo. 13.35

  - Päätän jatkaa ongelman selvittämistä
  - Huomaan, että virheilmoitusta ei jostain syystä enää tule
  - ![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/dccaabe2-fbeb-47a4-8d63-23be795a7db5)
 

    
## B) Pubkey 

#### Julkinen SSH-avain // klo 14.05

- Lähden asentamaan SSH-palvelinta koneelle `sudo apt-get update` ja `sudo apt-get install ssh`
- Syötin terminaaliin komennon `ssh janikap@localhost`, varmistus haluanko jatkaa yhdistämistä
- Syötin käyttäjän salasanan
- Suoritan komennon `ssh-keygen -t rsa` ja `ssh-copy-id janikap@localhost`
- Käynnistän SSH-palvelimen uudelleen `sudo systemctl restart ssh`
- Pääsen kirjautumaan palvelimelle komennolla `ssh janikap@localhost`

 ![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/3205f93a-bb73-433b-8cb7-5c26f89f7b9f)

  


  ## C) Digging host 
  
  #### Domain-nimen tutkiminen // klo. 14.25

  - Kirjaudun alkuperäiselle virtuaalikoneelleni voidakseni tutkia domain-nimeni tietoja
  - Suoritan terminaalilla komennon `sudo apt-get -y install bind9-dnsutils bind9-host`, joka asentaa käyttöön `host` ja `dig` komennot
  - `host janikapenttinen.com` komento ilmoittaa domainin IP-osoitteen
  - `dig janikapenttinen.com` komento ilmoittaa domainin IP-osoitteen ja sen TTL. NOERROR tarkoittaa ettei ole virheitä, Answer section kertoo mitä domainia kysyin.
    (Linux.fi-wiki, 19.01.2021)
  
![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/9a0eace6-9a91-41c5-a094-0017cdf48f5a)

     



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

Karvinen, T. H5 - Koko juttu, Linux-palvelimet kurssi. Tero Karvisen verkkosivut. Luettavissa: https://terokarvinen.com/2024/linux-palvelimet-2024-alkukevat/ 
Luettu 15.02.2024.

Karvinen, T. 10.04.2018. Name Based Virtual Hosts on Apache - Multiple Websites to Single IP Address. Tero Karvisen verkkosivut. Luettavissa: https://terokarvinen.com/2018/04/10/name-based-virtual-hosts-on-apache-multiple-websites-to-single-ip-address/ 
Luettu 15.02.2024.

Linux.fi-wiki. 19.01.2021. Dig. Suomenkielinen Linux-wiki. Luettavissa: https://www.linux.fi/wiki/Dig
Luettu 25.02.2024.



