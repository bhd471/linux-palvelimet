
## Tiivistelmä

## Djangon tuotantotyyppinen asennus

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

![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/145d9c49-74e8-4809-b3ce-cf2c4275a43d)
![image](https://github.com/bhd471/linux-palvelimet/assets/148760837/527bf25a-5981-4834-b07e-470b12e0847f)

- Asennetaan VirtuelEnv `sudo apt-get -y install virtualenv`
- Siirryn kansioon `cd publicwsgi/`
- Luon uuden virtuaaliympäristön `virtualenv -p python3 --system-site-packages env`

### Asennetaan Django virtuaaliympäristöön

- Aktivoidaan virtuaaliympäristö `source env/bin/activate`


### Lähdeluettelo

