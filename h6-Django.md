
## Tiivistelmä

## Ohjelma Djangolla

- Aloitan uuden projektin `django-admin startproject janiikki`
- Siirryn kansioon `cd janiikki`
- Käynnistän palvelimen ja lisään muistutuksen siitä, ettei testipalvelinta julkaista verkkoon `./manage.py runserver # development server, don't expose to the internet`
- Siirryn osoitteeseen http://127.0.0.1:8000/

![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/dc83f702-a57d-4834-bc39-004425f76c78)

### Admin

- Päivitetään tietokannat `./manage.py makemigrations` `./manage.py migrate`
- Lisätään käyttäjä, asennetaan pwgen-ohjelma ja generoidaan satunnainen salasana `sudo apt-get install pwgen` `pwgen -s 20 1 # randomize a password`
- `./manage.py createsuperuser`
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

