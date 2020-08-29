# Looking Glass hologrammilasin opas kehittäjälle

![Logo](/Assets/lgf-logo.png)



[**Johdanto**](https://github.com/petri1807/LookingGlass#johdanto)

[**Kenelle tämä opas on tarkoitettu**](https://github.com/petri1807/LookingGlass#kenelle-t%C3%A4m%C3%A4-opas-on-tarkoitettu)



## Johdanto
Tässä osiossa käydään lyhyesti läpi mistä laitteesta on kyse, kenelle tämä opas on tarkoitettu ja kuka tämän oppaan on kirjoittanut. 

Looking Glass on Looking Glass Factoryn kehittämä hologramminäyttö joka huijaa katsojan näköaistia uskomaan että näytöllä esiteltävä sisältö on kolmiulotteista. Näytölle esitetään 45 eri kuvakulmaa kohteesta yhtäaikaisesti. Näytön pinnalla oleva polarisoiva filtteri näyttää kullekkin silmälle 3-5 kuvakulmaa vaihtelevalla voimakkuudella luoden sulavan illuusion kolmiulotteisesta kohteesta. Päätä liikutettaessa kohdetta voi tarkkailla vaakasuunnassa eri puolilta noin 40-50 asteen kulmassa. Hologrammilasista on tämän käsioppaan kirjotushetkellä (kesä 2020) saatavilla neljä versiota:

-	8.9” Development Kit (käytössä tämän oppaan kirjoittajalla)
-	15.6” Development Kit
-	15.6” Pro (sisältää integroidun tietokoneen ja sivulle aukeavan kosketusnäytön)
-	32” 8K Immersive Display
 
![Kuva 1](/Assets/meet-the-looking-glass.jpg)
*Looking Glass-laitteet vasemmalta alkaen: 8.9" / 15.6" / 32”*

## Kenelle tämä opas on tarkoitettu
Tämän käsikirjan tarkoitus on opastaa tulevia kehittäjiä tuomaan valmiita tai itse tehtyjä 3D-malleja hologrammilasille, sekä selvittää mitä asioita pitää ottaa huomioon omia malleja luodessa. Kehittäjältä odotetaan aiempaa kokemusta 3D-mallinnuksesta uutta sisältöä luodessa. Ohjelmistona käytössä Blender 2.83. Lataa uusin versio [blenderin kotisivuilta](https://blender.org) 

## Kytkennät
Laitteen liitännät ovat erittäin yksinkertaiset. Pakkauksessa tulee mukana yksi HDMI ja yksi USB-kaapeli. Näiden liitännät löytyvät lasin takapuolelta. Kun yhdistät nämä tietokoneeseen, avaa näytön asetukset ja asetaa Looking Glassin resoluutioksi 2560 x 1600 ja skaalaus 100%.
Joidenkin sovellusten kohdalla kolmen näytön käyttäminen samaan aikaan aiheutti ongelmia. Itselläni Lightfield Photo App ei suostunut avautumaan Looking Glassilla kolmantena näyttönä. Jos tällaista esiintyy kohdallasi, käy ottamassa näytön asetuksista toinen näyttö pois käytöstä, avaa sovellus lasille, ja tämän jälkeen voit ottaa toisen näytön uudelleen käyttöön.

## Tarvittavien sovellusten asennus
[DevTools](https://lookingglassfactory.com/devtools)-sivulta löytyvät kaikki viralliset lasille kehitetyt sovellukset sekä lisäosat. 
[HoloPlay Service](https://lookingglassfactory.com/software/holoplay-service) täytyy asentaa jotta lasi toimii ja sille pystyy kehittämään sisältöä.
Looking Glass Librarysta pääset asentamaan muiden käyttäjien julkaisemia sovelluksia. [MadeWith](https://madewith.lookingglassfactory.com/)-sivulla pääset myös testaamaan muiden käyttäjien julkaisemia sovelluksia ja quilt-kuvia.  

Tässä oppaassa keskitymme seuraaviin sovelluksiin:
-	3D Model Importer
-	Lightfield Photo App 
-	HoloPlay Unity SDK
-	Leap Motion-kontrolleri 
