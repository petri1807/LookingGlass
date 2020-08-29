# Lightfield Photo App

Tässä oppaassa käydään kädestä pitäen läpi vaiheet joilla voit itse luoda kuvasarjoja Lightfield Photo Appiin tuotavaksi, jossa niistä voi muokata ja tallentaa oman quilt-kuvan.

### Tarvittavat asennukset

- [**Blender**](https://blender.org) on ilmainen avoimen lähdekoodin 3D-ohjelmisto. Lataa uusin versio.
- [**RenderBurst**](https://github.com/VertStretch/RenderBurst) -lisäosa blenderiin, joka mahdollistaa useiden kuvien renderöinnin automatisoidusti.
- [**Lightfield Photo App**](https://lookingglassfactory.com/devtools/lightfield-photo-app) johon lopulta tuomme kuvat.

### Vaiheet
-	Mallin tuonti blenderiin
-	Kameroiden asettelu
-	Valaistuksen säätö
-	RenderBurst lisäosan asennus
-	Renderöinti
-	Kuvien tuonti Lightfield Photo Appiin
-	Kuvan rajaus ja tarkennus
-	Quiltin tallennus
-	Protip: Denoiserin eli kohinan poistimen käyttö Cycles-rendermoottorilla

![](https://github.com/petri1807/LookingGlass/blob/master/Assets/LightfieldPhotoApp/Dia3.JPG)
- Avaa Blender. Valitse kuutio (hiiren vasen) ja poista se (X, hiiren vasemmalla tai Enter vahvistat komennon)

![](https://github.com/petri1807/LookingGlass/blob/master/Assets/LightfieldPhotoApp/Dia4.JPG)
- Tuodaan Blenderiin oma malli. Avaa File -> Import -> ja valitse oikea tiedostomuoto

![](https://github.com/petri1807/LookingGlass/blob/master/Assets/LightfieldPhotoApp/Dia5.JPG)
- Valitse mallisi ja paina Import

![](https://github.com/petri1807/LookingGlass/blob/master/Assets/LightfieldPhotoApp/Dia6.JPG)
- Mallin ilmestyy Viewporttiin. Valitse kamera (hiiren vasen) ja avaa sivupaneeli (N)

![](https://github.com/petri1807/LookingGlass/blob/master/Assets/LightfieldPhotoApp/Dia7.JPG)
- Siirry Top Orthographic näkymään (Numpad 7) ja zoomaa kauemmas (hiiren rullaa alas)

![](https://github.com/petri1807/LookingGlass/blob/master/Assets/LightfieldPhotoApp/Dia8.JPG)
- Muuta sivupaneelista kameran Z-rotation arvo nollaksi (korostettu punaisella, valitse arvo hiiren vasemmalla ja syötä arvoksi 0)

![]()
- Valitse Measure-työkalu. Tämä osio ei ole varsinaisesti tarpeellinen, mutta yritän tällä havainnollistaa optimaalisen 50° kulman jolta kamerat mallia katsovat. Hologrammilasin katselukulma on noin 40-50° joten yritetään pysyä samoilla linjoilla.

![]()
- Piirrä viivoittimella suora viiva vasemmalta oikealle (hiiren vasen), ja raahaa sitten viivan keskeltä (hiiren vasen) mallin päälle jolloin se muuttuu näyttämään kulman asteina. Raahaa molempia päitä niin että ne ovat yhtä kaukana mallin molemmin puolin ja mittari näyttää 50°

![]()
- Siirrä kamera viivoittimen vasempaan reunaan (G, tai Move työkalupalkista)

![]()
- Siirry kameranäkymään (Numpad 0). Jos malli ei näy viewportissa syystä että se on todella pieni, laske kameraa alemmas Z-akselilla joko raahaamalla Z-location arvoa vasemmalle kunnes malli tulee näkyviin tai liikuttamalla kameraa (G), lukitsemalla siirron Z-akselille (Z) ja liikuttamalla hiirtä taakse.

![]()
- Siirry kameranhallinta välilehdelle oikeasta laidasta ja muuta Focal Length-arvoa kunnes malli on kameran näkymän rajojen sisällä. Tämä arvo on kameroiden kulman kanssa tärkeä osa sitä miten malli esiintyy hologrammilasilla.

![]()
- Siirry takaisin Top Orthographic-näkymään (Numpad 7) ja tee linkitetty kopio kamerasta (Alt + D), lukita siirto X-akselille (X) ja siirrä kopiota hieman oikealle. Linkitetyllä kopiolla voimme myöhemmin muuttaa kameran asetuksia kuten Focal Length jolloin muutokset yhdessä kamerassa vaikuttavat kaikkiin kameroihin.

![]()
- Toista viimeisin komento (Shift + R) kunnes sinulla on 45 kameraa. 
Quilt-kuvia voi tehdä pienemmälläkin määrällä esim. testausta varten, mutta tällöin kokemus lasilla ei ole yhtä sulava.

![]()
- Ensimmäinen kamera täytyy nimetä uudelleen sillä myöhemmin kun renderöimme nämä kaikki kuvakulmat, tiedostonimet määritetään kameroiden nimien mukaan. Muuta oikealta ylhäältä Outliner-paneelista ”Camera”-objektin nimeksi ”Camera.000”. Tällöin se pysyy ensimmäinenä kuvana vasemmalta kun nämä tuodaan Lightfield Photo Appiin.

![]()
- Korjataan kameroiden sijainnit. Ensimmäinen kamera on jo oikealla kohdalla, joten käytetään 3D kursoria apuna muiden siirtämiseen. Siirrä 3D kursori ensimmäisen kameran kohdalle (Shift + S, Cursor to Selected)

![]()
- Vaihda Transform Pivot Point 3D kursoriksi. 

![]()
- Valitse vasemmalta työkalupalkista Select Box ja valitse oikealta viimeinen kamera. Aseta se aktiiviseksi kameraksi painamalla oikealta ylhäältä Outlinerista kamerakuvaketta sen kohdalla. Valitse kaikki kamerat pitämällä hiiren vasenta pohjassa ja raahaamalla valintalaatikon kaikkien ylle.

![]()
- Siirry aktiivisen kameran näkymään (Numpad 0) ja skaalaa kaikkia kameroita pienemmäksi (S, raahaa hiirtä vasemmalle) kunnes malli tulee kameran rajojen sisään.

![]()
- Nyt jos siirrymme Top Orthographic-näkymään (Numpad 7) ja aktivoimme Measure-työkalun, niin kameroiden pitäisi olla noin 50° kulmassa malliin nähden.

Lataa [Render Burst](https://github.com/VertStretch/RenderBurst) lisäosa Blenderiin. Linkistä löytyy ohjeet asennukseen.

Render Burst helpottaa renderöintiä automatisoimalla usean kameran kuvan renderöinnin ja tallentamisen yhden napin painalluksen taakse. Säästät aikaa sekä hermojasi. Ilman Render Burstia jokainen kuva tulisi yksitellen renderöidä, tallentaa kovalevylle numerojärjestykessä oikealla nimellä, ja aktiivista kameraa pitäisi vaihtaa seuraavaan.


![]()
- Varmista että kohteesi on valaistu. Vaihda Shading mode renderöityyn tilaan (viewportin oikean yläkulman viimeinen kuvake, tai paina Z ja valitse Rendered). Testauksessa kannattaa käyttää Eevee-rendermoottoria. Tämän pitäisi olla normaalisti valittuna, mutta tarkista se silti Render Properties-välilehdeltä.

![]()
- Render Burst vaatii tallennuskansion johon kuvat tallennetaan. Avaa Output Properties-välilehti ja valitse Output kohdasta kansio johon haluat kuvasi tallentaa. Täältä voi myös muuttaa resoluutiota. Helppo tapa renderöidä suuremmalla tai pienemmällä resoluutiolla on vaihtaa Resolution % arvoa. 200% == 3840 x 2160, 
50% == 960 x 540 jne.

![]()
- Nyt voimme renderöidä kaikki kuvat. Siirry Render Properties-välilehdelle, rullaa valikkoa alas kunnes löydät Render Burst valikon. Paina Render! ja kuvasi tallentuvat.

![]()
- Kuvasarja on valmis tuotavaksi Lightfield Photo Appiin.

![]()
- Paina New Image, ja valitse Unnamed

![]()
- Täältä voit lisätä kuvat valitsemalla Choose Photos

![]()
- Valitse kaikki kuvat (Ctrl + A) ja avaa

![]()
- Valitse Set Cropping. Täältä voit hallita leikkausta ja tarkennusta. Raahaa kohdistusikkunaa painamalla ikkunan sisältä, skaalaa ikkunan kokoa raahaamalla sinisistä nurkista. Focus-sliderilla hallitset tarkennuksen kohtaa syvyyssunnassa. Reverse Image kääntää kuvat jos kuvien järjestys vahingossa menisi oikealta vasemmalle.

![]()
- Tallenna Quilt-kuva painamalla Save Quilt.

Valmis Quilt näyttää tältä.

Näitä voi avata samaan tapaan kun kuvasarjoja menemällä Quilts-osioon Lightfield Photo Appissa, mutta muokkaus ei enää onnistu.

Quilt-kuvia käyttämällä mallin teossa ei tarvitse murehtia vertexien määrästä tai muista rajoitteista. 

Parhaan tuloksen Blenderissä saa käyttämällä Cycles-rendermoottoria joka tuottaa realistisen path tracing valaistuksen. Tämä kuitenkin vie huomattavasti enemmän aikaa renderöinnissä, jonka takia denoiserin käyttö on suositeltavaa

![]()
- Intel Open Image Denoiserin käyttö
Varmista että Render Engine on Cycles.
Jos koneessasi on erillinen näytönohjain, valitse Device kohdasta GPU Compute.
Sampling-menusta voit hallita sample määrää. Render valmiille kuvalle, Viewport livenä editorissa. Enemmän sampleja == parempi laatu mutta vie enemmän aikaa.


![]()
- Siirry Layer Properties-välilehdelle ja valitse Denoising Data 

![]()
- 5. Siirry Compositing-workspaceen ylhäältä
6. Valitse Use Nodes

![]()
- 7. Lisää Filter  Denoise node ja raahaa se Render Layers ja Composite nodejen väliin
8. Renderöi kuva. Vasen yläkulma, Render  Render Image


![]()
- 9. Yhdistä node kuten kuvassa, eli korvaa Image yhteys Noisy Imagella, ja yhdistä Denoising Normal  Normal sekä Denoising Albeido  Albeido
10. Valmis. Voit tarkastella eroa vaihtamalla Composite nodeen yhdistyvää lähdettä.


![]()
- 

Denoisen ollessa käytössä jokainen kuva käy filtterin läpi ennen tallennusta. Tämä siis tarvitsee tehdä vain kerran.

Denoise toimii pelkästään Cyclesin kanssa. Jos käytät Eevee-rendermoottoria muista muuttaa Render Layers-Composite yhteys alkuperäiseen (Dia 36) tai ota Use Nodes pois päältä.

Käytettävien samplejen määrä on laadun ja nopeuden tasapainottelua. Yksinkertaisissa kohteissa voidaan käyttää hyvin matalia lukuja ilman että laatu kärsii huomattavasti. Lasi jonka läpi heijastetaan valoa on hyvä esimerkki kohteesta joka saattaa vaatia verrattaen suuren määrän sampleja näyttääkseen hyvältä.
