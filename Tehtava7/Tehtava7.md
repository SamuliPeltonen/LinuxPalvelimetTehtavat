# Tehtävä 7

Tein vuoden 2019 laboratiorioharjoituksen, linkki siihen tässä: http://terokarvinen.com/2019/arvioitava-laboratorioharjoitus-linux-palvelimet-ict4tn021-3004-ti-alkukevat-2019-5-op/

Tehtävä vaikutti aluksi vaikeustasoltaan sopivalta, mutta monien mutkien ja haasteiden jälkeen teki mieli vaihtaa tehtävää, mutta se tuntui liian myöhäiseltä. Tein kaikki tehtävät, jotka vaikuttivat itselleni sopivilta vaikeustason puolesta. 

Asensin aivan ensimmäisenä puhtaan Debian 10.8:n.

Tämän jälkeen aloin asentamaan LAMP-stackiä. 
Apachen asennus hoitu klassisella `sudo apt-get -y install apache2` ja `sudo systemctl restart apache2`
Seuraavaksi asensin flaskin sekä psycopg2:n komennolla `sudo apt-get -y install python3-flask-sqlalchemy python3-psycopg2`
Tein LAMP-sovelluksen kuten viime viikolla ja noudatin omia kotitehtäväohjeitani, ongelmia ei tullut vastaan, joten en koe tarpeelliseksi mainita sen tekemisestä.¨
Tässä vielä linkki viimeviikkoiseen tehtävään:
https://github.com/SamuliPeltonen/LinuxPalvelimetTehtavat/blob/main/Tehtava6/tehtava6.md


Maijalle käyttäjän tekeminen onnistuu komennolla `sudo adduser maija`

Seuraavaksi vaihdan oletussivun pois apache2 sivusta komennolla `echo "testi"|sudo tee /var/www/html/index.html`

Ohje wsgin käyttöönottoon löytyy täältä, sen olen kuitenkin tehnyt ja kommentoinut niin monessa tehtävässä, että en sitä koe tarpeelliseksi tehdä nyt. 
https://terokarvinen.com/2020/deploy-python-flask-to-production/


Tässä linkki viikon 5 tehtävään, jonka avulla tein nytkin: 
https://github.com/SamuliPeltonen/LinuxPalvelimetTehtavat/blob/main/Tehtava5/tehtava5.md

![Kuvakaappaus verkkosivusta selaimessa](./1.png)



`goodmorning.sh` skriptin tekeminen onnistuu komennolla `nano goodmorning`. Sisällöksi tiedostoon laitan: 
```
#!/bin/bash
echo "hyvää huomenta"
hostname -I
date

```
Jotta kaikki saavat suorittaa skriptin, annan oikeudet `chmod a+x goodmorning`, jonka jälkeen kopioin sen kaikille käytettäväksi: `sudo cp goodmorning /usr/local/bin`, jonka jälkeen sitä voi käyttää kaikki käyttäjät, kaikista hakemistoista. 


Maijan hakemistoon helloworld.pyn lisääminen tapahtuu komennolla `sudo nano /home/maija/helloworld.py`, johon sisällöksi `print("hello world")`. 
