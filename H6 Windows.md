#### x) Lue ja tiivistä

Windows 10:n asennus virtuaalikoneelle käy läpi prosessia, jossa Windows asennetaan virtuaaliseen ympäristöön. Ohjeet sisältävät linkin asennusohjeisiin ja kertovat mitä asetuksia tulisi käyttää asennuksen aikana. Yhteyksien testaus virtuaaliympäristössä on osa oppimisprosessia.


Linuxin tiedostojärjestelmän standardi, FSH, ohjeistaa Linux-järjestelmän tiedostojen ja hakemistojen sijoittelua. Se tarjoaa suuntaviivat sille, miten tiedostojärjestelmän tulisi olla organisoitu toimivuuden ja yhteensopivuuden varmistamiseksi.


#### a) Windows 10:n asennus virtuaalikoneeseen

Windows 10 -käyttöjärjestelmän virtuaalikoneasennusprosessi on dokumentoitu, sisältäen ohjeet ja linkit asennusta varten. Asennuksen aikana suositeltavat konfiguraatiot on listattu, ja lisäksi prosessiin kuuluu virtuaaliympäristön yhteyksien testaus. Asennuksen haasteisiin on haettu ratkaisuja lataamalla asennustiedosto uudelleen ja säätämällä asetuksia, mutta ongelman epäillään johtuvan riittämättömästä muistista.

#### b) Saltin asennus ja testaus Windowsissa

Salt-ohjelmiston asentaminen Windows-järjestelmään vaatii ensin asennuspaketin lataamista. Ohjelmiston voi hankkia virallisilta SaltStackin sivuilta, joiden ohjeita noudattaen suoritetaan asennus. Tiedostot ladataan ja asennetaan, jonka jälkeen tehdään tarvittavat konfiguraatiot. Tämä sisältää Masterin ja Minionin nimien määrittämisen, jotka ovat keskeisiä SaltStackin hajautetun hallinnan arkkitehtuurissa.

Kun asennus on valmis, suoritetaan paikallinen komento salt-call --local --version varmistamaan, että Salt on asennettu oikein ja on toimintakunnossa. Tämä komento palauttaa asennetun Salt-version, joka on merkki onnistuneesta asennuksesta. Onnistunut asennus tarkoittaa, että voimme alkaa käyttää Saltia tehtävien automatisointiin ja järjestelmänhallintaan Windows-ympäristössä.

#### c) Koneen tietojen kerääminen Saltin avulla


Saltin grains.items-toiminto on tehokas työkalu, joka kerää tietoa hallittavista koneista. Tämä toiminto antaa yksityiskohtaista tietoa, joka auttaa ymmärtämään kunkin järjestelmän ominaisuudet.

Käyttämällä komentoa salt '*' grains.item os*, saan selville kaikki käyttöjärjestelmään liittyvät grains-tiedot, kuten käyttöjärjestelmän version, perheen ja koodinimen. Tämä tieto on hyödyllistä, kun haluan varmistaa yhteensopivuuden sovellusten ja päivitysten kanssa tai tunnistaa eri koneiden väliset käyttöjärjestelmien erot.

Toisena komentona salt '*' grains.item mem_total kertoo minulle kokonaismuistin määrän gigatavuina kussakin koneessa. Tämä on kriittinen tieto resurssien suunnittelussa ja kapasiteetin hallinnassa, auttaen minua arvioimaan, onko koneilla tarpeeksi muistia suorittaa tietyt tehtävät.

Lopuksi, komennolla salt '*' grains.item roles saan listan rooleista tai ryhmistä, joita kukin kone palvelee Salt-ympäristössä. Roolit voivat kuvata koneen tehtävää, kuten web-palvelin tai tietokantapalvelin, ja auttaa minua ymmärtämään jokaisen koneen vastuun suuremmassa infrastruktuurissa.

Näiden komentojen avulla pystyn keräämään kattavan kuvan Windows-ympäristön koneiden nykytilasta, mikä mahdollistaa tehokkaamman hallinnan ja suunnittelun.

#### d) Saltin tiedostohallinnan kokeilu Windowsissa

Saltin file-moduulin avulla voit tehokkaasti hallita tiedostoja Windows-järjestelmissä. Se tarjoaa laajan valikoiman toimintoja tiedostojen käsittelyyn. Katsotaanpa, mitä eri komentoja voidaan suorittaa ja mitä ne tekevät:

Komento salt '*' file.file_exists C:\path\to\file.txt auttaa selvittämään, löytyykö määritetty tiedosto halutusta sijainnista. Tämä on hyödyllinen ensimmäinen tarkistus ennen tiedostoon kohdistuvia toimenpiteitä. Tämä komento palauttaa totuusarvon, joka kertoo tiedoston olemassaolosta.

Uuden tiedoston luominen onnistuu komennolla salt '*' file.touch C:\path\new_file.txt. Jos tiedostoa ei ole olemassa, tämä komento luo sen. Jos tiedosto on jo olemassa, komento päivittää sen muokkausaikaleiman nykyhetkeen.

Kun haluat poistaa tiedoston, käytä komentoa salt '*' file.remove C:\path\to\file.txt. Tämä poistaa valitun tiedoston pysyvästi, joten käytä tätä varoen.

Jos tarvitsee muuttaa tiedoston käyttöoikeuksia, käytetään komentoa salt '*' file.set_mode C:\path\to\file.txt 777. Tämä asettaa tiedostolle luku-, kirjoitus- ja suoritusoikeudet kaikille käyttäjille. Windows-ympäristössä tämä komento voi kuitenkin käyttäytyä toisin, sillä Unix-tyylisten oikeuksien konsepti on erilainen Windowsissa.


#### e) Aikavyöhykkeen säätäminen Saltilla Windowsissa

Kun syvennyin Saltin komentoihin Windows-ympäristössä, huomasin, että aikavyöhykkeen hallinta on mahdollista suorittaa helposti komentoriviltä. Käyttämällä komentoa salt '*' win_timezone.get_zone, voisin nopeasti tarkastella, minkä aikavyöhykkeen alla jokainen Windows-kone toimii. Tämä on erityisen kätevää, kun halutaan varmistaa, että kaikki palvelimet noudattavat samaa aikaa.

Jos tarvetta ilmenee, voisin myös muuttaa aikavyöhykettä komennolla salt '*' win_timezone.set_zone 'Eastern Standard Time'. Tämä komento sallisi minun asettaa koneet haluamalleni aikavyöhykkeelle, olipa kyseessä sitten siirtyminen kesäaikaan tai ajan synkronointi toisen toimipisteen kanssa. Tämä joustavuus Saltin avulla tekee palvelinten ylläpidosta sujuvampaa ja vähentää manuaalisen konfiguroinnin tarvetta

#### Lähteet

https://docs.saltproject.io/en/latest/ref/modules/all/salt.modules.grains.html

https://terokarvinen.com/2023/configuration-management-2023-autumn/

https://github.com/therealhalonen/PhishSticks/blob/master/notes/ollikainen/windows.md

https://terokarvinen.com/2018/04/18/control-windows-with-salt/
