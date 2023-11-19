## H4 Demonit

### x)  Lue ja tiivistä. (Tässä x-alakohdassa ei tarvitse tehdä testejä tietokoneella, vain lukeminen tai kuunteleminen ja tiivistelmä riittää. Tiivistämiseen riittää muutama ranskalainen viiva.)

#### 1) Karvisen (2023) Salt Vagrant -ohjeistossa "Infra as Code - Your wishes as a text file" ja "top.sls - What Slave Runs What States" kohdat tiivistetysti:

- Infra as Code: : Mahdollistaa infrastruktuurin määrittelyn ja hallinnan tekstitiedostojen avulla.

- top.sls Määrittely: Tiedosto, joka määrittää, mitä tiloja (states) ajetaan milläkin orjalla (slave).

- Käytä Saltia Ilman Moduulien Nimeämistä: sudo salt '*' state.apply suorittaa tilat ilman, että moduuleja tarvitsee nimetä erikseen.

- Luo hakemisto: sudo mkdir -p /srv/salt/hello.

- Luo init.sls tiedosto hello-moduulille ja kirjoita siihen YAML-syntaksilla. Huomioi kaksi välilyöntiä sisennyksessä, ei tabulaattoreita.

- Määritä Tiedostonhallinta init.sls-tiedostossa: Esimerkissä luodaan /tmp/infra-as-code tiedosto file.managed-määrittelyn avulla.

- Sovella hello-tilaa Saltilla: sudo salt '*' state.apply hello komento soveltaa hello-tilaa kaikkiin Saltin hallinnoimiin koneisiin.

#### 2) Salt contributors: Salt overview, kohdat Rules of YAML, YAML simple structure, Lists and dictionaries - YAML block structures:

###### YAML:n Säännöt

- Perusrakenne: YAML tiedostoissa käytetään avain: arvo -pareja.

- Merkintätapa: Avain: arvo -parit erotetaan kaksoispisteellä ja yhdellä välilyönnillä (“: ”).

- Avainten Arvot: Voivat olla useissa eri rakenteissa, kaikki avaimet ovat kirjainkoosta riippuvaisia.

- Välilyönnit, Ei Tabulaattoreita: Käytä ainoastaan välilyöntejä, tabulaattorit eivät ole sallittuja.

- Kommentit: Alkavat risuaidalla “#”.
 
###### YAML:n Yksinkertainen Rakenne

- Skalaarit: Avain: arvo -parit, joissa arvo voi olla numero, merkkijono tai totuusarvo.

- Listat: Avain seuraa listaa arvoista, jossa jokainen arvo on omalla rivillään, edeltäen kahta välilyöntiä ja väliviivaa.

- Sanakirjat: Kokoelma avain: arvo -pareja ja listoja.

###### YAML:n Listat ja Sanakirjat - Lohkorakenteet

- Lohkorakenne: YAML järjestetään lohkorakenteisiin, sisennyksellä määritellään konteksti.

- Sisennys: Käytä yhtä tai useampaa välilyöntiä sisennykseen, standardina kaksi välilyöntiä.

- Kokoelmat: Listat tai sanakirjablokkijonot, joissa jokainen merkintä alkaa väliviivalla ja välilyönnillä (“- ”).

#### 3) Salt contributors: Salt states

###### State Moduulit

- Moduuli.Funktio: State moduulit kutsuvat vastaavia suoritusmoduuleita ja lisäävät tai rajoittavat niiden vaihtoehtoja valtiollisia operaatioita varten.

- Mahdolliset Ristiriidat: Eroja state moduulien ja suoritusmoduulien välillä, esim. state moduulit eivät tue tilan tarkistuksia.

###### State SLS Tietorakenne

- Osat: Jokaisessa state-määrittelyssä on tunnistin, state-moduulin nimi, kutsuttava funktio, tilan nimi ja argumentit.

- Rekvisiitat ja Julistukset: Tärkeitä state-määrittelyissä, käsitellään erikseen.
###### top.sls-tiedosto

- Käyttö: Skalautuvuutta varten, mapataan Salt statet oikeille minionille.

- Rakenne: Määrittelee, mitkä nodet vetävät mitäkin ympäristöistä ja mitkä statet ajetaan näissä ympäristöissä.

- Esimerkki: Yksinkertainen mutta joustava rakenne, jossa määritellään ympäristöt, kohdennusparametrit ja käytettävät state-tiedostot.

###### SSH ja Apache Staten Luonti

- SSH State: Asenna OpenSSH, hallinnoi SSH:n konfiguraatiotiedostoja ja varmista, että SSH-palvelu on käynnissä.
- Apache State: Asenna HTTPD (Apache), hallinnoi Apache-konfiguraatiota ja varmista, että HTTPD-palvelu on käynnissä.

###### Teron Huomiot ja Suositukset
service.watch Puuttuminen: Jos asetustiedosto päivittyy masterilla, se ei välttämättä tule automaattisesti käyttöön minioneilla ilman service.watch-määrittelyä, joka varmistaisi palvelun uudelleenkäynnistyksen konfiguraation päivityksen jälkeen.

#### 4) Karvinen 2018: Pkg-File-Service – Control Daemons with Salt – Change SSH Server Port

##### SSH Palvelimen Portin Muuttaminen Saltilla

- Paketti-Tiedosto-Palvelu: Yleinen malli daemonien hallintaan konfiguraationhallintajärjestelmillä. Prosessi sisältää ohjelmiston asentamisen, konfiguraatiotiedoston korvaamisen ja daemonin uudelleenkäynnistyksen uuden konfiguraation käyttämiseksi.

- SSH Staten Luonti: State Tiedosto (sshd.sls): Määrittää openssh-server-paketin asennuksen, hallinnoi /etc/ssh/sshd_config tiedostoa ja varmistaa, että sshd-palvelu on käynnissä ja seuraa sshd_config-tiedoston muutoksia.

- Konfiguraatiotiedosto (sshd_config): Esimerkkitiedosto, jossa vain kommentit poistettu ja porttinumero muutettu (Port 8888).

- Staten Soveltaminen Orjille: Käytä komentoa sudo salt '*' state.apply sshd soveltaaksesi staten Saltin orjille.

- Testaus: Testaa yhteyttä muutettuun porttiin (esim. 8888) käyttäen nc-komentoa tai SSH-yhteyttä määritellyllä portilla.

### a) Hello SLS! Tee Hei maailma -tila kirjoittamalla se tekstitiedostoon, esim /srv/salt/hello/init.sls.

Aloitin luomalla tarvittavan hakemiston Saltin tilatiedostoille. Seuraavaksi siirryin luomaan itse tilatiedoston. Avattuani init.sls-tiedoston komennolla: sudoedit /srv/salt/hello/init.sls.


![image](https://github.com/vilikaihola/Palvelinten-hallinta/assets/148875596/af9318ed-83e3-4e5a-aa56-21c4aeb6108a)

Kirjoitin tiedostoon seuraavan tilamäärittelyn: 

 hello_world:
  cmd.run:
    - name: echo "Hei maailma!"


![image](https://github.com/vilikaihola/Palvelinten-hallinta/assets/148875596/2061dc39-d10b-4324-bc68-e253d5bdd097)

Valmisteltuani masterin ja varmistettuani, että minionit T001 ja T002 olivat verkossa ja odottivat komentoja, suoritin seuraavan komennon tilan levittämiseksi ja suorittamiseksi kohdeminioneilla: 

![image](https://github.com/vilikaihola/Palvelinten-hallinta/assets/148875596/6b16c164-ba57-459c-9661-c44765d33dbc)

### b) Top. Tee top.sls niin, että tilat ajetaan automaattisesti, esim komennolla "sudo salt '*' state.apply".

Hakemiston ja Tiedoston Valmistelu:

Varmistin, että hakemisto /srv/salt oli olemassa master-koneella.
Avattuani tekstieditorin, loin tiedoston nimeltä top.sls polkuun /srv/salt/ seuraavalla komennolla:

![image](https://github.com/vilikaihola/Palvelinten-hallinta/assets/148875596/5d9a75e3-1ad7-4014-9f39-6a19607be1c9)

##### top.sls-tiedoston Sisällön Kirjoittaminen:

Kirjoitin top.sls-tiedostoon seuraavan sisällön, joka määrittelee kaikkien minioneiden, kuten T001 ja T002, suorittavan "hello" tilan:
base:
  '*':
    - hello

##### Tilojen Levitys:

Suoritin seuraavan komennon master-koneelta levittääkseni hello-tilan kaikille minioneille, mukaan lukien T001 ja T002: 

![image](https://github.com/vilikaihola/Palvelinten-hallinta/assets/148875596/643bf9cf-aab0-4ac7-97a6-9de27786c547)

### c) Apache. Asenna Apache, korvaa sen testisivu ja varmista, että demoni käynnistyy.
- Ensin käsin, vasta sitten automaattisesti.
- Kirjoita tila sls-tiedostoon.
- pkg-file-service
- Tässä ei tarvita service:ssä watch, koska index.html ei ole asetustiedosto


![image](https://github.com/vilikaihola/Palvelinten-hallinta/assets/148875596/00027fac-d874-413b-bbaa-48742ba13500)
![image](https://github.com/vilikaihola/Palvelinten-hallinta/assets/148875596/a5f9465c-e494-4194-bb09-56bdef7e01bd)
![image](https://github.com/vilikaihola/Palvelinten-hallinta/assets/148875596/1590cf12-9419-4fbd-a1da-8b4309bdf05d)
![image](https://github.com/vilikaihola/Palvelinten-hallinta/assets/148875596/2fdd028b-53d7-4abe-ba96-44aa953fa3fb)

