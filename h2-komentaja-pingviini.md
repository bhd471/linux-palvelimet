# Komentaja Pingviini

## Tiivistys

- Komentorivi on nopea työkalu, joka on ollut käytössä jo ennen internettiä

Tärkeimpiä komentoja

- cd = liikkuminen komentorivillä johonkin tiettyyn kansioon. Lisätessä perään ".." mahdollistaa liikkumisen kansiossa ylöspäin
- ls = listaa työhakemiston tiedostot
- mkdir = tämän avulla voidaan luoda uusi kansio
- nano kissa.txt = luo uuden tekstitiedoston editoriin
  (Karvinen, 03.02.2020)

Käytin tehtävän suorittamiseen Acer Nitro N50-620 työasemaa, jolla on Windows 11 käyttöjärjestelmä. Työasemassani on Intel Core i5-prosessori, NVIDIA GeForce RTX 3060 Ti-näytönohjain, 16 Gt RAM-muistia sekä 1 TB tallennustilaa.

Aloitin tehtävän suorittamisen 23.01., klo 19.15. 

Aloitan tehtävän suorittamisen perehtymällä Teron ohjeisiin. Avaan komentorivin virtuaalikoneellani ja suoritan komennon sudo apt-get update. Tämän jälkeen minulta pyydetään salasanaa. Kirjoittaessa salasanaani komentoriville ei tullut minkäänlaisia merkkejä näkyviin, ja ihmettelin tätä hieman. Kirjautuminen kuitenkin onnistui. 

Klo. 19.25. Suoritan komentorivillä komennon sudo apt-get -y install micro, jonka pitäisi asentaa micro-editori. Luon uuden kansion, avaan editorin ja luon uuden tiedoston komennolla micro testi.txt. Hetken pähkäilin, sillä kirjoittaessani editoriin, teksti ei tullut näkyviin. Käytin kuitenkin virtuaalikonetta koko ruudun tilassa, ja lähti tämän jälkeen näkymään. Kokeilin vielä kirjoittamista editoriin, ja se onnistui hienosti. 


![microtesti](https://github.com/bhd471/linux-palvelimet/assets/148760837/14929848-fa8e-49c2-89c6-6f8f80752c3d)





B) 29.01.2024, Klo 13.45. Aloitin taas päivittämällä listan, ja tämän jälkeen suoritan komennon sudo apt install lshw. Lähden suorittamaan komentorivillä komentoa sudo lshw -short -sanitize. 

Komennosta tulee ilmi, että käytän Virtualboxia, sekä antaa tietoja virtuaalikoneen komponenteista. Tässä listauksessa on mukana esimerkiksi prosessorin tiedot sekä tietoa muistista ja verkkoyhteyksistä. 


![sudosanitize](https://github.com/bhd471/linux-palvelimet/assets/148760837/aacbb5c3-245d-47ab-8e0e-76d9b3076b59)

C) Klo 14.10. Tutkin verkosta mahdollisia komentoriviohjelmia asennettavaksi. Päädyin asentamaan Vimin, Cowsayn sekä CMatrixin. (Deepesh Sharma, 01.11.2022) Käytin asennukseen komentoa sudo apt-get install cowsay cmatrix vim. Komento asensi kaikki ohjelmat kerralla. 

Testasin kaikkien kolmen ohjelman toimivuuden. 

![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/591f0c73-a396-4033-870b-2b5f616c49c7)


![cowsay](https://github.com/bhd471/linux-palvelimet/assets/148760837/8ab06707-a9a2-4aa5-9fc4-7fb15b6f85ef)

![vim2](https://github.com/bhd471/linux-palvelimet/assets/148760837/8dfebc55-54c3-445e-9b44-33e5c92a64ec)







### Lähdeluettelo

Karvinen Tero, 03.02.2020. Command Line Basics Revisited. Luettavissa: https://terokarvinen.com/2020/command-line-basics-revisited/?fromSearch=command%20line%20basics%20revisited 
Luettu 23.01.2024.

https://docs.rackspace.com/docs/command-line-text-editors-in-linux

