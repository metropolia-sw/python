# Luokka, olio, alustaja

Tässä moduulissa opit olio-ohjelmoinnin lähtökohdat. Opit kirjoittamaan luokkia, jotka määrittävät yhteiset ominaisuudet ja operaatiot luokan ilmentymille eli olioille. Opit olioiden luonnin, alustamisen ja käytön periaatteet.

## Luokat ja oliot

Olio-ohjelmoinnissa luokalla tarkoitetaan yleiskäsitettä, joka määrittää yleiset ja yhteiset piirteet, joita sen jäsenillä on.

Esimerkiksi **koira** on tällainen yleiskäsite. Jokaisella koiralla on joukko ominaisuuksia kuten nimi ja syntymävuosi. Lisäksi koiralla on toimintoja (eli Python-termein metodeja) kuten haukkuminen.

Voimme nyt kirjoittaa pienimmän mahdollisen Koira-luokan seuraavasti:

```python
class Koira:
    pass
```

Edellä `pass`-lause on tyhjä lause, joka ei tee mitään. Se tarvitaan paikkamerkiksi, sillä luokan määrityksen rungossa on oltava ainakin yksi lause.

Tämä luokan määritys vain kertoo, että on olemassa Koira-luokka. Se ei toistaiseksi ota kantaa koirien ominaisuuksiin eikä niiden metodeihin.

Voimme käyttää Koira-luokkaa siten, että luomme tuosta luokasta olion. Olio tarkoittaa luokan ajonaikaista ilmentymää eli realisaatiota. Luomme näin Koira-olion, joka on nimeltään Rekku ja jonka syntymävuosi on 2022:

```python
class Koira:
    pass
   
koira = Koira()
koira.nimi = "Rekku"
koira.syntymävuosi = 2022

print (f"{koira.nimi} on syntynyt vuonna {koira.syntymävuosi}." )
```

Pääohjelman ensimmäinen lause luo Koira-olion, johon viitataan muuttujalla `koira`. Luodulle koiralle annetaan nimeksi Rekku ja syntymävuodeksi 2022. Nämä ovat luodun olion ominaisuuksia, ja ne ovat oliokohtaisia. Voisimme siis luoda monta koiraa, joista jokaisella olisi oma yksilöllinen nimensä ja syntymävuotensa. Jollekin koirista voisimme lisäksi määrittää rodun ja jollekin lempinimen. Olioiden ominaisuudet voivat siis poiketa toisistaan.

Kuten esimerkistä näkyy, olion ominaisuuteen viitataan kirjoittamalla ensin olion nimi, sitten piste ja lopuksi ominaisuuden nimi. Esimerkki tällaisesta viittauksesta on `koira.nimi`.

Esimerkkiohjelman viimeinen lause tulostaa pääohjelman luoman koiraolion nimen ja syntymävuoden:

```monospace
Rekku on syntynyt vuonna 2022.
```

Huomaa Python-kielen vakiintunut kirjoitustapa luokkien nimille: ne kirjoitetaan isoin alkukirjaimin. Jos luokan nimi koostuu useammasta sanasta, sanat kirjoitetaan yhteen ilman alaviivamerkkiä siten, että kukin sana aloitetaan isolla alkukirjaimella. Tästä kirjoitustyylistä käytetään nimitystä *CamelCase*. Esimerkki tällaisesta luokan nimestä on `NäytönSuorakulmio`.

## Alustaja eli konstruktori

Edellä Koira-olio luotiin siten, että ensin tehtiin olio ilman ominaisuuksia, ja sen jälkeen oliolle määritettiin ominaisuudet yksi kerrallaan. Tämä on ohjelmoijalle melko työläs tapa luoda olioita.

Olioiden luonnin helpottamiseksi luokan sisälle kirjoitetaan usein alustaja eli konstruktori, joka automaattisesti asettaa halutut arvot luotavan olion ominaisuuksiksi. Seuraavan esimerkin luokassa on nimen ja syntymävuoden asettava alustaja. Pääohjelma käyttää olion luonnissa juuri laadittua alustajaa:

```python
class Koira:
    def __init__(self, nimi, syntymävuosi):
        self.nimi = nimi
        self.syntymävuosi = syntymävuosi

koira = Koira("Rekku", 2022)

print (f"{koira.nimi} on syntynyt vuonna {koira.syntymävuosi}." )
```

Python-kielen alustaja määritetään luokan sisällä kirjoittamalla funktio, jonka nimenä on `__init__`. Funktion ensimmäiseksi parametriksi määritetään aina `self`. Tämän jälkeen määritellään muut parametrit, jotka alustajalle halutaan antaa. Tässä tapauksessa ne ovat nimi ja syntymävuosi. Näin kirjoitettu ja nimetty funktio tulkitaan ohjelmaa ajettaessa automaattisesti alustajaksi, ja se suoritetaan aina, kun uusi olio luodaan. Alustajan loppuun ei kirjoiteta return-lausetta.

Alustajan sisällä on kaksi sijoituslausetta, joilla annetaan arvot luotavan olion ominaisuuksille. Uuden olion ominaisuuksiin viitataan kirjoittamalla varattu sana `self`, minkä jälkeen tulee piste ja halutun ominaisuuden nimi. Uuden olion ominaisuuden arvoksi annetaan tyypillisesti alustajan parametrina saatu arvo. Esimerkiksi lause `self.nimi = nimi` antaa uuden olion nimi-ominaisuuden arvoksi nimi-parametrimuuttujan arvon.

Huomaa, että oliota luotaessa alustajan ensimmäinen parametri `self` ohitetaan kokonaan. Ei siis kirjoiteta:

```python
# Virheellinen luontilause
koira = Koira(self, "Rekku", 2022)
```

vaan kirjoitetaan:

```python
koira = Koira("Rekku", 2022)
```

## Metodit

Edellä opittiin määrittämään oliolle ominaisuuksia. Tämän lisäksi olioille halutaan usein määrittää toimintoja, joita  kutsutaan metodeiksi. Kirjoitetaan alla Koira-luokkaan hauku-metodi, jota voidaan kutsua Koira-luokan ilmentymille eli olioille. Esimerkin ohjelma luo kaksi Koira-oliota ja käskee niitä haukkumaan kyseiselle oliolle tyypilliseen tapaan:

```python
class Koira:
    def __init__(self, nimi, syntymävuosi, haukahdus="Vuh-vuh"):
        self.nimi = nimi
        self.syntymävuosi = syntymävuosi
        self.haukahdus = haukahdus

    def hauku(self, kerrat):
        for i in range(kerrat):
            print(self.haukahdus)
        return


koira1 = Koira("Muro", 2018)
koira2 = Koira("Rekku", 2022, "Viu viu viu")

koira1.hauku(2)
koira2.hauku(5)
```

Alustajan parametreja on nyt kolme. Viimeiselle parametrille (`haukahdus`) on annettu oletusarvo, joka asetetaan silloin, kun parametria ei oliota luotaessa anneta. Esimerkissä Muro-koira saa siis oletushaukahduksen.

Luokan sisään kirjoitettiin `hauku`-niminen metodi, jota voidaan kutsua mille tahansa olemassa olevalle Koira-luokan ilmentymälle. Metodin ensimmäiseksi parametriksi asetetaan aina `self`. Tämän jälkeen luetellaan muut parametrit, joiden arvo annetaan metodia kutsuttaessa.

Metodin kutsu tehdään siten, että kirjoitetaan olion nimi, sen jälkeen piste ja lopuksi metodin nimi kaarisulkeineen ja mahdollisine parametreineen. Esimerkiksi kutsu `koira1.hauku(2)` kutsuu koira1-olion hauku-metodia. Metodikutsun parametrina välitetään haukahdusten määrä (2). Metodin sisällä voidaan viitata olion omiin ominaisuuksiin siten, että kirjoitetaan `self`, jota seuraa piste ja ominaisuuden nimi. Esimerkiksi ilmaisu `self.haukahdus` viittaa kulloisenkin olion `haukahdus`-ominaisuuden arvoon.

## Luokkamuuttuja eli staattinen muuttuja

Aiemmassa esimerkissä koiran ominaisuuksina olivat nimi, syntymävuosi ja haukahdus. Olion ominaisuudet ovat tietenkin oliokohtaisia, eli yhdellä koiralla voi olla eri nimi kuin toisella koiralla.

Toisinaan on tarve tallentaa jokin koko luokkaa koskeva tieto, joka ei liity mihinkään yksittäiseen luokan olioon. Esimerkiksi `Koira`-luokan tapauksessa tällainen ominaisuus voisi olla tieto siitä, montako koiraa (eli `Koira`-luokan ilmentymää) kaiken kaikkiaan on luotu. Tällainen tieto voidaan tallentaa luokkamuuttujaan eli staattiseen muuttujaan.

Seuraavassa esimerkissä on laadittu `tehty`-niminen luokkamuuttuja lukumäärän tallentamiseksi. Huomaa muuttujan sijoittaminen alustajan ulkopuolelle. Luokkamuuttujan määrityslauseeseen ei lisätä `self.`-etuliitettä. (Esimerkistä on jätetty pois aiempi haukkumistoiminnon toteutus.)

```python
class Koira:

    tehty = 0

    def __init__(self, nimi, syntymävuosi, haukahdus="Vuh-vuh"):
        self.nimi = nimi
        self.syntymävuosi = syntymävuosi
        self.haukahdus = haukahdus
        Koira.tehty = Koira.tehty + 1

koira1 = Koira("Muro", 2018)
koira2 = Koira("Rekku", 2022, "Viu viu viu")
print (f"Koiria on nyt {Koira.tehty}.")
```

Luokkamuuttujan arvoon viitataan kirjoittamalla sekä luokan että luokkamuuttujan nimi, esimerkissä siis `Koira.tehty`.

Ohjelma tuottaa seuraavan tulosteen:

```monospace
Koiria on nyt 2.
```

## Olioiden ja luokan välinen suhde

Edellä esitelty luokka voidaan esittää luokkakaaviona seuraavasti:

```mermaid
classDiagram
    class Koira {
        +nimi: str
        +syntymävuosi: int
        +haukahdus: str
        static tehty: int
        +__init__(nimi, syntymävuosi, haukahdus="Vuh-vuh")
        +hauku(kerrat)
    }
```

Ensimmäisessä osassa on luokan nimi, toisessa osassa on luokan ominaisuudet ja kolmannessa osassa on luokan metodit. Ominaisuuksien ja metodien eteen on merkitty näkyvyys: `+` tarkoittaa julkista (public) näkyvyyttä. Muuttujien näkyvyyttä emme tässä moduulissa käsittele enempää, mutta mainittakoon, että Pythonissa kaikki luokan jäsenet ovat oletuksena julkisia. Luokkamuuttuja `tehty` on merkitty sanalla `static`, joka tarkoittaa, että kyseessä on staattinen eli luokkamuuttuja.

Seuraavassa kaaviossa on esitetty, miten edellisen koodiesimerkin muuttujat, luokat ja oliot liittyvät toisiinsa:

```mermaid
flowchart LR
    %%classDef luokka fill:#f9f,stroke:#333,stroke-width:2px;
    %%classDef olio fill:#bbf,stroke:#333,stroke-width:1px;

    subgraph Muuttujat
        V1[koira1]
        V2[koira2]
    end

    L["Koira (luokka)" <br> tehty=2]:::luokka

    subgraph Oliot_ajonaikana
      O1((nimi='Muro' syntymävuosi=2018 haukahdus='Vuh-vuh')):::olio
      O2((nimi='Rekku' syntymävuosi=2022 haukahdus='Viu viu viu')):::olio
    end

    O1 -. instanssi .-> L
    O2 -. instanssi .-> L

    V1 --> O1
    V2 --> O2
```

Muuttujat `koira1` ja `koira2` viittaavat ajonaikaisiin olioihin, jotka on luotu Koira-luokasta. Nuo oliot puolestaan ovat Koira-luokan ilmentymiä eli instansseja. Luokkamuuttuja `tehty` kuuluu luokkaan, ei yksittäisiin olioihin.

Olioita ei siis tallenneta suoraan muuttujien "sisään", vaan muuttujat viittaavat olioihin (vrt. lista ja muut tietorakenteet). Muuttujat voivat siis olla erilaisia, mutta ne voivat viitata samaan olioon. Esimerkiksi voisimme kirjoittaa pääohjelmaan lauseen `koira3 = koira1`, jolloin muuttuja `koira3` viittaisi samaan olioon kuin `koira1`:

```mermaid
flowchart LR

    subgraph Muuttujat
        V1[koira1]
        V2[koira2]
        V3[koira3]
    end

    L["Koira (luokka)" <br> tehty=2]:::luokka

    subgraph Oliot_ajonaikana
      O1((nimi='Muro' syntymävuosi=2018 haukahdus='Vuh-vuh')):::olio
      O2((nimi='Rekku' syntymävuosi=2022 haukahdus='Viu viu viu')):::olio
    end

    O1 -. instanssi .-> L
    O2 -. instanssi .-> L

    V1 --> O1
    V3 --> O1
    V2 --> O2
```

Tällöin esimerkiksi lause `koira3.nimi` palauttaisi arvon `'Muro'`, koska `koira3` viittaa samaan olioon kuin `koira1`. Ja jos kirjoitetaan lause `koira3.nimi = "Musti"`, muuttuu `koira1`-olion nimi-ominaisuuden arvoksi `'Musti'`.

Jos kirjoitamme lauseen `koira2 = koira1`, kaikki muuttujat `koira1`, `koira2` ja `koira3` viittaavat samaan olioon, jolloin koiraan, jonka nimi on "Rekku", ei ole enää mitään viittausta. Tällöin tuo olio poistuu muistista, kun Pythonin roskienkeruu (*garbage collection*) siivoaa muistista olioita, joita ei enää ole käytössä:

```mermaid
flowchart LR
    classDef deleted fill:#aa0000,stroke:#333,stroke-width:2px,color:#fff;
    subgraph Muuttujat
        V1[koira1]
        V2[koira2]
        V3[koira3]
    end

    L["Koira (luokka)" <br> tehty=2]

    subgraph Oliot_ajonaikana
      O1((nimi='Musti' syntymävuosi=2018 haukahdus='Vuh-vuh'))
      O2((nimi='Rekku' syntymävuosi=2022 haukahdus='Viu viu viu')):::deleted
    end

    O1 -. instanssi .-> L
    O2 -. instanssi .-> L

    V1 --> O1
    V2 --> O1
    V3 --> O1
```


---

[Seuraavassa moduulissa käsitellään olioiden välisiä yhteyksiä ja keskinäistä vuorovaikutusta.](10_Assosiaatio.md)

---

<!-- add mermaid support for gh pages -->
<script type="module">
    Array.from(document.getElementsByClassName("language-mermaid")).forEach(element => {
      element.classList.add("mermaid");
    });
    import mermaid from 'https://cdn.jsdelivr.net/npm/mermaid@11/dist/mermaid.esm.min.mjs';
    mermaid.initialize({ startOnLoad: true });
</script>
