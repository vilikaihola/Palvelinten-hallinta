### Oma moduuli
SaltStack Automaation ja Hallinnan Moduuli


###### Johdanto

Tämä projekti keskittyy kehittämään SaltStack-pohjaista moduulia, jonka tarkoituksena on tehostaa ja yksinkertaistaa IT-infrastruktuurin hallintaa. Projektissa luodaan ratkaisu, joka automatisoi perustason toimintoja, kuten ohjelmistojen asennukset, käyttäjähallinnan ja järjestelmän seurannan, käyttäen yksinkertaista infrastruktuuria, jossa on yksi master ja kaksi slavea.

Tämän moduulin tavoitteena on parantaa järjestelmän tehokkuutta ja vakautta, samalla tarjoten joustavuutta ja laajennettavuutta. Projekti dokumentoi kehitysprosessin, haasteet ja ratkaisut, tarjoten käsityksen SaltStackin monipuolisista käyttömahdollisuuksista infrastruktuurin hallinnassa.

#### 1. Ympäristön Tarkistus ja Valmistelu
Ihan ensimmäiseksi ajoin omalla raudallani vagrant destroy käskyn, ja sitten alustin masterin ja 2 orjaa uudelleen. Noudatin tässä jo h2:ssa käytettyjä ohjeita.

#### 2. Ohjelmistojen Hallintamoduulin Perustaminen

Luodaan yksinkertainen Salt State, joka asentaa htop-ohjelmiston. pkg.installed on Saltin sisäänrakennettu toiminto, joka varmistaa, että määritellyt paketit ovat asennettuja. Tämä toimii sekä Debian- että Red Hat -pohjaisissa järjestelmissä.

![image](https://github.com/vilikaihola/Palvelinten-hallinta/assets/148875596/090cb428-cf89-4e85-a1a1-8cb7f6b319ae)

init.sls tiedoston sisältö:

![image](https://github.com/vilikaihola/Palvelinten-hallinta/assets/148875596/8083f615-1fa6-42d0-85db-5a5e0c6e9c83)

#### 3. Ohjelmiston asennuksen testaus
Testattiin luodun Salt Staten toimivuutta asentamalla htop ohjelmisto Salt Minioneille t001 ja t002. Tämä tehtiin suorittamalla komento sudo salt 't00*' state.apply software Salt Masterilla tmaste. Komento pyysi Salt Masteria soveltamaan software-nimistä tilaa kaikille Minioneille, joiden nimet alkavat t00. Tämän suorituksen tarkoituksena oli varmistaa, että htop asennettiin oikein jokaiseen määritettyyn Minioniin. Komennon suoritus tarjosi palautteen asennuksen onnistumisesta tai mahdollisista virheistä, antaen näin tietoa Salt Staten toiminnasta käytännössä.

![image](https://github.com/vilikaihola/Palvelinten-hallinta/assets/148875596/d186c368-100a-4894-8d6c-779bb05a3c2c

#### 4. 

Tässä vaiheessa ensin luotiin uusi hakemisto /srv/salt/users Salt Master -koneella tmaster. Tämän jälkeen luotiin uusi Salt State -tiedosto nimeltä init.sls tässä hakemistossa. Tiedostoon kirjoitettiin konfiguraatio, joka määritteli uuden käyttäjätunnuksen luomisen Minioneille t001 ja t002. Konfiguraatio sisälsi käyttäjänimen, täydellisen nimen ja käytettävän shellin määrittelyn. Tämä toimi osana projektin tavoitetta automatisoida ja yhtenäistää käyttäjähallinta koko Salt-ympäristössä.

![image](https://github.com/vilikaihola/Palvelinten-hallinta/assets/148875596/4229bdd4-50e1-4abb-a6f5-7176e93929a6)

init.sls tiedoston sisältö: 

![image](https://github.com/vilikaihola/Palvelinten-hallinta/assets/148875596/38d64387-9782-4d8e-89bf-21ef405a022f)

Tässä vaiheessa käytettiin komentoa sudo salt 't00*' state.apply users testataksemme, että aiemmin luodussa /srv/salt/users/init.sls-tiedostossa määritelty käyttäjätunnuksen luomiskonfiguraatio toimi oikein Minioneilla t001 ja t002. Tämä prosessi varmisti, että uusi käyttäjätunnus, kuten exampleuser, luotiin onnistuneesti molemmille Minioneille tai, jos tunnus oli jo olemassa, että sen tiedot olivat oikein. Tässä päätavoitteena oli varmistaa käyttäjähallintamoduulin toimivuus ja sen kyky hallita käyttäjätunnuksia keskitetysti koko Salt-ympäristössä.

![image](https://github.com/vilikaihola/Palvelinten-hallinta/assets/148875596/a0455913-2f3c-4512-a2ee-554a86e52d09)

#### 5. 
Keskityin nyt järjestelmän seurantaskriptien luomiseen ja testaamiseen SaltStackin avulla. Tässä vaiheessa ensin luotiin uusia Salt States -tiedostoja Salt Master -koneella tmaster hakemistossa /srv/salt/. Nämä tiedostot sisälsivät skriptejä järjestelmän muistin ja levytilan käytön seurantaan.

Konkreettisesti luotiin kaksi tiedostoa: monitorointi.sls muistin käytön tarkasteluun ja kovalevynmuisti.sls levytilan käytön seurantaan. Nämä tiedostot sisälsivät Salt States -konfiguraatioita, jotka suorittivat järjestelmäkomentoja (free -m muistille ja df -h levytilalle) Minioneilla t001 ja t002.

Tässä .sls tiedostojen sisällöt:





![image](https://github.com/vilikaihola/Palvelinten-hallinta/assets/148875596/3dc919ea-53a0-48b1-88c7-f63bd2e6eec4)  ![image](https://github.com/vilikaihola/Palvelinten-hallinta/assets/148875596/e1a0ccc3-a6a1-42aa-814e-71793ea20303)





Kun konfiguraatiot oli kirjoitettu, testasit niiden toimivuuden suorittamalla ne tmaste-koneelta käyttäen Saltin state.apply-komentoa. Tämä komento käynnisti seurantaskriptit Minioneilla, ja sen jälkeen tarkastelit tulosteita varmistaaksesi, että sait tarvittavat tiedot muistin ja levytilan käytöstä kultakin Minionilta.



![image](https://github.com/vilikaihola/Palvelinten-hallinta/assets/148875596/d3fb7bdc-434c-4c50-b780-920aa5850e8a)



![image](https://github.com/vilikaihola/Palvelinten-hallinta/assets/148875596/364b4873-1f27-4a18-8279-e74464873530)


#### 7. 

Tulen nyt automatisoimaan seurantaskriptien säännöllisen suorittamisen ja mahdollisesti asettamaan hälytyksiä tietyistä tapahtumista. Tässä vaiheessa käytän SaltStackin ajastus- ja hälytysominaisuuksia.

lisäsin seuraavan skriptin masterin konfiguraatio tiedostoon:


![image](https://github.com/vilikaihola/Palvelinten-hallinta/assets/148875596/4b80089a-8694-4029-b8db-88ce3fc46ac1)



![image](https://github.com/vilikaihola/Palvelinten-hallinta/assets/148875596/9903f994-5bca-4ae0-a982-ed1e66dc6944)




