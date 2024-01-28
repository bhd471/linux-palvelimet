# Komentaja Pingviini

## Tiivistys

- Komentorivi on nopea työkalu, joka on ollut käytössä jo ennen internettiä

Tärkeimpiä komentoja

- cd = liikkuminen komentorivillä johonkin tiettyyn kansioon. Lisätessä perään ".." mahdollistaa liikkumisen kansiossa ylöspäin
- ls = listaa työhakemiston tiedostot
- mkdir = tämän avulla voidaan luoda uusi kansio
- nano kissa.txt = luo uuden tekstitiedoston editoriin
  (Karvinen, 03.02.2020)

## Työasema ja Micro-editorin asennus

Käytin tehtävän suorittamiseen Acer Nitro N50-620 työasemaa, jolla on Windows 11 käyttöjärjestelmä. Työasemassani on Intel Core i5-prosessori, NVIDIA GeForce RTX 3060 Ti-näytönohjain, 16 Gt RAM-muistia sekä 1 TB tallennustilaa.

Aloitin tehtävän suorittamisen 23.01., klo 19.15. Jatkoin tehtävän suorittamista 28.01.

Aloitan tehtävän suorittamisen perehtymällä Teron ohjeisiin (Karvinen, h2- Komentaja Pingviini). Avaan komentorivin virtuaalikoneellani ja suoritan komennon `sudo apt-get update`. Tämän jälkeen minulta pyydetään salasanaa. Kirjoittaessa salasanaani komentoriville ei tullut minkäänlaisia merkkejä näkyviin, ja ihmettelin tätä hieman. Kirjautuminen kuitenkin onnistui. 

Klo. 19.25. Suoritan komentorivillä komennon `sudo apt-get -y install micro`, jonka pitäisi asentaa micro-editori. Luon uuden kansion, avaan editorin ja luon uuden tiedoston komennolla `micro testi.txt`. Hetken pähkäilin, sillä kirjoittaessani editoriin, teksti ei tullut näkyviin. Käytin kuitenkin virtuaalikonetta koko ruudun tilassa, ja lähti tämän jälkeen näkymään. Kokeilin vielä kirjoittamista editoriin, ja se onnistui hienosti. 


![microtesti](https://github.com/bhd471/linux-palvelimet/assets/148760837/14929848-fa8e-49c2-89c6-6f8f80752c3d)





## Rauta

29.01.2024, Klo 13.45. Aloitin taas päivittämällä listan, ja tämän jälkeen suoritan komennon `sudo apt install lshw`. Lähden suorittamaan komentorivillä komentoa `sudo lshw -short -sanitize`. Komennosta tulee ilmi, että käytän Virtualboxia, sekä antaa tietoja virtuaalikoneen komponenteista. Tässä listauksessa on mukana esimerkiksi prosessorin tiedot sekä tietoa muistista ja verkkoyhteyksistä. 


![sudosanitize](https://github.com/bhd471/linux-palvelimet/assets/148760837/aacbb5c3-245d-47ab-8e0e-76d9b3076b59)


## Apt

Klo 14.10. Tutkin verkosta mahdollisia komentoriviohjelmia asennettavaksi. Päädyin asentamaan Vimin, Cowsayn sekä CMatrixin. (Deepesh, 01.11.2022) Käytin asennukseen komentoa `sudo apt-get install cowsay cmatrix vim`. Komento asensi kaikki ohjelmat kerralla. 

Testasin kaikkien kolmen ohjelman toimivuuden. 


![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/591f0c73-a396-4033-870b-2b5f616c49c7)


![cowsay](https://github.com/bhd471/linux-palvelimet/assets/148760837/8ab06707-a9a2-4aa5-9fc4-7fb15b6f85ef)


![vim2](https://github.com/bhd471/linux-palvelimet/assets/148760837/8dfebc55-54c3-445e-9b44-33e5c92a64ec)


## FHS

Tärkeimpien kansioiden esittelyt komentorivillä. (Karvinen, 03.02.2020)

![fhs](https://github.com/bhd471/linux-palvelimet/assets/148760837/552c5f96-5066-4648-b2e2-07be61acee28)






![fhs2](https://github.com/bhd471/linux-palvelimet/assets/148760837/df36869c-5c7f-441d-aa97-0263e0f32fcf)

## The Friendly M

Esimerkkejä `grep`-komennon käytöstä. 
(Vivek, 27.12.2023)



![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/df940c69-63e8-428c-ac2e-7187e05ef222)



![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/575af8ed-fbf5-4492-a1d7-823fd44f5824)



## Pipe

Esimerkki putkien käytöstä. Testailin komentoa `ls -l | more `
(Geeks for geeks, 2023)



![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/99463fb6-6ea5-4f70-9529-e2c5c1725256)

## Loki

Osasin tarkastella lokia komennolla `journalctl -f`. Sain myös tuotettua `logger` -komennon avulla onnistuneen ilmoituksen lokiin, mutta epäonnistuneen ilmoituksen tuottamisessa en onnistunut. 
(Henry-Stocker, 22.05.2018)



![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/df5ff3b3-a234-4f9f-966c-f0d33f85da77)




### Lähdeluettelo

Karvinen, T. 11.01.2024. Linux Palvelimet 2024 alkukevät. Luettavissa: https://terokarvinen.com/2024/linux-palvelimet-2024-alkukevat/
Luettu 23.01.2024.

Karvinen, T. 03.02.2020. Command Line Basics Revisited. Luettavissa: https://terokarvinen.com/2020/command-line-basics-revisited/?fromSearch=command%20line%20basics%20revisited 
Luettu 23.01.2024.

Deepesh, S. 01.11.2022. 11 Fun Linux command-line programs you should try when bored. Make use of. Luettavissa: https://www.makeuseof.com/fun-linux-command-line-programs/
Luettu 28.01.2024.

Vivek, G. 27. 12.2023. How to use grep command in Linux/Unix with examples. Cyberciti. Luettavissa: https://www.cyberciti.biz/faq/howto-use-grep-command-in-linux-unix/
Luettu 28.01.2024.

Geeks for geeks. 05. 07.2023. Piping in Unix or Linux. Luettavissa: https://www.geeksforgeeks.org/piping-in-unix-or-linux/
Luettu 28.01.2024.

Henry-Stocker, S. 22.05.2018. How to use logger on Linux. Networkworld. Luettavissa: https://www.networkworld.com/article/965762/using-logger-on-linux.html
Luettu 28.01.2024.
