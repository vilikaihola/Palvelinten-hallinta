# H3 Versio

## a) Online. Tee uusi varasto GitHubiin (tai Gitlabiin tai mihin vain vastaavaan palveluun). Varaston nimessä ja lyhyessä kuvauksessa tulee olla sana "winter". Aiemmin tehty varasto ei kelpaa. (Muista tehdä varastoon tiedostoja luomisvaiheessa, esim README.md ja GNU General Public License 3)

Loin uuden GitHub-varaston nimeltä "winteriscoming", joka täyttää annetut vaatimukset: varaston nimi ja kuvaus sisältävät sanan "winter". Varastoon lisäsin alustavat tiedostot, kuten README.md, joka antaa perustiedot projektista, ja GNU General Public License 3 -lisenssin, joka määrittelee ohjelmiston käyttöehdot. Tämä varasto on nyt valmis talviaiheisille ohjelmistoprojekteille ja niiden dokumentoinnille.

## b) Dolly. Kloonaa edellisessä kohdassa tehty uusi varasto itsellesi, tee muutoksia, puske ne palvelimelle, ja näytä, että ne ilmestyvät weppiliittymään.

 Ajoin ensiksi komennon git clone https://github.com/vilikaihola/winteriscoming git versionhallintatyökalun terminaalissa, joka toimi mainiosti:

![image](https://github.com/vilikaihola/Palvelinten-hallinta/assets/148875596/f0bbd985-9400-4739-b5cf-ed091846a651)

#### 1. Muutosten Lisääminen (git add .):

Tämä komento lisää kaikki paikallisen hakemiston muutetut tiedostot Gitin seurantaan valmistellen niitä tallennettavaksi (commit). Piste (.) merkitsee, että kaikki muutokset nykyisessä hakemistossa lisätään, mukaan lukien uudet, muutetut ja poistetut tiedostot.
Tämä vaihe on välttämätön, koska Git ei automaattisesti ota huomioon kaikkia muutoksia, vaan sinun täytyy erikseen kertoa Gitille, mitkä muutokset haluat sisällyttää seuraavaan commitiin.

![image](https://github.com/vilikaihola/Palvelinten-hallinta/assets/148875596/6b0c9ed1-c316-4ba8-9c18-550dc87bb2f1)

Seuraavassa kohdasssa kohtasin pienimuotoisen ongelman,joka johtui siitä että olin tehnyt muutoksia "winteriscoming" repositoryyn näiden askeleiden välissä. 

![image](https://github.com/vilikaihola/Palvelinten-hallinta/assets/148875596/3c682e4a-cdbf-4b76-993e-6f12c1ba3aff)

Ongelma ratkesi ajamalla komennon git pull origin main, jonka jälkeen git push komento toimi toivotulla tavalla.

![image](https://github.com/vilikaihola/Palvelinten-hallinta/assets/148875596/ef812601-e57a-4b6b-9d44-3af6ff2ee91f)


![image](https://github.com/vilikaihola/Palvelinten-hallinta/assets/148875596/c478fcfa-99c1-48ee-a3a0-07e257ff12eb)

