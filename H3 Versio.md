# H3 Versio

### a) Online. Tee uusi varasto GitHubiin (tai Gitlabiin tai mihin vain vastaavaan palveluun). Varaston nimessä ja lyhyessä kuvauksessa tulee olla sana "winter". Aiemmin tehty varasto ei kelpaa. (Muista tehdä varastoon tiedostoja luomisvaiheessa, esim README.md ja GNU General Public License 3)

Loin uuden GitHub-varaston nimeltä "winteriscoming", joka täyttää annetut vaatimukset: varaston nimi ja kuvaus sisältävät sanan "winter". Varastoon lisäsin alustavat tiedostot, kuten README.md, joka antaa perustiedot projektista, ja GNU General Public License 3 -lisenssin, joka määrittelee ohjelmiston käyttöehdot. Tämä varasto on nyt valmis talviaiheisille ohjelmistoprojekteille ja niiden dokumentoinnille.

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

![image](https://github.com/vilikaihola/Palvelinten-hallinta/assets/148875596/10823de4-a860-4484-a15d-7932bcca6ff1)

### c) Doh! Tee tyhmä muutos gittiin, älä tee commit:tia. Tuhoa huonot muutokset ‘git reset --hard’. Huomaa, että tässä toiminnossa ei ole peruutusnappia.

