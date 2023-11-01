## H2 Karjaa 

### x) Lue ja tiivistä. (Tässä x-alakohdassa ei tarvitse tehdä testejä tietokoneella, vain lukeminen tai kuunteleminen ja tiivistelmä riittää. Tiivistämiseen riittää muutama ranskalainen viiva.)

#### 1. Slater 2017: What is the definition of "cattle not pets"?. 
- "Cattle, not pets" -terminologia vertaa palvelimien hallintaa lemmikkieläimiin ja karjaan.
- Lemmikit (Pets): Yksilöllisiä palvelimia, joita hoidetaan manuaalisesti ja jotka ovat korvaamattomia.
- Karja (Cattle): Useita palvelimia, jotka on rakennettu automatisoiduilla työkaluilla, ja suunniteltu toimimaan vikaantumisen sattuessa ilman ihmisen väliintuloa.
- Tavoitteena on siirtyä ainutlaatuisten "lemmikki" palvelimien käytöstä automatisoituun "karja" malliin, joka parantaa järjestelmän joustavuutta ja vikasietoisuutta.
- Esimerkkejä "karja"-mallista ovat web-palvelinryhmät, monimaster-tietovarastot ja kaikki kuormantasapainotetut, monimaster-ratkaisut.

#### 2. Karvinen 2017: Vagrant Revisited – Install & Boot New Virtual Machine in 31 seconds.
- Vagrant automatisoi uuden virtuaalikoneen asennuksen, joka on käytettävissä puolessa minuutissa ssh-yhteyden kautta.
- Asennusprosessi sisältää Vagrantin ja VirtualBoxin asentamisen, uuden virtuaalikoneen alustamisen ja käynnistämisen.
- Komento 'vagrant destroy' tuhoaa vieraan virtuaalikoneen ja kaikki sen tiedostot.

#### 3. Karvinen 2023: Salt Vagrant - automatically provision one master and two slaves.
- Artikkeli opastaa, kuinka käyttää Vagrantia ja Saltia kolmen virtuaalikoneen verkon luomiseen ja hallintaan.
- Virtuaalikoneiden asennus ja konfigurointi tehdään automaattisesti Vagrantfile-tiedoston määrittelemien asetusten mukaan.
- Vagrantin ja Salin avulla voidaan hallita virtuaalikoneita, asentaa ohjelmistoja, käynnistää/pysäyttää palveluita, hallita käyttäjiä ja toteuttaa "Infra as Code" -periaatetta.
- Virtuaalikoneet voidaan myös poistaa helposti komennolla 'vagrant destroy', mikä tukee "cattle, not pets" -periaatetta infrastruktuurin hallinnassa.

### a) ja b) Asenna Vagrant. Asenna yksi kone Vagrantilla, ota siihen SSH-yhteys, osoita että netti toimii.
![image](https://github.com/vilikaihola/Palvelinten-hallinta/assets/148875596/cc00c6e2-27dc-45fd-b87b-94f687933478)
![image](https://github.com/vilikaihola/Palvelinten-hallinta/assets/148875596/31cde458-9eb4-488a-aa15-fc4cb941702c)
![image](https://github.com/vilikaihola/Palvelinten-hallinta/assets/148875596/1ee617a9-ca95-42b7-aa48-d9215e0d8c79)

### c) Oma orjansa. Asenna Salt herra ja orja samalle koneelle.

![image](https://github.com/vilikaihola/Palvelinten-hallinta/assets/148875596/e33a31e6-edd4-4e44-8f81-12dc609e6e88)

### d) Asenna Saltin herra-orja arkkitehtuuri toimimaan verkon yli.

  Aloitin hyväksymällä avaimet tmaster herralla
  
  ![image](https://github.com/vilikaihola/Palvelinten-hallinta/assets/148875596/e9af9842-26b4-453d-919a-1c2e70fa5dcb)

Tämän jälkeen  käytin komentoa: $ sudo salt '*' test.ping testatakseni yhteyden koneiden välillä. 

![image](https://github.com/vilikaihola/Palvelinten-hallinta/assets/148875596/25d8b90b-be60-4347-852d-b4bb74667a83)

### e) Aja useita idempotentteja (state.single) komentoja verkon yli.

Ajoin ensin komennon:
    
    $ sudo salt --state-output=terse '*' state.single file.managed '/tmp/see-you-at-terokarvinen-com' 

![image](https://github.com/vilikaihola/Palvelinten-hallinta/assets/148875596/33a866ed-ba71-462b-88fe-0a29d58a4461)

Asensin softan Apache2. Yritin asentaa kokeilumielessä myös muita sovelluksia, kuten nethack ja ngix, mutta tämä ei jostain syystä onnistunut.
![image](https://github.com/vilikaihola/Palvelinten-hallinta/assets/148875596/8ea0b3a0-0c33-4c0b-a1d7-65947413c6ed)

Tämän jälkeen varmistin että daemon toimii kaikilla koneilla:
![image](https://github.com/vilikaihola/Palvelinten-hallinta/assets/148875596/aba43c2a-2253-4592-84ee-da716dc04131)

Jonka jälkeen asensin curlin ja varmistin, että se todella toimii:
![image](https://github.com/vilikaihola/Palvelinten-hallinta/assets/148875596/8ed68114-2298-499f-9108-53de297fd0c2)

 Lopuksi sammutin apache2:n antamalla komentoriville käskyn  sudo salt '*' state.single service.dead apache2. Alla olevassa kuvassa ilmenee mitä tein varmistaakseni apachen olevan pois päältä.
![image](https://github.com/vilikaihola/Palvelinten-hallinta/assets/148875596/954b7d66-0423-467d-b9a4-23973c7edd36)

Loput ohjeiden komennot käsittelivät käyttäjien hallintaa ja muokkaamista. nävä tapahtuivat käskyillä:

Käyttäjien hallinta onnistuu käskyllä.

    $ sudo salt '*' state.single user.present terote01

Muokkaaminen puolestaan käskyllä

    $ sudo salt '*' state.single user.present terote01 shell="/bin/bash"

Tällä käskyllä puolestaan varmistettiin ettei käyttäjiä enään ole:

    $ sudo salt '*' state.single user.present terote01 shell="/bin/bash"

En kokenut tarpeelliseksi suorittaa viimeistä komentoa, sillä yllolevat ajoivat asiansa varsin mainiosti.

### f) Kerää teknistä tietoa orjista verkon yli (grains.item)

Ensimmäiseksi kokeilin käskyä, joka ilmeisesti listasi aivan kaiken, mitä tmastein järjestelmässä oli: 

    $ sudo salt '*' grains.items

Seuraavaksi kokeilin ohjeiden mukaisesti komentoa, jolla saa tietoa orjakoneiden verkkoasetuksista.

![image](https://github.com/vilikaihola/Palvelinten-hallinta/assets/148875596/d010829b-d4b4-4745-b25a-d9c4d294c170)

### g)  Aja shell-komento orjalla verkon yli.

Kokeilin muutamia komentoja verkon yli orjalla, mutta esimerkki komentona päätin käyttää shell- komentoa, joka näytti järjestelmän uptimen:

![image](https://github.com/vilikaihola/Palvelinten-hallinta/assets/148875596/ae3263f2-2c6f-4cb7-8624-c4d1bc8bc5e5)

### h) Hello, IaC. Tee infraa koodina kirjoittamalla /srv/salt/hello/init.sls. Aja tila jollekin orjalle. Tila voi esimerkiksi tehdä esimerkkitiedoston johonkin hakemistoon. Testaa toisella komennolla, että pyytämäsi muutos on todella tehty.

Käytin SaltStackia infrastruktuurin automatisointiin, määrittäen tilan, joka varmistaa /tmp/infra-as-code -tiedoston olemassaolon kaikissa minioneissa. Aloittaessamme luomisen, määrittelimme tilan /srv/salt/hello/init.sls ja määritimme sen soveltuvan kaikkiin minioneihin top.sls-tiedostossa. Ensimmäinen yritys soveltaa tilaa epäonnistui vahingossa keskeytetyllä komennolla, mutta korjasimme ongelman ja saimme tilan onnistuneesti sovelletuksi. Tämä kokemus opetti meille SaltStackin perusteet ja sen tehokkuuden infrastruktuurin hallinnassa. Tämä osio sujui ongelmitta, mutta huomasin että ohjeissa on käskyssä $ sudo salt '*' state.apply hello^C. ^C ei siis kuulu käskyyn.
En oikein saanut kiinni tässä osiossa, että mitä käskyjen outputeilla oli eroa. Tarkoitan siis käskyjä:

    $ sudo salt '*' state.apply hello

    $ sudo salt '*' state.apply


##### Lopuksi poistin tekemäni herra-orja infrastruktuurin käyttämällä komentoja:

    $ exit

    $ vagrant destroy
