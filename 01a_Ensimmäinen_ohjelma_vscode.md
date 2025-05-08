# Ensimmäinen ohjelma

Tervetuloa ohjelmoimaan Python-kieltä Metropolia Ammattikorkeakoulussa!

... ja sama Pythoniksi:

```python
print("Tervetuloa opiskelemaan Python-kieltä!")
```

[Python](https://www.python.org/) on maailman yleisimpiä ohjelmointikieliä. Kun opiskelet Pythonia, voit:

- oppia ohjelmoimaan helposti ja hauskasti
- koodata laadukkailla ja ergonomisilla kehitystyökaluilla
- luoda näyttävää grafiikkaa visualisointikirjastojen avulla
- soveltaa tekoälyä kattavien koneoppimiskirjastojen ansiosta

Ensimmäisenä opiskeluvuonna saat vankat Python-ohjelmoinnin perustaidot. Syvennät osaamistasi myöhemmissä opinnoissa, ja opit käyttämään Python-kieltä työkaluna ohjelmointi- ja ohjelmistotuotantoprojekteissa. 

Tässä ensimmäisessä moduulissa asennat Python-kehitystyökalut ja opit kirjoittamaan ja ajamaan ensimmäisen Python-ohjelmasi.

## Python-ohjelmointiympäristön asennus

Ensimmäisenä tehtävänä onkin asentaa ohjelmointiympäristö, joka koostuu Python-tulkista ja koodieditorista lisäosineen (ohjelmistokehitin). Tällä opintojaksolla käytetään [Visual Studio Code](https://code.visualstudio.com/) -kehitintä.

Ohjelmointiympäristön asentaminen tapahtuu [näiden ohjeiden](https://code.visualstudio.com/docs/python/python-tutorial) mukaisesti.

### Python-tulkin asennus

Python-tulkki on ohjelma, joka lause kerrallaan tulkkaa Python-kieliset lauseet tietokoneen suorittimen ymmärtämään muotoon eli konekielelle. Sen asentaminen on välttämätöntä, jotta voit ohjelmoida Pythonilla.

1. Siirry selaimella sivulle <https://www.python.org/downloads/>.
1. Lataa viimeisin versio (3.x.x) Pythonista omalle käyttöjärjestelmällesi. (Windows, MacOS) ja käynnistä asennusohjelma.
1. Etene ohjatun toiminnon esittämällä tavalla, ja asenna Python asennusohjelman ehdottamaan oletussijaintiin.

**Tärkeää:** Ohjattu asennustoiminto tarjoaa mahdollisuuden lisätä Python-tulkki Windows-käyttöjärjestelmän `PATH`-ympäristömuuttujaan. Kyseinen ympäristömuuttuja sisältää luettelon kansioista, joista käyttöjärjestelmä etsii suoritettavia ohjelmia automaattisesti. Lisäys kannattaa tehdä: sen ansiosta voit antaa komentoikkunassa komennon `python` (tai `python3`) mistä tahansa kansiosta, ja Python-tulkki löytyy automaattisesti. (Tästä on hyötyä tulevilla Laitteisto 1 ja 2 -opintojaksoilla, joilla myös työskennellään Pythonilla.)

Seuraava kuva näyttää valintaruudun, josta lisäys tehdään:

![PATH-ympäristömuuttujan päivittäminen](img/path_envvar.png)

>Tällä kurssilla käytetään myös MariaDB-tietokantaa. Sen vaatima MySQL Connector/Python -ajuri ei tätä kirjoitettaessa (elokuu 2022)
vielä tue uusimpia Python 3.10 -versioita. Tästä syystä kannattaa valita hieman vanhempi versio (esimerkiksi 3.9), jolle
tuki on jo olemassa. Jos lataat nyt uusimman Python-version, voit myöhemmin joutua asentamaan aiemman version rinnalle.

### Kehittimen asennus

1. Lataa ja asenna [Visual Studio Code](https://code.visualstudio.com/).
1. Asennuksen jälkeen avaa Visual Studio Code ja asenna [Python-laajennus](https://marketplace.visualstudio.com/items?itemName=ms-python.python).

### Ensimmäisen ohjelmointiprojektin ja Python-tiedoston luonti

Nyt olet valmis kirjoittamaan ensimmäisen ohjelman. Ensimmäiseksi on perustettava projekti. Projektia voi ajatella eräänlaisena salkkuna, johon kerätään samaan aihepiiriin liittyviä ohjelmia. Esimerkiksi ensimmäisiä ohjelmointikokeiluja varten voit perustaa uuden projektin nimeltä ´python-harjoitukset´. Projekti on käytännössa sitä varten omistettu **kansio** tietokoneen käyttöjärjestelmän tiedostojärjestelmässä, johon kerätään kaikki ohjelmatiedostot ja mahdolliset muut tiedostot, joita ohjelma tarvitsee toimiakseen.

Tee siis projektia varten uusi kansio. Voit luoda kansion esimerkiksi työpöydälle tai omiin asiakirjoihisi. Anna kansion nimeksi `python-harjoitukset`. Avaa luotu kansio Visual Studio Codessa. Voit tehdä sen valitsemalla **File / Open Folder** ja valitsemalla sitten luomasi kansion.

// TODO: korjaa loput


Uusi projekti perustetaan oletusarvoisesti virtuaaliympäristöön (venv). Tämä helpottaa ohjelmien käyttämien
pakkausten ja niiden versioiden hallintaa.

Kun painat **Create**, kehitin kysyy, avataanko projekti olemassaolevassa vai uudessa ikkunassa. Voit valita kumman vain vaihtoehdon.

Näytön vasempaan reunaan ilmestyy projektipuu, joka näyttää projektiin kuuluvat tiedostot:

![Uuden projektin luonti](img/projektipuu.png)

Jokainen ohjelma kirjoitetaan tiedostoon projektin kansiohierarkian sisälle. Voit tehdä ensimmäistä
ohjelmaa varten uuden tiedoston napsauttamalla projektin nimeä projektipuussa hiiren kakkospainikkeella.
Valitse sitten **New / Python file** ja kirjoita avautuvaan valintaikkunaan tiedoston nimi, esimerkiksi
`heimaailma`.
Projektipuuhun ilmestyy kuvassa näkyvä tiedosto nimeltä `heimaailma.py`. Python-ohjelma kirjoitetaan tiedostoihin, joiden päättenä on ´.py´. 


## Ohjelman kirjoitus, tallennus ja ajo

Ohjelma, eli Python-lähdekoodi, kirjoitetaan editorikenttään: 

![Ensimmäinen ohjelma](img/ekaohjelma.png)

Voit suorittaa eli ajaa ohjelman napsauttamalla hiiren kakkospainiketta editorikentässä ja valitsemalla **Run 'hello'**.

Tuloste ilmestyy alareunan konsoli-ikkunaan:

```output
Hei, maailma!
```

Jos ohjelmassa on virheitä, ei hätää! Saat virheilmoituksen, joka auttaa virheen paikantamisessa. Sen jälkeen voit
korjata ohjelmaa niin monta kertaa kuin on tarpeen ja suorittaa sen aina uudelleen.

Virheiden teko kuuluu ohjelmointiin. On arvioitu, että 80 prosenttia ammattimaisen ohjelmoijan työajasta kuuluu
virheiden jäljitykseen ja niiden korjaamiseen. Myös oppiminen tapahtuu virheitä tekemällä. Kun selvität virheen
syyn ja korjaat sen, olet oppinut hieman paremmaksi ohjelmoijaksi.

