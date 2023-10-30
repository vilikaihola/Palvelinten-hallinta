## H1 Viisikko
x) Lue ja tiivistä. (Tässä x-alakohdassa ei tarvitse tehdä testejä tietokoneella, vain lukeminen tai kuunteleminen ja tiivistelmä riittää. Tiivistämiseen riittää muutama ranskalainen viiva.)
#
Karvinen 2023: Create a Web Page Using Github
-Rekisteröidy Githubiin ja luo uusi repositorio (lisää README.md-tiedosto luodessasi).
-Lisää .md-tiedosto verkkosivullesi, kirjoita tekstiä ja tee commit.
-Sivusi julkaistaan automaattisesti.
-Markdown mahdollistaa otsikoiden, tekstikappaleiden ja koodin helpon muotoilun.
-Voit myöhemmin edetä Githubin edistyneempiin ominaisuuksiin ja kokeilla vastaavia toimintoja Gitlabissa tai muissa Git-pohjaisissa palveluissa.
#
Karvinen 2023: Run Salt Command Locally
-Salt-komentoja voidaan ajaa paikallisesti harjoitteluun, testaukseen ja nopeaan asetukseen.
-Tärkeimmät tilafunktiot ovat pkg, file, service, user ja cmd.
-Salt asennetaan normaalisti ohjaamaan useita orjakoneita verkossa, mutta voidaan käyttää myös paikallisesti.
-Esimerkkejä komentojen käytöstä Debianissa tai Ubuntussa annettu, kuten sovellusten asennus ja poisto, tiedostojen hallinta, palveluiden käynnistys ja pysäytys, käyttäjien luominen ja poistaminen, sekä komentojen suorittaminen.
-Komentojen idempotenssi varmistetaan määritteillä kuten creates, unless, ja onlyif.
#
a) Asenna Salt (salt-minion) koneellesi.
  Asensin Salt:in käyttämällä Teron ohjeita (https://terokarvinen.com/2023/configuration-management-2023-autumn/)
  #
b) Viisi tärkeintä. Näytä esimerkit viidestä tärkeimmästä Saltin tilafunktiosta: pkg, file, service, user, cmd. Analysoi ja selitä tulokset.
  pkg= pkg installed ja pkg removed ovat tilafunktioita jotka hallitsevat ohjelmistopakettien asennusta ja poistoa järjestelmästä. Molemmat komennot antoivat outputin succeeded, eli ilmeisesti ne onnistuivat
  file= Ensimmäinen komento luo tyhjän tiedoston nimeltä /tmp/hellotero, jos sitä ei ole olemassa. Toinen komento luo tiedoston /tmp/moitero sisällöllä "foo", tai päivittää sen sisällön "foo":ksi, jos tiedosto on jo olemassa. Kolmas komento poistaa tiedoston /tmp/hellotero, jos se on olemassa. Kaikkien komentojen suoritus ilmoitti "succeeded (changed 1)", mikä tarkoittaa, että jokainen komento muutti järjestelmän tilaa onnistuneesti.
  service= Ensimmäinen komento yritti varmistaa, että apache2-palvelu on käynnissä ja käynnistyy automaattisesti, mutta epäonnistui ilmeisesti virheilmoituksen "Invalid function passed" takia. Toinen komento varmisti, että apache2-palvelu ei ole käynnissä eikä käynnisty automaattisesti, ja se onnistui, kuten ilmoitus "succeeded" osoitti.
  user= Ensimmäisellä käskyllä luotiin uusi käyttäjä terote08 ja toisella komennolla poistettiin käyttäjä terote08.
cmd= 
Komento $ sudo salt-call --local -l info state.single cmd.run 'touch /tmp/foo' creates="/tmp/foo" suorittaa touch /tmp/foo -komentoa luoden uuden tyhjän tiedoston nimeltä /tmp/foo, jos sitä ei ole olemassa. Parametri creates="/tmp/foo" estää komennon suorituksen, jos tiedosto on jo olemassa. Ilmoitus "succeeded (changed=1)" tarkoittaa, että tiedosto luotiin onnistuneesti.
#
c) Idempotentti. Anna esimerkki idempotenssista. Aja 'salt-call --local' komentoja, analysoi tulokset, selitä miten idempotenssi ilmenee.
  Esimerkki idempotenssista käyttäen salt-call --local -komentoja:

Tiedoston luonti:
Komento: $ sudo salt-call --local state.single file.managed /tmp/idem_example contents="Hello, World!"
Ensimmäisellä suorituksella tiedosto luodaan, ja output on "succeeded (changed=1)". Toisella suorituksella, koska tiedosto on jo olemassa oikealla sisällöllä, output on "succeeded (changed=0)".

Tiedoston poisto:
Komento: $ sudo salt-call --local state.single file.absent /tmp/idem_example
Ensimmäisellä suorituksella tiedosto poistetaan, ja output on "succeeded (changed=1)". Toisella suorituksella, koska tiedosto on jo poistettu, output on "succeeded (changed=0)".

Idempotenssin ilmeneminen:

Idempotenssi ilmenee siinä, että toisen suorituksen aikana järjestelmän tila ei muuttunut, koska haluttu tila oli jo saavutettu ensimmäisen suorituksen aikana. Komennon toistuva suorittaminen ei aiheuttanut muutoksia järjestelmän tilassa, mikä on idempotenssin ydin.
#
d) Tietoa koneesta. Kerää tietoja koneesta Saltin grains.items -tekniikalla. Poimi kolme kiinnostavaa kohtaa, näytä tulokset ('grains.item osfinger virtual') ja analysoi ne.
  Productname=VirtualBox: Järjestelmäsi on virtualisoitu Oracle VirtualBox -alustalla.
os_family=Debian: Käytössäsi on Debian-käyttöjärjestelmäperheen jakelu.
osarch=amd64: Järjestelmäsi on 64-bittinen, mikä mahdollistaa suuremman muistimäärän ja paremman suorituskyvyn.
  ## References 
  https://terokarvinen.com/2023/create-a-web-page-using-github/
  https://terokarvinen.com/2021/salt-run-command-locally/
  
