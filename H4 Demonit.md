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

Aloitin "Hei maailma" -tilan luomisen SaltStackilla tutustumalla ensin Saltin peruskonsepteihin. Ymmärsin, että tarvitsisin .sls-tiedoston, joka toimisi ohjeistuksena Salt-minioneille suoritettavista toimenpiteistä. Prosessin ensimmäisenä askeleena loin tarvittavan hakemiston Saltin tilatiedostoille komennolla:

![image](https://github.com/vilikaihola/Palvelinten-hallinta/assets/148875596/247215a8-2db3-4a13-87c5-86f9a1f1f809)

Tämän jälkeen siirryin luomaan itse .sls-tiedoston, joka sisältäisi "Hei maailma" -toiminnallisuuden.

![image](https://github.com/vilikaihola/Palvelinten-hallinta/assets/148875596/71a16466-7f30-40ca-8a06-277b168a9270)

kirjoitin tiedostoon seuraavan sisällön:

![image](https://github.com/vilikaihola/Palvelinten-hallinta/assets/148875596/b011f0e7-d714-4cc5-accb-6ae37c31bce0)

Tässä tapauksessa en käyttänyt Salt Master -minion -arkkitehtuuria tehtävän suorittamiseen. Tämä johtui siitä, että tavoitteeni oli yksinkertaisesti demonstroida Saltin perusominaisuuksia yksittäisessä ympäristössä ilman tarvetta konfiguroida monimutkaisempaa Salt Master -minion -asetusta. Lisäksi halusin välttää mahdolliset verkko- tai konfiguraatioon liittyvät ongelmat, jotka voivat ilmetä käytettäessä monimutkaisempaa infrastruktuuria. Tämä yksinkertaistettu lähestymistapa mahdollisti sen, että voisin keskittyä oppimaan Saltin syntaksia ja toimintalogiikkaa ilman ylimääräisiä häiriötekijöitä.

Lopputulos oli onnistunut; tila toimi odotetusti ja sain välittömän palautteen Saltin käyttöliittymästä, mikä vahvisti, että "Hei maailma" -viesti oli tulostettu onnistuneesti. Näin ollen sain kokea Saltin tehokkuuden ja helppokäyttöisyyden automaation alustana.

![image](https://github.com/vilikaihola/Palvelinten-hallinta/assets/148875596/07351afe-20d4-4bc1-98d3-a285fd35a5f3)

### b) Top. Tee top.sls niin, että tilat ajetaan automaattisesti, esim komennolla "sudo salt '*' state.apply".

![image](https://github.com/vilikaihola/Palvelinten-hallinta/assets/148875596/5edeec15-c14e-4022-988a-9bf29fcd841d)


![image](https://github.com/vilikaihola/Palvelinten-hallinta/assets/148875596/85b643fd-3eb1-4bfb-82f6-f78218e6121d)

