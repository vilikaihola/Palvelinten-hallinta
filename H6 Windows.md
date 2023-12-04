#### x) Lue ja tiivistä

Windows 10:n asennus virtuaalikoneelle käy läpi prosessia, jossa Windows asennetaan virtuaaliseen ympäristöön. Ohjeet sisältävät linkin asennusohjeisiin ja kertovat mitä asetuksia tulisi käyttää asennuksen aikana. Yhteyksien testaus virtuaaliympäristössä on osa oppimisprosessia.


Linuxin tiedostojärjestelmän standardi, FSH, ohjeistaa Linux-järjestelmän tiedostojen ja hakemistojen sijoittelua. Se tarjoaa suuntaviivat sille, miten tiedostojärjestelmän tulisi olla organisoitu toimivuuden ja yhteensopivuuden varmistamiseksi.


#### a) Windows 10:n asennus virtuaalikoneeseen

Windows 10 -käyttöjärjestelmän virtuaalikoneasennusprosessi on dokumentoitu, sisältäen ohjeet ja linkit asennusta varten. Asennuksen aikana suositeltavat konfiguraatiot on listattu, ja lisäksi prosessiin kuuluu virtuaaliympäristön yhteyksien testaus. Asennuksen haasteisiin on haettu ratkaisuja lataamalla asennustiedosto uudelleen ja säätämällä asetuksia, mutta ongelman epäillään johtuvan riittämättömästä muistista.

#### b) Saltin asennus ja testaus Windowsissa

Salt-ohjelmiston asennus Windows-käyttöjärjestelmälle vaatii erityisen asennustiedoston, jonka suorittamisen jälkeen voidaan tarkistaa asennuksen onnistuminen ajamalla paikallinen komento. Asennusprosessin yksityiskohtia selostetaan dokumenteissa, ja lopuksi suoritetaan testi varmistaakseen, että Salt on asennettu oikein.

#### c) Koneen tietojen kerääminen Saltin avulla

Saltin grains.items-toiminnolla voidaan kerätä tärkeää tietoa Windows-koneesta, kuten käyttöjärjestelmän yksityiskohdat, muistin kokonaismäärä ja koneiden roolit. Tämän toiminnon avulla saadut tiedot antavat kattavan kuvan järjestelmän ominaisuuksista ja konfiguraatiosta.

#### d) Saltin tiedostohallinnan kokeilu Windowsissa

Saltin file-moduuli tarjoaa monipuolisia toimintoja tiedostojen hallintaan Windows-järjestelmissä. Tämän avulla voidaan suorittaa tiedostoihin liittyviä tehtäviä, kuten tarkistaa tiedoston olemassaolo, luoda ja poistaa tiedostoja sekä muuttaa tiedostojen oikeuksia. Lisäksi tutustutaan uusiin toimintoihin, kuten aikavyöhykkeen hallintaan, joka lisää järjestelmänhallinnan mukautettavuutta.
