# H6 - DJ Ango
Tämän viikon kotitehtävässä tein tiivistelmän Tero Karvisen artikkeleista [Deploy Django 4 - Production Install](https://terokarvinen.com/2022/deploy-django/) (Karvinen, 2022) ja [Django 4 Instant Customer Database Tutorial](https://terokarvinen.com/2022/django-instant-crm-tutorial/) (Karvinen, 2022). Näitä artikkeleja seuraten tein esimerkkiohjelman Djangolla sekä Djangon tuotantotyyppisen asennuksen. 
## Tiivistelmä

## Ohjelma Djangolla

- Aloitan uuden projektin `django-admin startproject janiikki`
- Siirryn kansioon `cd janiikki`
- Käynnistän palvelimen ja lisään muistutuksen siitä, ettei testipalvelinta julkaista verkkoon `./manage.py runserver # development server, don't expose to the internet`
- Siirryn osoitteeseen http://127.0.0.1:8000/

![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/dc83f702-a57d-4834-bc39-004425f76c78)

### Admin

- Päivitetään tietokannat `./manage.py makemigrations` `./manage.py migrate`
- Asennetaan pwgen-ohjelma ja generoidaan satunnainen salasana `sudo apt-get install pwgen` `pwgen -s 20 1 # randomize a password`
- Luodaan käyttäjä `./manage.py createsuperuser`
- Käynnistän palvelimen `./manage.py runserver`, kokeilen toimivuutta selaimessa -> Toimii, pääsen kirjautumaan sisään

![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/c1468430-f094-4f37-bb24-ca8010f6c484)

### Customer Database

- Luodaan uusi hakemisto $ ./manage.py startapp crm
- Avataan micro-tiedosto `micro janiikki/settings.py`, lisätään INSTALLED_APPS-kohtaan alimmaiseksi 'crm'
  
![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/8b2df5d9-3aea-4258-89e7-ff32ac12aea7)

- Avataan micro-tiedosto `micro crm/models.py` ja lisätään malleja
  
![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/35c6c00e-6c58-4e56-b913-406b3f2e07cf)

- Päivitetään tietokannat `./manage.py makemigrations` `./manage.py migrate`
- Avataan micro-tiedosto `micro crm/admin.py`, rekisteröidään tietokanta

![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/3a5d0db9-c8e2-4fb2-9efd-1b3a88f2ce53)

- Käynnistetään palvelin `./manage.py runserver`
- Avataan sivu http://127.0.0.1:8000/admin/ ja kirjaudutaan sisään
- Lisätään vasemmasta reunasta Add-napista asiakkaita tietokantaan

![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/1efa3978-ad02-4b97-b008-11c4bd113925)

### Lisätään asiakkaiden nimet näkyviin 

- Avataan micro-editori `micro crm/models.py`
- Tehdään alapuolella näkyvät muutokset
 ![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/9e188549-3336-4f5e-92bf-7b02e77ec7b3)
- Käynnistetään palvelin `./manage.py runserver`

![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/86649538-db3b-4e66-9061-3b53504b8b9c)


## Djangon tuotantotyyppinen asennus

Asennukseen kului aikaa noin 45 minuuttia. 

- Aloitan päivittämällä paketit `sudo apt-get update`
- Luon uuden hakemiston `mkdir -p publicwsgi/teroco/static/`
- Lisään tekstiä sivulle `echo "Stay tuned"|tee publicwsgi/janika/static/index.html`
- Alan luomaan uutta VirtualHostia `sudoedit /etc/apache2/sites-available/janiikki.com.conf`

![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/55628ad9-2c98-41e5-96ba-e23b52afda3c)

- Laitan uuden sivuni päälle `sudo a2ensite janiikki.com.conf`
- Suljen vanhan sivun `sudo a2dissite hattu.example.com.conf`
- Tarkistan toimivuuden `/sbin/apache2ctl configtest`
- Koodi AH00558 ilmaantuu, tämä ok
- Käynnistetään apache uudelleen `sudo systemctl restart apache2`
- Tarkistetaan vielä, että localhost/static/ sivu näkyy oikein `curl http://localhost/static/`


![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/527bf25a-5981-4834-b07e-470b12e0847f)

- Asennetaan VirtuelEnv `sudo apt-get -y install virtualenv`
- Siirryn kansioon `cd publicwsgi/`
- Luon uuden virtuaaliympäristön `virtualenv -p python3 --system-site-packages env`

### Asennetaan Django virtuaaliympäristöön

- Aktivoidaan virtuaaliympäristö `source env/bin/activate`
- Tarkistetaan, että pip sijaitsee oikeassa hakemistossa `which pip`
- Luon uuden tekstitiedoston `micro requirements.txt`
- Kirjoitan tekstitiedostoon "django"
- Asennetaan `pip install -r requirements.txt`
- Testataan, asentuiko Django `django-admin --version`
- Asennus onnistui

  ![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/5d93320d-3854-426b-8507-3dbf7aefc9f5)




### Lähdeluettelo
Luettavissa: https://terokarvinen.com/2022/deploy-django/
Luettu 27.02.2024.

Luettavissa: https://terokarvinen.com/2022/django-instant-crm-tutorial/
Luettu 03.03.2024.
