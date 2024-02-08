## x) Lue ja tiivistä

### Teoriasta käytäntöön pilvipalvelimen avulla

- Pilven vuokraaminen verkosta, oman julkisen palvelimen asentaminen verkkoon

- Reikä SSH-palvelimelle, jonka jälkeen palvelin suojataan tulimuurilla

- Luodaan Apache-webbipalvelimella kotisivut

- Päivitetään kaikki palvelimen ohjelmat

 (Lehto, 14.02.2022.)

### First Steps on a New Virtual Private Server

- Verkkotunnukset ja yksityiset virtuaalipalvelimet ovat kovasti kilpailtuja

- Uuden serverin voi luoda esim. DigitalOcean nimisessä palvelussa

- Tehdään reikä tulimuuriin, suljetaan root-tunnus, päivitetään softa.

- Gandi ja NameCheap- nimiset palvelut tarjoavat vuokrattavia domain-nimiä

(Karvinen, 19.09.2017)

### Oma käyttöympäristö

Käytin tehtävän suorittamiseen Acer Nitro N50-620 työasemaa, jolla on Windows 11 käyttöjärjestelmä. Työasemassani on Intel Core i5-prosessori, NVIDIA GeForce RTX 3060 Ti-näytönohjain, 16 Gt RAM-muistia sekä 1 TB tallennustilaa.

## a) Virtuaalipalvelimen vuokraaminen

Siirryin DigitalOceanin sivuille, johon kirjauduin Googlen tunnuksilla. Sivusto lupasi 200 dollarin edestä ilmaisia krediittejä 60 päivän ajaksi. Jouduin varmentamaan identiteettini syöttämällä luottokorttitietoni sivustolle. Tililtäni veloitettiin 5 dollaria, mutta tämä luvattiin palauttaa viikon kuluessa. Tämän jälkeen päivitin tiimini nimen omaksi nimekseni. 

Aloin luomaan uutta virtuaalipalvelinta kohdasta "Droplets". Sivun mukaan palvelimen ylläpitäminen maksaa alkaen 4 dollaria kuukaudessa. Valitsin uuden virtuaalikoneen maaksi Amsterdamin, ja käyttöjärjestelmäksi Debian 12.  Valitsin 'Shared CPU Basic' ja 'Regular CPU, Disk type SSD'. Seuraavaksi jouduin valitsemaan minkä kokoisen paketin tarvitsen. Päädyin toiseksi halvimpaan, jonka hinta oli 6 dollaria kuukaudessa, sisältäen 1 GB prosessori, 25 GB SSD-tilaa ja 1000 GB siirtodataa. Seuraavaksi pyydettiin valitsemaan kirjautuminen salasanalla tai SSH avaimella. Vielä tässä vaiheessa en tiedä oikeastaan mitään SSH-avaimista, joten valitsen salasanan. Salasanan luomisen jälkeen kysellään, haluanko lisäpalveluita, joista en ota mitään. Lopuksi valitsin, että tahdon luoda yhden koneen, jonka nimesin mauksi.

![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/be396f8c-1780-439f-8da4-ac58a64acdf4)


## b) Alkutoimet omalla palvelimella

Aloitan asentamalla SSH-ohjelman virtuaalikoneelleni, suorittamalla komentorivillä ensin komennon `sudo apt-get update` ja sen jälkeen `sudo apt-get install ssh`. Seuraavaksi syötin komennon `ssh root@159.65.194.165`. Minulta pyydettiin virtuaalipalvelimeni salasanaa, jonka syötin. Sain yhteyden palvelimelleni, ja hain päivitykset `sudo apt-get update` komennolla. Asensin tulimuurin komennolla `sudo apt-get install ufw`. Tein reiän tulimuuriin komennolla `sudo ufw allow 22/tcp` ja laitoin muurin päälle `sudo ufw enable`.




<img src="polku/kuva.jpg" alt="Kuva nimi" width="400" height="300">![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/7c1a1f2a-524a-4e5d-bbfc-344874cb1380)


Aloin asentamaan weppipalvelinta uudelle virtuaalipalvelimelleni. Suoritin komentorivillä komennon `sudo adduser janika`, joka luo palvelimelle käyttäjän. Keksin vahvan salasanan, ja syötin kokonimeni. Muut kohdat jätin tyhjäksi. Annoin käyttäjälle pääkäyttäjän oikeudet komennolla `sudo adduser janika sudo`. Avasin uuden terminaalin, ja kokeilin käyttäjän toimivuutta. Päivitin päivitystiedot onnistuneesti. 

Suljin root-tunnuksen komennolla `sudo usermod --lock root`. Suljen vielä kirjautumisen SSH- kautta komennolla `sudoedit /etc/ssh/sshd_config`. Lisäsin avautuvaan nanotiedostoon tekstin PermitRootLogin no. Suoritin vielä komennon `sudo service ssh restart`.


## c) Weppipalvelimen asentaminen


Kirjauduin SSH-yhteydellä palvelimelleni sisään. Asennan päivitykset komennoilla `sudo apt-get update` ja `sudo apt-get upgrade`. Tein toisen reiän tulimuuriin komennolla `sudo ufw allow 80/tcp`. 


Seuraavaksi asensin Apachen virtuaalikoneelleni (Karvinen, 10.04.2018). Loin uuden kansion 'netti' palvelinta varten.  Korvasin testisivun komennolla `echo "Default"|sudo tee /var/www/html/index.html`. 


![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/d3ff48d0-09e6-4319-964e-ed8b15097e25)

Kokeilin useammalla laitteella sivun toimivuutta. 


## d) Domainin vuokraaminen

Siirryin NameCheapin sivuille valitsemaan domain-nimeä. Päädyin nimeen janikapenttinen.com. Sivustolla oli uusille käyttäjille tarjous, jolla saisin nimen hintaan 5,98 dollaria/vuosi. Vuokraaminen oli simppeliä.

![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/74cfc86c-09f1-44f0-994e-c76754e5f6b8)

Seuraavaksi lähdin ohjaamaan domainia virtuaalipalvelimelle. Domain list -> Advanced DNS ->  Host records. Loin tähän kohtaan kaksi uutta tiedostoa. Ensimmäiselle hostiksi www, valueksi virtuaalipalvelimen IP-osoite ja TTL- 5 min välein. Toiselle hostiksi @, muuten samat valinnat.

![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/ea39207c-6f8d-4ea5-98c2-6a162420e41f)


## Lopputulos

Loin name based virtual hostin ja lisäsin tekstiä sivulle, sivu näyttää tällä hetkellä tältä. Toimii eri selaimilla, myös puhelimella.

![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/369d5734-d845-4430-a11d-816a79465c6b)


### Lähdeluettelo

Karvinen, T. H4 - Maailma kuulee, Linux-palvelimet kurssi. Tero Karvisen verkkosivut. Luettavissa: https://terokarvinen.com/2024/linux-palvelimet-2024-alkukevat/
Luettu 06.02.2024.

Lehto, S. 14.02.2022. Teoriasta käytäntöön pilvipalvelimen avulla. Susanna Lehdon blogi. Luettavissa: https://susannalehto.fi/2022/teoriasta-kaytantoon-pilvipalvelimen-avulla-h4/
Luettu: 06.02.2024.

Karvinen, T. 19.09.2017. First steps on a new virtual private server - an example on DigitalOcean and Ubuntu 16.04 LTS. Tero Karvisen verkkosivut. Luettavissa: https://terokarvinen.com/2017/first-steps-on-a-new-virtual-private-server-an-example-on-digitalocean/
Luettu: 06.02.2024.

Karvinen, T. 10.04.2018. Name Based Virtual Hosts on Apache - Multiple Websites to Single IP Address. Tero Karvisen verkkosivut. Luettavissa: https://terokarvinen.com/2018/04/10/name-based-virtual-hosts-on-apache-multiple-websites-to-single-ip-address/
Luettu 08.02.2024.
