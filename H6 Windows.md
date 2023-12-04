#### x) Lue ja tiivistä

Windows 10:n asennus virtuaalikoneelle käy läpi prosessia, jossa Windows asennetaan virtuaaliseen ympäristöön. Ohjeet sisältävät linkin asennusohjeisiin ja kertovat mitä asetuksia tulisi käyttää asennuksen aikana. Yhteyksien testaus virtuaaliympäristössä on osa oppimisprosessia.


Linuxin tiedostojärjestelmän standardi, FSH, ohjeistaa Linux-järjestelmän tiedostojen ja hakemistojen sijoittelua. Se tarjoaa suuntaviivat sille, miten tiedostojärjestelmän tulisi olla organisoitu toimivuuden ja yhteensopivuuden varmistamiseksi.

#### a) Asenna Windows virtuaalikoneeseen

Windowsin virtuaalikoneasennuksen aikana kohtasin virheilmoituksen, jonka mukaan järjestelmällä ei välttämättä ollut tarpeeksi resursseja asennuksen suorittamiseksi. Tämän seurauksena, tutustuin asennusprosessiin enemmän teoreettisesti, käyttäen apuna lähteitä, jotka tarjosivat ohjeita virtuaalikoneelle asennettavasta Windowsista.

#### b) Asenna Salt Windowsille. Osoita 'salt-call --local' komentoa ajamalla, että asennus on onnistunut.

Saltin asentaminen Windowsille vaatii erityisen asennuspaketin, jonka jälkeen asennuksen onnistumista voidaan testata paikallisesti ajettavalla komennolla. Tietoja järjestelmästä, kuten käyttöjärjestelmän tietoja, yhteismuistin määrää ja koneiden rooleja, voidaan tutkia grains.item-komennon avulla.

#### c) Kerää Windows-koneesta tietoa grains.items -toiminnolla. Poimi 'grains.item' perään muutamia keskeisiä tietoja ja analysoi ne, eli selitä perusteellisesti mitä ne ovat. Kuvaile ja vertaile numeroita.


#### d) Kokeile Saltin file -toimintoa Windowsilla.

Saltin file-toiminnolla voidaan hallita tiedostoja Windows-koneilla, kuten tarkistaa tiedoston olemassaolo, luoda uusia tiedostoja, poistaa tiedostoja ja muuttaa tiedostojen oikeuksia. Lisäksi, uudet Salt-toiminnot, kuten aikavyöhykkeen tarkistaminen ja muuttaminen, tarjoavat joustavuutta ja mukautuvuutta järjestelmän hallinnassa.

Näissä prosesseissa hyödynsin erityisesti Saltin dokumentaatiota ja Tero Karvisen antamia opetusmateriaaleja, jotka tarjoavat syvällistä tietoa ja ohjeistusta Saltin käytöstä Windows-ympäristössä.
