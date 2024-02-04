# H3 - Hello Web Server

## Tiivistelmä



## A) Localhost


Apache-web-palvelin löytyy virtuaalikoneeltani jo asennettuna. 


![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/ee58ae6a-ae58-4a36-9a4c-da27034d9a69)

Web-palvelin vastaa osoitteella http://localhost.

## B) Loki

Jostain syystä en saanut access.log-tiedostoja auki. Kokeilin komentoja `sudo tail -10 /var/log/apache2/access.log` sekä `sudo tail -f /var/log/apache2/access.log`. Error-log-tiedostot aukesivat kyllä. 

![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/c0fc165b-ec67-4e4b-b4f0-82f7546060c5)


## C) Etusivu uusiksi

Aloitin poistamalla apachen asennuksen kokonaan sekä vanhat tiedostot käyttämällä komentoa `sudo purge apache2`. Poistin myös kansion janika.example.com komennolla `sudo rmdir /home/janika/webbi/janika.example.com`. (Brown, 15.12.2020)

Tämän jälkeen lähden lataamaan apachea uudelleen komennolla `sudo apt-get -y install apache2`. Syötän komennon `sudoedit /etc/apache2/sites-available/hattu.axample.com.conf`. Komento avaa nano-editorin, johon syötän tarvittavat Virtual Host tiedot. Tässä vaiheessa myös tarkistan oikean asettelun tekstille.

![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/27c0f691-27cc-458f-b516-535ecacbfb7b)


Aktivoin palvelimen komennolla `sudo a2ensite hattu.example.com`. Käynnistän sen uudelleen komennolla `sudo systemctl restart apache2`. Luon hakemiston käyttäen komentoa `mkdir -p /home/janika/webbi/hattu.example.com/`. Seuraavaksi komennolla `echo hattu > /home/janika/webbi/hattu.example.com/index.html` kirjoitan tekstin hattu index.html sivulle. 

Testaan komennolla `curl -H 'Host: hattu.example.com' loclahost` sekä `curl localhost`. Tässä vaiheessa sivulla ei näy muuta tekstiä kuin "Default". Pitkän miettimisen ja googlailun jälkeen (Niazi, R. 25.03.2022) tajusin käyttää komentoa `sudo a2dissite 000-default.conf`. Tämän jälkeen index.html sivulle syöttämäni teksti tuli näkyviin localhost-sivulla. 





## E) HTML5-sivu

Lähdin työstämään index.html tiedostossa validia HTML-sivua. Olen joskus aikaisemmin luonut verkkosivun käyttämällä HTML5, joten tälläisen simppelin sivun luominen oli yksinkertaista. Validoin sivuni käyttämällä HTML Validatoria. (AppDevTools)


![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/70b03807-a8d2-47ff-90b3-21a14fd716c5)


![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/62d5965e-41aa-43d0-b221-36532cb7ab24)


![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/5640b775-f055-4fb3-8e16-e91bc940233a)



## F) Esimerkit curl-komennoista

Komennolla `curl -i localhost` komentoriville tulostuu HTTP-otsakkeet. 
"HTTP/1.1 200 OK" kertoo käytetyn protokolla ja että pyyntö on onnistunut. (Mdn Web Docs)
"Server: Apache/2.4.57 (Debian)" kertoo, että käytössä on Apache web-ohjelmiston versio 2.4.57. 




![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/721a1ac3-30bd-406a-a5ae-092a5e4aa383)


Komennolla `curl localhost` saadaan näkyviin komentoriville localhost sivulla näkyvä koodi.


![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/2428ec6f-57fd-4c90-9ecc-9fd74c734e8e)



### Lähdeluettelo

Karvinen, T. Linux-palvelimet alkukevät 2024. Luettavissa: https://terokarvinen.com/2024/linux-palvelimet-2024-alkukevat/
Luettu 31.01.2024. 

Brown, K. How to remove Apache server from Ubuntu. Luettavissa: https://linuxconfig.org/how-to-remove-apache-web-server-from-ubuntu
Luettu 31.01.2024.

Niazi, R. How to set up an Apache web server on Linux. Luettavissa: https://www.makeuseof.com/tag/set-apache-web-server-3-easy-steps/
Luettu 01.02.2024.

AppDevTools. HTML Validator. Käytettävissä: https://appdevtools.com/html-validator
Käytetty: 04.02.2024.

Mdn Web Docs. 200 OK. Luettavissa: https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/200
Luettu 04.02.2024.
