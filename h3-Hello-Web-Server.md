# H3 - Hello Web Server

## Tiivistelmä

Lähdin suorittamaan tehtävää 31.01.2024.

## A) Localhost


Klo 19.45. Apache-web-palvelin löytyy virtuaalikoneeltani jo asennettuna. 


![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/ee58ae6a-ae58-4a36-9a4c-da27034d9a69)

Web-palvelin vastaa osoitteella http://localhost.

## B) Loki



![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/c0fc165b-ec67-4e4b-b4f0-82f7546060c5)


## C) Etusivu uusiksi

Aloitin poistamalla apachen asennuksen kokonaan sekä vanhat tiedostot käyttämällä komentoa `sudo purge apache2`. Poistin myös kansion janika.example.com komennolla `sudo rmdir /home/janika/webbi/janika.example.com`. (Brown, 15.12.2020)

Tämän jälkeen lähden lataamaan apachea uudelleen komennolla `sudo apt-get -y install apache2`. Syötän komennon `sudoedit /etc/apache2/sites-available/hattu.axample.com.conf`. Komento avaa nano-editorin, johon syötän tarvittavat Virtual Host tiedot. Tässä vaiheessa myös tarkistan oikean asettelun tekstille.

![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/27c0f691-27cc-458f-b516-535ecacbfb7b)


Aktivoin palvelimen komennolla `sudo a2ensite hattu.example.com`. Käynnistän sen uudelleen komennolla `sudo systemctl restart apache2`. Luon hakemiston käyttäen komentoa `mkdir -p /home/janika/webbi/hattu.example.com/`. Seuraavaksi komennolla `echo hattu > /home/janika/webbi/hattu.example.com/index.html` kirjoitan tekstin hattu index.html sivulle. 

Testaan komennolla `curl -H 'Host: hattu.example.com' loclahost` sekä `curl localhost`. Tässä vaiheessa sivulla ei näy muuta tekstiä kuin "Default". 

## E) HTML5-sivu

## F) Esimerkit komennoista


### Lähdeluettelo

Karvinen, T. Linux-palvelimet alkukevät 2024. Luettavissa: https://terokarvinen.com/2024/linux-palvelimet-2024-alkukevat/
Luettu 31.01.2024. 

Brown, K. How to remove Apache server from Ubuntu. Luettavissa: https://linuxconfig.org/how-to-remove-apache-web-server-from-ubuntu
Luettu 31.01.2024.
