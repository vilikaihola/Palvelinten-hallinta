# H3 Versio

### a) Online. Tee uusi varasto GitHubiin (tai Gitlabiin tai mihin vain vastaavaan palveluun). Varaston nimessä ja lyhyessä kuvauksessa tulee olla sana "winter". Aiemmin tehty varasto ei kelpaa. (Muista tehdä varastoon tiedostoja luomisvaiheessa, esim README.md ja GNU General Public License 3)

Loin uuden GitHub-varaston nimeltä "winteriscoming", joka täyttää annetut vaatimukset: varaston nimi ja kuvaus sisältävät sanan "winter". Varastoon lisäsin alustavat tiedostot, kuten README.md, joka antaa perustiedot projektista, ja GNU General Public License 3 -lisenssin, joka määrittelee ohjelmiston käyttöehdot.

### b) Dolly. Kloonaa edellisessä kohdassa tehty uusi varasto itsellesi, tee muutoksia, puske ne palvelimelle, ja näytä, että ne ilmestyvät weppiliittymään.

 Ajoin ensiksi komennon git clone https://github.com/vilikaihola/winteriscoming git versionhallintatyökalun terminaalissa, joka toimi mainiosti:

![image](https://github.com/vilikaihola/Palvelinten-hallinta/assets/148875596/f0bbd985-9400-4739-b5cf-ed091846a651)

#### 1. Muutosten Lisääminen (git add .):

Tämä komento lisää kaikki paikallisen hakemiston muutetut tiedostot Gitin seurantaan valmistellen niitä tallennettavaksi (commit). Piste (.) merkitsee, että kaikki muutokset nykyisessä hakemistossa lisätään, mukaan lukien uudet, muutetut ja poistetut tiedostot.
Tämä vaihe on välttämätön, koska Git ei automaattisesti ota huomioon kaikkia muutoksia, vaan sinun täytyy erikseen kertoa Gitille, mitkä muutokset haluat sisällyttää seuraavaan commitiin.

![image](https://github.com/vilikaihola/Palvelinten-hallinta/assets/148875596/826aeb11-c05b-4cc0-b696-f2644b69257c)


Seuraavassa kohdasssa kohtasin pienimuotoisen ongelman,joka johtui siitä että olin tehnyt muutoksia "winteriscoming" repositoryyn näiden askeleiden välissä. 

![image](https://github.com/vilikaihola/Palvelinten-hallinta/assets/148875596/3c682e4a-cdbf-4b76-993e-6f12c1ba3aff)

#### 2. Ongelma ratkesi ajamalla komennon git pull origin main, jonka jälkeen git push komento toimi toivotulla tavalla.

- Tämä komento lähettää äskettäin tekemäsi commitit paikallisesta repositorystä etärepositoryyn, kuten GitHubiin. Tämä on olennaista, jotta muutokset tulevat näkyviin GitHubissa ja jotta muut tiimin jäsenet tai yleisö pääsevät käsiksi näihin muutoksiin.

- Tämä vaihe on tärkeä, koska se varmistaa, että työsi on tallennettu ja saatavilla etäpalvelimella, mikä mahdollistaa yhteistyön ja varmuuskopioinnin.

![image](https://github.com/vilikaihola/Palvelinten-hallinta/assets/148875596/315c0110-9a66-4f21-9fdc-0cd51c739b8b)


#### 3. Commitointi (git commit -m "muutosten kuvaus"):

- Tämän komennon avulla tallennat aiemmin lisäämäsi muutokset paikalliseen repositoryyn. Commitointi on kuin ottaisit "valokuvan" nykyisestä projektisi tilasta, ja tämä "valokuva" sisältää kaikki git add-komennolla lisätyt muutokset.

- Parametri -m mahdollistaa viestin lisäämisen suoraan komentoriviltä, joka kuvaa commitin sisältöä. Tämä viesti on hyödyllinen, kun myöhemmin katsot läpi projektisi historian ja haluat ymmärtää, mitä muutoksia kussakin commitissa on tehty.

![image](https://github.com/vilikaihola/Palvelinten-hallinta/assets/148875596/cee20fbe-0132-4d4d-91bb-0cc4a0a376c3)

#### 4. Onnistunut lopputulos näyttti selaimessa vastaavalta:

![image](https://github.com/vilikaihola/Palvelinten-hallinta/assets/148875596/4dcbab20-c8eb-4d61-ae48-6b4574ed5a5e)


### SSH

![image](https://github.com/vilikaihola/Palvelinten-hallinta/assets/148875596/9ce7f1e8-aa59-4ae9-90b8-121636a1b57a)


![image](https://github.com/vilikaihola/Palvelinten-hallinta/assets/148875596/924375ca-686d-4a26-9020-47fe2a932430)


![image](https://github.com/vilikaihola/Palvelinten-hallinta/assets/148875596/833002be-64b1-4ed7-879d-cf5189fbdf2b)

![image](https://github.com/vilikaihola/Palvelinten-hallinta/assets/148875596/49fc7601-4244-4e9b-bae5-18879ebafce0)


![image](https://github.com/vilikaihola/Palvelinten-hallinta/assets/148875596/377daf72-2563-4776-a012-6c27841acec5)


Kokeilin vielä suorittaa tehtävän ensimmäiset askeleet SSH menetelmällä, tällä kertaa käyttäen winterfell nimistä varastoa. Tämä ei tuottanut vaikeuksia. Kuvittain alhaalta ylös toimin seuraavasti: Ensin loin avaimet, jonka jälkeen kävin lyömässä ne kopioinnin jälkeen githubiini. Tämän jälkeen turvallisinta olisi tarkistaa, että yhdistämäni palvelimen sormenjälki vastaa GitHubin julkaisemaa sormenjälkeä. Vastataan bashille "yes", ja sen jälkeen testattiin yhteys. Tämän jälkeen suoritin kloonauksen ssh:n kautta.

### c) Doh! Tee tyhmä muutos gittiin, älä tee commit:tia. Tuhoa huonot muutokset ‘git reset --hard’. Huomaa, että tässä toiminnossa ei ole peruutusnappia.

Kohdassa c käytin git reset --hard -komentoa Git-repositoriossani. Tämä komento peruutti kaikki paikalliset, vielä commitoimattomat muutokset ja palautti repositorioni viimeisimpään commitoitavaan tilaan. Toisin sanoen, kaikki tekemäni tiedostomuokkaukset, uudet tiedostot ja muut muutokset, joita en ollut vielä vahvistanut, hylättiin pysyvästi. Tämän komennon seurauksena repositorioni palasi "puhtaaseen" tilaan, joka vastaa viimeisintä tallennettua commitia. Tämä toimenpide oli peruuttamaton, ja kaikki poistetut muutokset ovat menetettyjä

![image](https://github.com/vilikaihola/Palvelinten-hallinta/assets/148875596/de43d0f6-2503-4640-8e64-50435aa497ed)

![image](https://github.com/vilikaihola/Palvelinten-hallinta/assets/148875596/0319e5d3-ddd3-48dc-b11a-4c99f64f5050)


### d) Tukki. Tarkastele ja selitä varastosi lokia. Tarkista, että nimesi ja sähköpostiosoitteesi näkyy haluamallasi tavalla ja korjaa tarvittaessa.

![image](https://github.com/vilikaihola/Palvelinten-hallinta/assets/148875596/a4f30b71-75f5-4b95-bc48-d3fd779df6bf)


Git-logissa winteriscoming-repositoriossa näkyy sarja commiteja, jotka olen tehnyt. Tässä on tiivistelmä logista:

Viimeisin Commit:

Viimeisin commit, merkitty tunnuksella e4b401e, tehtiin 12. marraskuuta 2023, jossa SNOW.md-tiedostoa päivitettiin käyttäen echo-komentoa.

Merge Commit:

Logissa on myös yhdistämiscommit (merge commit), tunnuksella 9aae901, tehty samana päivänä. Tämä näyttäisi olevan yhdistäminen etärepositoryn kanssa.

Aiemmat Muutokset:

Logissa näkyy useita päivityksiä README.md-tiedostoon. Aluksi commitit tehtiin käyttäen GitHubin generoimaa anonymisoitua sähköpostiosoitetta, mutta myöhemmissä commiteissa käytin henkilökohtaista sähköpostiosoitettani

Sähköpostiosoitteen Muutos:

Muutin Git-konfiguraatioasetuksiani, mukaan lukien sähköpostiosoitteeni, komennolla $ git config --global user.email "-". Tämä tarkoittaa, että tulevissa commiteissa näkyy tämä uusi sähköpostiosoite.
Yhteenvetona, Git-logista käy ilmi, että olen tehnyt useita päivityksiä, erityisesti SNOW.md- ja README.md-tiedostoihin, ja että olen vaihtanut sähköpostiosoitettani Gitin konfiguraatioasetuksissa. Lisäksi logissa on tietoa repositoryn yhdistämisestä GitHubin etärepositoryn kanssa.


### Lähteet

https://chat.openai.com/

https://github.com/Seppohto/Palvelinten-hallinta-Haaga-Helia/

https://terokarvinen.com/2023/configuration-management-2023-autumn/
