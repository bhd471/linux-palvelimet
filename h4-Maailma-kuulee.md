## Tiivistelmä

### Teoriasta käytäntöön pilvipalvelimen avulla, Susanna Lehto

a) - Pilven vuokraaminen verkosta, oman julkisen palvelimen asentaminen verkkoon

d) - Reikä ssh-palvelimelle, jonka jälkeen palvelin suojataan tulimuurilla

e) - Luodaan Apache-webbipalvelimella kotisivut

f) - Päivitetään kaikki palvelimen ohjelmat

(Lehto, 14.02.2022.)

### First Steps on a New Virtual Private Server

- Verkkotunnukset ja yksityiset virtuaalipalvelimet ovat kovasti kilpailtuja

- Uuden serverin voi luoda esim. DigitalOcean nimisessä palvelussa

## a) Virtuaalipalvelimen vuokraaminen

Siirryin DigitalOceanin sivuille, johon kirjauduin Googlen tunnuksilla. Sivusto lupasi 200 dollarin edestä ilmaisia krediittejä 60 päivän ajaksi. Jouduin varmentamaan identiteettini syöttämällä luottokorttitietoni sivustolle. Tililtäni veloitettiin 5 dollaria, mutta tämä luvattiin palauttaa viikon kuluessa. Tämän jälkeen päivitin tiimini nimen omaksi nimekseni. 

Aloin luomaan uutta virtuaalipalvelinta kohdasta "Droplets". Sivun mukaan palvelimen ylläpitäminen maksaa alkaen 4 dollaria kuukaudessa. Valitsin uuden virtuaalikoneen maaksi Amsterdamin, ja käyttöjärjestelmäksi Debian 12.  Valitsin 'Shared CPU Basic' ja 'Regular CPU, Disk type SSD'. Seuraavaksi jouduin valitsemaan minkä kokoisen paketin tarvitsen. Päädyin toiseksi halvimpaan, jonka hinta oli 6 dollaria kuukaudessa, sisältäen 1 GB prosessori, 25 GB SSD-tilaa ja 1000 GB siirtodataa. Seuraavaksi pyydettiin valitsemaan kirjautuminen salasanalla tai SSH avaimella. Vielä tässä vaiheessa en tiedä oikeastaan mitään SSH-avaimista, joten valitsen salasanan. Salasanan luomisen jälkeen kysellään, haluanko lisäpalveluita, joista en ota mitään. Lopuksi valitsin, että tahdon luoda yhden koneen, jonka nimesin mauksi.

![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/be396f8c-1780-439f-8da4-ac58a64acdf4)


## b) Alkutoimet omalla palvelimella

Aloitan luomalla SSH-avaimet virtuaalikoneellani. Syötin komentoriville komennon ´ssh-keygen´. 
Seuraavaksi lähdin avaamaan omaa virtuaalikonettani, jonka komentoriville syötin komennon `ssh root@159.65.194.165`.

### Lähdeluettelo

Lehto, S. Teoriasta käytäntöön pilvipalvelimen avulla. 14.02.2022. Luettavissa: https://susannalehto.fi/2022/teoriasta-kaytantoon-pilvipalvelimen-avulla-h4/
Luettu: 06.02.2024.

Karvinen, T. First steps on a new virtual private server - an example on DigitalOcean and Ubuntu 16.04 LTS. 19.09.2017. Luettavissa: https://terokarvinen.com/2017/first-steps-on-a-new-virtual-private-server-an-example-on-digitalocean/
Luettu: 06.02.2024.
