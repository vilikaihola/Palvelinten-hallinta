### (x  Lue ja tiivistä. (Tässä x-alakohdassa ei tarvitse tehdä testejä tietokoneella, vain lukeminen tai kuunteleminen ja tiivistelmä riittää. Tiivistämiseen riittää muutama ranskalainen viiva.)
###### Karvinen 2018: Apache User Homepages Automatically – Salt Package-File-Service Example
Tero Karvisen artikkeli "Apache User Homepages Automatically – Salt Package-File-Service Example" keskittyy SaltStackin käyttöön Apache-palvelimen konfiguroinnissa, erityisesti käyttäjien kotisivujen automaattiseen määrittämiseen.

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

Tiivistelmässä korostetaan konfiguraatioiden hallinnan tärkeyttä ja sitä, miten SaltStackin avulla voi tehokkaasti ottaa käyttöön ja ylläpitää web-palvelimen asetuksia, mukaan lukien käyttäjäkohtaiset kotisivut.
