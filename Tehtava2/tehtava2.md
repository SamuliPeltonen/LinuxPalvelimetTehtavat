#a) 
Yritin asentaa Curlia sudona, mutta antaen sekä väärän salasanan että oikean. 
Tämä tuottaa logiin seuraavanlaisen tulosteen: 
```
Feb  2 16:15:50 ubuntuvirtual sudo:   samuli : TTY=pts/0 ; PWD=/home/samuli/Desktop/weatherapp/frontend ; USER=root ; COMMAND=/usr/bin/apt-get install curl
Feb  2 16:15:50 ubuntuvirtual sudo: pam_unix(sudo:session): session opened for user root by (uid=0)
Feb  2 16:15:51 ubuntuvirtual sudo: pam_unix(sudo:session): session closed for user root
Feb  2 16:16:08 ubuntuvirtual sudo: pam_unix(sudo:auth): Couldn't open /etc/securetty: No such file or directory
Feb  2 16:16:09 ubuntuvirtual sudo: pam_unix(sudo:auth): Couldn't open /etc/securetty: No such file or directory
Feb  2 16:16:09 ubuntuvirtual sudo: pam_unix(sudo:auth): authentication failure; logname= uid=1000 euid=0 tty=/dev/pts/0 ruser=samuli rhost=  user=samuli
Feb  2 16:16:10 ubuntuvirtual sudo: pam_unix(sudo:auth): Couldn't open /etc/securetty: No such file or directory
Feb  2 16:16:12 ubuntuvirtual sudo: pam_unix(sudo:auth): Couldn't open /etc/securetty: No such file or directory
Feb  2 16:16:12 ubuntuvirtual sudo:   samuli : TTY=pts/0 ; PWD=/home/samuli/Desktop ; USER=root ; COMMAND=/usr/bin/apt-get install curl
Feb  2 16:16:12 ubuntuvirtual sudo: pam_unix(sudo:session): session opened for user root by (uid=0)
Feb  2 16:16:12 ubuntuvirtual sudo: pam_unix(sudo:session): session closed for user root

```
Lokissa näkyy "Authentication failure", joka osoittaa, ettei sudon kirjautuminen mennyt läpi. Toiseksi viimeisellä rivillä puolestaan taas lukee: "Sessio opened for user root", joka tarkoittaa, että salasana meni läpi ja sessio root-käyttäjälle voitiin aloittaa.
 
#c) 
```
sudo apt-get install curl
```
asentaa curl-ohjelman, jolla voi komentorivin kautta mm. tarkastella verkkosivuja. Käytin tätä ohjelmaa Docker-containerien oikein lataamisen varmistamiseen. Onnistuneessa tilanteessa curl-tulosteessa näkyy <div>-elementti. 
Curl tuloste:
```
samuli@ubuntuvirtual:~/Desktop$ curl localhost:8000
<!doctype html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>What's the weather?</title>
    <link rel="stylesheet" type="text/css" href="/style.css">
  </head>
  <body>
    <div id="app"></div>
  <script src="/main.d145a6b8.js"></script></body>
</html>

```

#d)
Asensin Treen, joka on ohjelma, joka piirtää visuaalisen puun eri tiedostorakenteille. 
Tree asentui komennolla 
```
sudo apt-get install tree
```

Lisäksi asensin myös ncurses disk usage analyzerin, joka on ohjelma, jolla voit analysoida levyn käyttöäsi. 
Ohjelma asentuu komennolla
```
sudo apt-get install ncdu
```
Komento "ncdu" saa aikaan seuraavanlaisen näkymän, joka on tuoreen asennuksen vuoksi suhteellisen aneeminen. 
```
ncdu 1.14.1 ~ Use the arrow keys to navigate, press ? for help                  
--- /home/samuli/Desktop -------------------------------------------------------
  381,7 MiB [##########] /weatherapp                                            


```

Asensin Figletin, joka on ASCII-art-sovellus. 
Asentui komennolla
```
sudo apt install figlet toilet
```
Figletillä saa mm. tällaista aikaan: 
```
samuli@ubuntuvirtual:~/Desktop$ figlet -c Ubuntu
                       _   _ _                 _         
                      | | | | |__  _   _ _ __ | |_ _   _ 
                      | | | | '_ \| | | | '_ \| __| | | |
                      | |_| | |_) | |_| | | | | |_| |_| |
                       \___/|_.__/ \__,_|_| |_|\__|\__,_|
                                                         

```
