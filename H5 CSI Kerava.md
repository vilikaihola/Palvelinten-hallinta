### (x  Lue ja tiivistä. (Tässä x-alakohdassa ei tarvitse tehdä testejä tietokoneella, vain lukeminen tai kuunteleminen ja tiivistelmä riittää. Tiivistämiseen riittää muutama ranskalainen viiva.)
###### Karvinen 2018: Apache User Homepages Automatically – Salt Package-File-Service Example
Artikkeli "Apache User Homepages Automatically – Salt Package-File-Service Example" keskittyy SaltStackin käyttöön Apache-palvelimen konfiguroinnissa, erityisesti käyttäjien kotisivujen automaattiseen määrittämiseen.

Konfiguraatiotiedostojen Sijainti:
Ennen automatisointia, asennukset tulisi tehdä manuaalisesti, jotta tiedostaisit, mitä konfiguraatiotiedostoja tarvitsee muuttaa.

Moduulin Aktivointi:
Käyttäen komentoa a2enmod userdir voit ottaa käyttöön moduulin, ja find-komennon avulla voit selvittää, mitkä tiedostot ovat muuttuneet.

Idempotenttinen Komento:
Kun komentoa käytetään Salt state -tiedostossa, on varmistettava, että komento on idempotenttinen, eli toistuva suoritus ei muuta järjestelmän tilaa.

Käyttö Paremmalla Tavalla:
Artikkelissa suositellaan komentojen sijaan tiedostojen käyttöä, koska se on luotettavampi tapa hallita Salt states -tiedostoja.

Salt States -tiedosto:
init.sls-tiedostossa määritellään paketit, tiedostot ja palvelut, jotka SaltStack varmistaa olevan halutussa tilassa.

Testaus:
Lopuksi artikkeli ohjeistaa, miten voit testata konfiguraatiota luomalla käyttäjän kotisivun manuaalisesti ja varmistamalla, että se toimii oikein selaimessa.

### (a CSI Kerava. Näytä 'find' avulla viimeisimmäksi muokatut tiedostot /etc/-hakemistosta ja kotihakemistostasi. Selitä kaikki käyttämäsi parametrit ja format string 'man find' avulla.

 Viimeisimmäksi muokatut tiedostot /etc/-hakemistosta:

![image](https://github.com/vilikaihola/Palvelinten-hallinta/assets/148875596/a9ae24d4-1214-4668-a319-c333ba64494e)

Viimeisimmäksi muokatut tiedostot kotihakemistostasi:

![image](https://github.com/vilikaihola/Palvelinten-hallinta/assets/148875596/1d87fe10-052a-45e5-bfae-ffc84a71f628)

Selitys käytetyille parametreille ja format string -merkinnöille:

/etc/ ja ~/: Hakemistot, joista etsitään tiedostoja.
-type f: Etsii vain tiedostoja, ei hakemistoja.
-printf: Määrittelee tulostusmuodon seuraavasti:
%TY: Muokkausvuosi nelinumerisena.
%Tm: Muokkauskuukausi kaksinumerisena.
%Td: Muokkauspäivä kaksinumerisena.
%TH: Muokkaustunnin kaksinumeroinen esitys.
%TM: Muokkausminuutin kaksinumeroinen esitys.
%TS: Muokkaussekuntien kaksinumeroinen esitys, desimaaleineen.
%p: Tulostaa täyden polun tiedostoon.
\n: Uusi rivi jokaisen tulosteen jälkeen.
| sort -r: Putkittaa tuloksen sort-komennolle, joka järjestää rivit käänteisessä järjestyksessä (uusimmat ensin).
| head: Putkittaa tuloksen head-komennolle, joka rajoittaa tulosteen ensimmäiseen 10 riviin.

Tässä tehtävässä tärkeää on myös ymmärtää, mitä kukin komennon osa tekee:

-type f etsii vain tiedostoja, ei hakemistoja.
-mtime -1 etsii tiedostoja, jotka ovat muuttuneet viimeisen 24 tunnin aikana.
-exec ls -lt {} + listaa löydetyt tiedostot yksityiskohtaisesti ja aikajärjestyksessä.

### (b  Gui2fs. Muokkaa asetuksia jostain graafisen käyttöliittymän (GUI) ohjelmasta käyttäen ohjelman valikoita ja dialogeja. Etsi tämä asetus tiedostojärjestelmästä.

Tässä tehtävässä vaihdoin VB:llä pyörivän Debian järjestelmäni tasutakuvan ja etsin tämän asetuksen tiedostojärjestelmästä. 

![image](https://github.com/vilikaihola/Palvelinten-hallinta/assets/148875596/2f9f77a8-7f33-4f86-a946-f0287f3601e6)

Koitin myös tarkastella tiedoston sisältöä, mutta en onnistunut saaamaan tiedostosta irti muuta kuin binääri muodossa kirjoitetun sisällön, josta en ymmärtänyt mitään.
### (c  Komennus. Tee Salt-tila, joka asentaa järjestelmään uuden komennon.
