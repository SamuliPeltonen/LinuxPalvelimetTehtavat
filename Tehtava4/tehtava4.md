# a)
Tein palvelimen Digital Oceanissa. Valitsin käyttöjärjestelmäksi Debian 10:n ja laitoin salasanakirjautumisen sijasta SSH-avainkirjautumisen.
SSH-avaimen sain ajamalla komennon `ssh-keygen`, jonka jälkeen annoin vahvan passphrasen. Tämän jälkeen annoin palvelimelle kyseisen avaimen, jonka jälkeen palvelimen alustus on valmis.  
Otin SSH-yhteyden palvelimeen komennolla `ssh root@ip-osoite`, jonka jälkeen annan SSH-passphraseni. 
Ajan seuraavat komennot: 
`sudo apt-get update`, joka päivittää saatavilla olevat paketit.
`sudo apt-get upgrade`, joka päivittää kaikki asennetut paketit uusimpiin versioihinsa.
`sudo apt-get install ufw`, joka asentaa palomuurin
`sudo ufw allow 22/tcp`, jolla teemme reiän palomuuriin
`sudo ufw enable`, joka laittaa palomuurin päälle. 

Tämän jälkeen teen uuden käyttäjän, jolle kirjaudumme tulevaisuudessa rootin sulkemisen jälkeen. 
`sudo adduser samuli`, jonka jälkeen annamme vahvan salasanan käyttäjälle, jonka jälkeen lisäämme käyttäjälle sudo-oikeudet komennolla `sudo adduser samuli sudo`. 
Tämän jälkeen joudumme vaihtamaan väliaikaisesti asetuksia, jotta pääsemme kirjautumaan SSH-avaimella käyttäjälle sisään. 
Ajan komennon `sudo nano /etc/ssh/sshd_config`, jolla pääsemme muokkaamaan ssh-asetuksia. 
Vaihdamme `PasswordAuthentication no` arvon `PasswordAuthentication yes`, jonka jälkeen kokeilen kirjautua palvelimelle uudella käyttäjällä komennolla `ssh samuli@ip-osoite`. Tämä toimii, jonka jälkeen otamme tällekin käyttäjälle SSH-avaimen käyttöön ajamalla komennon ` ssh-copy-id samuli@ip-osoite` lokaalista tietokoneesta(huom. ei ssh:n läpi). Tämän jälkeen vaihdan sshd-configista takaisin `PasswordAuthentication no`, jonka jälkeen kokeilen avata uuden terminaali-ikkunan ja kirjautua uudella käyttäjällä. Nyt minulta pyydetään SSH-avaimen passphrasea, jonka oikein kirjoittamisen jälkeen pystyn kirjautumaan palvelimelleni SSH-avaimen avulla uudella käyttäjälläni. 

Seuraavaksi poistamme rootin käytöstä, jolloin palvelimelle voi kirjautua ainoastaan uudella tunnuksellani. 
Uudelta käyttäjältä ajamme komennot `sudo usermod --lock root`, joka lukitsee rootin salasanan 
Tämän jälkeen menemme taas sshd_config-tiedostoon, josta vaihdamme `PermitRootLogin no`, jonka jälkeen käynnistämme SSH:n uudelleen komennolla `sudo service ssh restart`. Tämän jälkeen, jos yritämme kirjautua rootille komennolla `ssh root@ip-osoite`, emme pääse kirjautumaan. 

Nyt asennamme Apache2:n komennolla `sudo apt-get install apache2`
Laitamme käyttäjien kotisivut päälle komennlla `sudo a2enmod userdir` ja käynnistämme apachen uudelleen komennolla `sudo systemctl restart apache2` Teemme myös reiän palomuuriin komennolla `ufw allow 80/tcp` ja käynnistämme palomuurin uudelleen komennolla `sudo ufw enable`
Nyt palvelimen ip-osoitteessa näkyy Apachen Default Page, loistojuttu. 

Nyt teemme dot.tk domain-nimen itsellemme. Käytämme tähän dot.tk:ta. Rekisteröin palvelimen meitsintestipalvelin.tk, asetukista valitsin DNS:n, johon asetin IP-osoitteeksi palvelimeni IP-osoitteen.
Rekisteröimisen jälkeen kokeilen avata selaimessa osoitetta [meitsintestipalvelin.tk](meitsintestipalvelin.tk), joka aukeaa Apachen default-sivulle. 

Wau, nyt palvelimella on oma DNS-nimi, josta pääsemme etusivulle. Tästä onkin viime viikon tehtävien tapaan helppo jatkaa eteenpäin ja vaihtaa oletussivu!