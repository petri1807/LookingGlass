# Looking Glass hologrammilasin opas kehittäjälle

![Looking Glass Factory logo](/Assets/lgf-logo.png)



## [Laitteeseen tutustuminen -](#laitteeseen-tutustuminen)

- [**Looking Glass Holographic Display**](#looking-glass-holographic-display)

- [**Kuka tämän oppaan kirjoitti**](#kuka-tämän-oppaan-kirjoitti)

- [**Kenelle tämä opas on tarkoitettu**](#kenelle-tämä-opas-on-tarkoitettu)

- [**Kytkennät**](#kytkennät)

- [**Tarvittavien sovellusten asennus**](#tarvittavien-sovellusten-asennus)

- [**Miten lasi toimii**](#miten-lasi-toimii)

## [Sovellukset -](#sovellukset)

- [**Lightfield Photo App**](#lightfield-photo-app)

  - [Quilt-kuvien teko Blenderillä](/lightfieldphotoapp.md)

- [**3D Model Importer**](#3d-model-importer)

  - [Tuetut tiedostomuodot](#tuetut-tiedostomuodot)
  
  - [Kontrollit](#kontrollit)
  
  - [Asetukset](#asetukset)

- [**Holoplay Unity SDK**](#holoplay-unity-sdk)

## Laitteeseen tutustuminen
Tässä osiossa käydään lyhyesti läpi mistä laitteesta on kyse, kenelle tämä opas on tarkoitettu ja kuka tämän oppaan on kirjoittanut. 

### Looking Glass Holographic Display

Looking Glass on Looking Glass Factoryn kehittämä hologramminäyttö joka huijaa katsojan näköaistia uskomaan että näytöllä esiteltävä sisältö on kolmiulotteista. Näytölle esitetään 45 eri kuvakulmaa kohteesta yhtäaikaisesti. Näytön pinnalla oleva polarisoiva filtteri näyttää kullekkin silmälle 3-5 kuvakulmaa vaihtelevalla voimakkuudella luoden sulavan illuusion kolmiulotteisesta kohteesta. Päätä liikutettaessa kohdetta voi tarkkailla vaakasuunnassa eri puolilta noin 40-50 asteen kulmassa. Hologrammilasista on tämän käsioppaan kirjotushetkellä (kesä 2020) saatavilla neljä versiota:

-	8.9” Development Kit (käytössä tämän oppaan kirjoittajalla)
-	15.6” Development Kit
-	15.6” Pro (sisältää integroidun tietokoneen ja sivulle aukeavan kosketusnäytön)
-	32” 8K Immersive Display
 
![Meet the lookinng glass](/Assets/meet-the-looking-glass.jpg)
*Looking Glass-laitteet vasemmalta alkaen: 8.9" / 15.6" / 32”*

### Kuka tämän oppaan kirjoitti
Hei, olen Petri, tietojenkäsittelyn toisen vuoden opiskelija, suuntauksena ohjelmistokehitys. Suoritin 15 opintopisteen (405h) harjoittelun 11/2019 - 08/2020 välisenä aikana Hämeen Ammattikorkeakoulun Smart-tutkimusyksikössä tutustuen hologrammilasin käyttöön ja sisällön kehitykseen.

### Kenelle tämä opas on tarkoitettu
Tämän käsikirjan tarkoitus on opastaa tulevia kehittäjiä tuomaan valmiita tai itse tehtyjä 3D-malleja hologrammilasille, sekä selvittää mitä asioita pitää ottaa huomioon omia malleja luodessa. Kehittäjältä odotetaan aiempaa kokemusta 3D-mallinnuksesta uutta sisältöä luodessa. Ohjelmistona käytössä Blender 2.83. Lataa uusin versio [blenderin kotisivuilta](https://blender.org) 

### Kytkennät
Laitteen liitännät ovat erittäin yksinkertaiset. Pakkauksessa tulee mukana yksi HDMI ja yksi USB-kaapeli. Näiden liitännät löytyvät lasin takapuolelta. Kun yhdistät nämä tietokoneeseen, avaa näytön asetukset ja asetaa Looking Glassin resoluutioksi 2560 x 1600 ja skaalaus 100%.
Joidenkin sovellusten kohdalla kolmen näytön käyttäminen samaan aikaan aiheutti ongelmia. Itselläni Lightfield Photo App ei suostunut avautumaan Looking Glassilla kolmantena näyttönä. Jos tällaista esiintyy kohdallasi, käy ottamassa näytön asetuksista toinen näyttö pois käytöstä, avaa sovellus lasille, ja tämän jälkeen voit ottaa toisen näytön uudelleen käyttöön.

### Tarvittavien sovellusten asennus
[DevTools](https://lookingglassfactory.com/devtools)-sivulta löytyvät kaikki viralliset lasille kehitetyt sovellukset sekä lisäosat.

[HoloPlay Service](https://lookingglassfactory.com/software/holoplay-service) täytyy asentaa jotta lasi toimii ja sille pystyy kehittämään sisältöä.

[Looking Glass Library](https://lookingglassfactory.com/devtools/looking-glass-library) on sovelluskirjasto josta löytyy muiden käyttäjien julkaisemia sovelluksia, ja sinne voi myös lisätä omia sovelluksia jos niitä haluaa jakaa julkisesti. 

[MadeWith](https://madewith.lookingglassfactory.com/)-sivulla pääset myös testaamaan muiden käyttäjien julkaisemia sovelluksia ja quilt-kuvia.  

#### Tässä oppaassa keskitymme seuraaviin sovelluksiin:
-	[3D Model Importer](https://lookingglassfactory.com/devtools/3d-model-importer)
-	[Lightfield Photo App](https://lookingglassfactory.com/devtools/lightfield-photo-app) 
-	[HoloPlay Unity SDK](https://lookingglassfactory.com/devtools/holoplay-unity-plugin)
-	[Leap Motion-liikkeentunnistusohjain](https://developer.leapmotion.com/setup/desktop)

### Miten lasi toimii
Hologrammilasin toiminta perustuu näytölle esitettävien 45 eri kuvakulman esittämisestä polarisoivan filtterin läpi, joka huijaa katsojan näköaistia havainnoimaan kolmiulotteisia objekteja lasin sisällä kahdella tavalla. 
-	Vaihtamalla katsojan näkökulmaa esitettävästä kohteesta vaakasuunassa
-	Esittämällä eri näkökulmia kullekkin silmälle

Alla oleva kuva havainnollistaa miten nämä 45 eri näkökulmaa esitetään lasille.
-	**Keskellä** Looking Glass lintuperspektiivistä. Laatikko esittää lasin sisällä olevaa tilaa. Lasiin yhdistyvät mustat viivat havainnollistavat mistä näkökulmasta vasemmalla ja oikealla esitettävä kuva näkyy.
-	Looking Glassin **sisällä** on kuvassa esitettävä 3D-malli, ja keskellä menee punaisella viivalla esitetty zero parallax plane.
-	**Oikealla** näkyy 2D-kuva jota kullekkin näkökulmalle esitetään. 
-	**Vasemmalla** näkyy kaikista 45 kuvasta muodostettu ”Quilt”, jossa punainen laatikko havainnollistaa myös mikä kuva mistäkin näkökulmasta katsottuna näkyy.

![Multiplex](/Assets/multiplex.gif)

Quilt tarkoittaa siis yhtä kuvatiedostoa jossa on tyypillisesti 5 kolumnia ja 9 riviä, yhteensä 45 itsenäistä kuvaa mallista eri kuvakulmista. Quiltin voi tehdä pienemmälläkin määrällä kuvia, mutta illuusion sulavuus kohdetta katsottaessa eri kuvakulmista saattaa kärsiä.

Tähän samaan toimintaan jokainen lasille kehitetty sovellus perustuu. Oli kyseessä sitten quilt-kuvien esitykseen tarkoitettu Lightfield Photo App, selaimella näytettävä sisältö tai Unity/Unreal pelimoottoreilla esitettävä interaktiivinen sisältö, kaikki nämä jakavat sisältönsä quilt-kuviin jotka sitten esitetään näytölle.

Quilt-kuva lasilla. Kameran linssille näkyy yhtäaikaisesti 5-6 kuvaa vaihtelevalla voimakkuudella. Tällöin lasia katsellessa kumpikin silmä näkee usean eri kuvan yhtäaikaisesti luoden sulavan kokemuksen päätä liikutettaessa sivulta toiselle. Syvyyssuunnassa lasin keskellä on ns. zero parallax plane, eli kohta jossa kohde on tarkimmillaan eikä liiku. Tämän kohdan takana ja edessä kohteen osat liikkuvat luoden kolmiulotteisen efektin.

![On LKG](/Assets/on-lkg.gif)

Aiheesta voi lukea lisää [How It Works](https://docs.lookingglassfactory.com/Appendix/how-it-works/)-sivulla. 


## Sovellukset

### Lightfield Photo App

Sovelluksen voi ladata osoitteesta https://lookingglassfactory.com/devtools/lightfield-photo-app

Lightfield Photo App toistaa lightfield-kuvia hologrammilasilla. Kuvasarjoja voi tehdä mistä tahansa 3D mallista, tai kuvata itse.
Quilt-kuvalla tarkoitetaan yhtä tiedostoa joka sisältää kaikki 32-45 kuvakulmaa 3D-mallista. Kuvasarjalla tarkoitetaan erillisiä kuvia joista voidaan rakentaa quilt.
Quilt-kuvien etuna on niiden kompakti koko sekä jaettavuuden helppous kun kyseessä on vain yksi tiedosto. Kuvasarjojen etuna taas on muokattavuus, eli kuvan kroppausta ja tarkennusta on mahdollista muuttaa. Kuvasarjoista voidaan tallentaa erillinen quilt-kuva. 

[**Quilt-kuvien teko Blenderillä**](/lightfieldphotoapp.md) osiosta löytyy ohjeet, jossa käydään läpi vaiheet miten omia quilt-kuvia voi tehdä helposti Blenderissä. Tähän voi käyttää mitä tahansa omaa tai netistä ladattua 3D mallia. Käytän esimerkkinä itse tekemääni Iittala Paratiisi-sarjan kahvimuki-mallia.

Ohjeeseen sisältyvät vaiheet:
-	Mallin tuominen blenderiin
-	Kameroiden asettelu
-	RenderBurst lisäosan asennus
-	Renderöinti
-	Kuvien tuonti Lightfield Photo Appiin
-	Kuvan rajaus ja tarkennus
-	Quiltin tallennus
- Denoiserin eli kohinan poistimen käyttö Cycles-rendermoottorilla

Hyvät puolet:
-	Realistisen sisällön tuottaminen suhteellisen helppoa jos 3D softat hallussa.
-	Ei rajoituksia mallin tai valaistuksen monimutkaisuuden puolesta.

Huonot puolet
-	Staattinen sisältö. Videoiden toisto ei ole mahdollista. 
-	Renderöintiin kuluva aika. 

### 3D Model Importer

Sovelluksen voi ladata osoitteesta https://lookingglassfactory.com/devtools/3d-model-importer

3D Model Importer mahdollistaa 3D mallin esittämisen hologrammilasilla helposti ja nopeasti. Mallia voi ohjailla hiirellä tai Leap Motion-liikeohjaimella. Valaistusta voi muokata itse melko rajallisesti. Käytössä on vain kaksi valonlähdettä, kohdistettu valo sekä ”ambient” valaistus.

#### Tuetut tiedostomuodot
| Tiedostopääte | Animaatiot |
|---|---|
| .glb | ✔ |
| .gltf | ✔ |
| .obj | ❌ |

#### Kontrollit

| Painike | Toiminto |
|---|---|
| Hiiren vasen | Pyöritä näkymää kiintopisteen ympäri |
| Hiiren rulla | Zoomaus lähemmäs/kauemmas |
| Hiiren oikea | Mallin liikuttaminen vaaka/pystysuunnassa |
| Hiiren vasen tuplaklikkaus | Aseta kiintopiste |
| Vasen/oikea nuolinäppäimet näytöllä tai näppäimistöllä | Edellinen/seuraava malli |
| Neliönäppäin näytöllä | Näyttää/piilottaa menun |
| Ympyränäppäin näytöllä | Pyöritä mallia |

#### Asetukset

![Asetukset-kuva](/Assets/importersettings.png)

| Nimi | Kuvaus |
|---|---|
| Load Model | Lataa malli |
| Remove Model | Poista malli |
| **OBJECT** |  |
| Metallic / Specular / Vertex Color | Shaderin valinta |
| Render Back Faces | Näyttää malleissa pinnat myös ns. väärätä puolelta. Jos valinta ei ole päällä, takapuolelta katsottuna pinnasta näkee läpi. Eli facen normal suunta määrittää tämän |
| Mesh Detail | Mallin tarkkuus prosentteina. Jos ohjelma pyörii heikosti raskaalla mallilla, aseta tähän pienempi luku ja paina SET |
| Glossiness | Mallin pinnan kiiltävyys asteikolla 0-1. Tämä korvataan Metallic ja Roughness arvoilla kun malli on ladattu |
| Jos tiedosto on .obj tähän väliin tulee tekstuurien lataukset | |
| Play Animation | Toista animaatio |
| Animation Speed | Animaation nopeus |
| **LIGHTING** | |
| Use backdrop | Käytä taustana valkoista seinää jos haluat varjojen heijastuvan pinnalle |
| Backdrop Distance | Taustan etäisyys mallista |
| Horizontal / Vertical Angle | Valon sijainti vaaka sekä pystyakselilla |
| Directional / Ambient Intensity | Valon voimakkuus kohdistettuna / ympäristöstä |
| POST-PROCESSING | |
| DoF / AO / Bloom Intensity | Depth of Field, Ambient Occlusion ja Bloom efektien voimakkuus |
| **QUALITY SETTINGS** | |
| Quilt Resolution | Resoluution säätö. 8K on raskain pyörittää mutta näyttää parhaalta |
| Optimization | Mallin optimointi. Joidenkin mallien kohdalla suorituskyky heikentyy tämän ollessa päällä. Käytä jos siitä on hyötyä | 
| Post-processing | Depth of Field, Ambient Occlusion ja Bloom efektien aktivointi |
| FPS-laskin | Kertoo kuinka hyvin kyseinen malli pyörii |
| Model Loading | Jos mallin tuominen epäonnistui sen suuren koon takia, aseta Timeout kohtaan suurempi arvo. Luku on 10–360 sekuntia kuinka kauan mallia sallitaan ladata |


### Holoplay Unity SDK

....
