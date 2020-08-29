# Quilt-kuvien teko Blenderillä

Tässä oppaassa käydään kädestä pitäen läpi vaiheet joilla voit itse luoda kuvasarjoja Lightfield Photo Appiin tuotavaksi, jossa niistä voi muokata ja tallentaa oman quilt-kuvan.

## Tarvittavat asennukset

- [**Blender**](https://blender.org) on ilmainen avoimen lähdekoodin 3D-ohjelmisto. Lataa uusin versio.
- [**RenderBurst**](https://github.com/VertStretch/RenderBurst) -lisäosa blenderiin, joka mahdollistaa useiden kuvien renderöinnin automatisoidusti.
- [**Lightfield Photo App**](https://lookingglassfactory.com/devtools/lightfield-photo-app) johon lopulta tuomme kuvat.

## Vaiheet
-	[**Mallin tuonti blenderiin**](#mallin-tuonti-blenderiin)
-	[**Kameroiden asettelu**](#kameroiden-asettelu)
-	[**RenderBurst lisäosan asennus**](#renderburst-lisäosan-asennus)
-	[**Renderöinti**](#renderöinti)
-	[**Kuvien tuonti Lightfield Photo Appiin**](#kuvien-tuonti-lightfield-photo-appiin)
-	[**Kuvan rajaus ja tarkennus**](#kuvan-rajaus-ja-tarkennus)
-	[**Quiltin tallennus**](#quiltin-tallennus)
-	[**Denoiserin eli kohinan poistimen käyttö Cycles-rendermoottorilla**](#denoiserin-eli-kohinan-poistimen-käyttö-cycles-rendermoottorilla)


## Mallin tuonti blenderiin

Ohjeet on järjestetty niin, että jokaisen kuvan alla on siihen liittyvät vaiheet.

![](https://github.com/petri1807/LookingGlass/blob/master/Assets/LightfieldPhotoApp/Dia3.JPG)
- Avaa Blender. Valitse kuutio (hiiren vasen) ja poista se (X, hiiren vasemmalla tai Enter vahvistat komennon)

![](https://github.com/petri1807/LookingGlass/blob/master/Assets/LightfieldPhotoApp/Dia4.JPG)
- Tuodaan Blenderiin oma malli. Avaa File -> Import -> ja valitse oikea tiedostomuoto

![](https://github.com/petri1807/LookingGlass/blob/master/Assets/LightfieldPhotoApp/Dia5.JPG)
- Valitse mallisi ja paina Import

## Kameroiden asettelu

![](https://github.com/petri1807/LookingGlass/blob/master/Assets/LightfieldPhotoApp/Dia6.JPG)
- Mallin ilmestyy Viewporttiin. Valitse kamera (hiiren vasen) ja avaa sivupaneeli (N)

![](https://github.com/petri1807/LookingGlass/blob/master/Assets/LightfieldPhotoApp/Dia7.JPG)
- Siirry Top Orthographic näkymään (Numpad 7) ja zoomaa kauemmas (hiiren rullaa alas)

![](https://github.com/petri1807/LookingGlass/blob/master/Assets/LightfieldPhotoApp/Dia8.JPG)
- Muuta sivupaneelista kameran Z-rotation arvo nollaksi (korostettu punaisella, valitse arvo hiiren vasemmalla ja syötä arvoksi 0)

![](/Assets/LightfieldPhotoApp/Dia9.JPG)
- Valitse Measure-työkalu. Tämä osio ei ole varsinaisesti tarpeellinen, mutta yritän tällä havainnollistaa optimaalisen 50° kulman, jolta kamerat mallia katsovat. Hologrammilasin katselukulma on noin 40-50°, joten kamera. 

![](/Assets/LightfieldPhotoApp/Dia10.JPG)
- Piirrä viivoittimella suora viiva vasemmalta oikealle (hiiren vasen), ja raahaa sitten viivan keskeltä (hiiren vasen) mallin päälle jolloin se muuttuu näyttämään kulman asteina. Raahaa molempia päitä niin, että ne ovat yhtä kaukana mallin molemmin puolin ja mittari näyttää 50°.

![](/Assets/LightfieldPhotoApp/Dia11.JPG)
- Siirrä kamera viivoittimen vasempaan reunaan (G, tai Move työkalupalkista)

![](/Assets/LightfieldPhotoApp/Dia12.JPG)
- Siirry kameranäkymään (Numpad 0). Jos mallisi on todella pieni, eikä näy viewportissa, laske kameraa alemmas Z-akselilla joko:
  - rahaamalla Z-location arvoa vasemmalle, kunnes malli tulee näkyviin
  - liikuttamalla kameraa (G), lukitsemalla siirron Z-akselille (Z) ja liikuttamalla hiirtä taakse.

![](/Assets/LightfieldPhotoApp/Dia13.JPG)
- Siirry kameranhallinta välilehdelle oikeasta laidasta ja muuta Focal Length-arvoa, kunnes malli on kameran näkymän rajojen sisällä.

![](/Assets/LightfieldPhotoApp/Dia14.JPG)
- Siirry takaisin Top Orthographic-näkymään (Numpad 7) ja tee linkitetty kopio kamerasta (Alt + D), lukita siirto X-akselille (X) ja siirrä kopiota hieman oikealle. Linkitetyllä kopiolla voimme myöhemmin muuttaa kameran asetuksia kuten Focal Length jolloin muutokset yhdessä kamerassa vaikuttavat kaikkiin kameroihin.

![](/Assets/LightfieldPhotoApp/Dia15.JPG)
- Toista viimeisin komento (Shift + R) kunnes sinulla on 45 kameraa. 
- Quilt-kuvia voi tehdä pienemmälläkin määrällä esim. testausta varten, mutta tällöin kokemus lasilla ei ole yhtä sulava.

![](/Assets/LightfieldPhotoApp/Dia16.JPG)
- Ensimmäinen kamera täytyy nimetä uudelleen, sillä myöhemmin, kun renderöimme nämä kaikki kuvakulmat, tiedostonimet määritetään kameroiden nimien mukaan. 
- Valitse vasemmalta ensimmäinen kamera, ja muuta sen nimeksi ”Camera.000” joko oikealta ylhäältä Outliner-paneelista, tai painamalla F2, joka avaa nimen muuttamisen.
- Nimeämällä kameran oikein se pysyy ensimmäinenä kuvana vasemmalta kun nämä tuodaan Lightfield Photo Appiin.

![](/Assets/LightfieldPhotoApp/Dia17.JPG)
- Korjataan kameroiden sijainnit. Ensimmäinen kamera on jo oikealla kohdalla, joten käytetään 3D kursoria apuna muiden siirtämiseen. Siirrä 3D kursori ensimmäisen kameran kohdalle (Shift + S, Cursor to Selected)

![](/Assets/LightfieldPhotoApp/Dia18.JPG)
- Vaihda Transform Pivot Point 3D kursoriksi. 

![](/Assets/LightfieldPhotoApp/Dia19.JPG)
- Valitse vasemmalta työkalupalkista Select Box ja valitse oikealta viimeinen kamera. Aseta se aktiiviseksi kameraksi painamalla oikealta ylhäältä Outlinerista kamerakuvaketta sen kohdalla. Valitse kaikki kamerat pitämällä hiiren vasenta pohjassa ja raahaamalla valintalaatikon kaikkien ylle.

![](/Assets/LightfieldPhotoApp/Dia20.JPG)
- Siirry aktiivisen kameran näkymään (Numpad 0) ja skaalaa kaikkia kameroita pienemmäksi (S, raahaa hiirtä vasemmalle) kunnes malli tulee kameran rajojen sisään.

![](/Assets/LightfieldPhotoApp/Dia21.JPG)
- Nyt jos siirrymme Top Orthographic-näkymään (Numpad 7) ja aktivoimme Measure-työkalun, niin kameroiden pitäisi olla noin 50° kulmassa malliin nähden.

## RenderBurst lisäosan asennus

Lataa [RenderBurst](https://github.com/VertStretch/RenderBurst) lisäosa Blenderiin. Linkistä löytyy ohjeet asennukseen.

RenderBurst helpottaa renderöintiä automatisoimalla usean kameran kuvan renderöinnin ja tallentamisen yhden napin painalluksen taakse. Säästät aikaa sekä hermojasi. Ilman RenderBurstia jokainen kuva tulisi yksitellen renderöidä, tallentaa kovalevylle numerojärjestykessä oikealla nimellä, ja aktiivista kameraa pitäisi vaihtaa seuraavaan.

## Renderöinti

![](/Assets/LightfieldPhotoApp/Dia22.JPG)
- Varmista että kohteesi on valaistu. Vaihda Shading mode renderöityyn tilaan (viewportin oikean yläkulman viimeinen kuvake, tai paina Z ja valitse Rendered). Testauksessa kannattaa käyttää Eevee-rendermoottoria. Tämän pitäisi olla normaalisti valittuna, mutta tarkista se silti Render Properties-välilehdeltä.

![](/Assets/LightfieldPhotoApp/Dia23.JPG)
- Render Burst vaatii tallennuskansion johon kuvat tallennetaan. Avaa Output Properties-välilehti ja valitse Output kohdasta kansio johon haluat kuvasi tallentaa. 

Täältä voi myös muuttaa resoluutiota. Helppo tapa renderöidä suuremmalla tai pienemmällä resoluutiolla on vaihtaa Resolution % arvoa. 

200% == 3840 x 2160

50% == 960 x 540 jne.

![](/Assets/LightfieldPhotoApp/Dia24.JPG)
- Nyt voimme renderöidä kaikki kuvat. Siirry Render Properties-välilehdelle, rullaa valikkoa alas kunnes löydät Render Burst valikon. Paina Render! ja kuvasi tallentuvat.

![](/Assets/LightfieldPhotoApp/Dia25.JPG)
- Kuvasarja on valmis tuotavaksi Lightfield Photo Appiin.

## Kuvien tuonti Lightfield Photo Appiin

![](https://github.com/petri1807/LookingGlass/blob/master/Assets/LightfieldPhotoApp/lpa_avaus.PNG)
- Avaa Lightfield Photo App
- Valitse oikea näyttö **Select Monitor** valikosta
- Ota **windowed**-valinta pois käytöstä
- Valitse **Screen**-valikosta resoluutioksi 2560 x 1600
- Paina Play!

![](/Assets/LightfieldPhotoApp/Dia26.JPG)
- Paina New Image, ja valitse Unnamed

![](/Assets/LightfieldPhotoApp/Dia27.JPG)
- Täältä voit lisätä kuvat valitsemalla Choose Photos

![](/Assets/LightfieldPhotoApp/Dia28.JPG)
- Valitse kaikki kuvat (Ctrl + A) ja avaa

## Kuvan rajaus ja tarkennus

![](/Assets/LightfieldPhotoApp/Dia29.JPG)
- Valitse Set Cropping. Täältä voit hallita leikkausta ja tarkennusta. 
- Raahaa kohdistusikkunaa painamalla ikkunan sisältä.
- Skaalaa ikkunan kokoa raahaamalla sinisistä nurkista. 
- Focus-sliderilla hallitset tarkennuksen kohtaa syvyyssunnassa, tai toisin sanoen Zero Parallax Planen sijaintia.
- Reverse Image kääntää kuvien järjestyksen jos nimeämis järjestys vahingossa menisi oikealta vasemmalle.

## Quiltin tallennus

![](/Assets/LightfieldPhotoApp/Dia30.JPG)
- Tallenna Quilt-kuva painamalla Save Quilt.

![](/Assets/LightfieldPhotoApp/quilt-esimerkki.jpg)
- Valmis Quilt näyttää tältä.

### Omia tuotoksiani.

![](https://github.com/petri1807/LookingGlass/blob/master/Assets/LightfieldPhotoApp/quilt-Iittalaparatiisi.jpg)
- Iittala Paratiisi-sarjan kahvimuki. Photogrammetrian avulla aidosta kahvikupista kaapattu tekstuuri.

![](https://github.com/petri1807/LookingGlass/blob/master/Assets/LightfieldPhotoApp/quilt-aaltovaasi.jpg)
- Iittala Aalto/savoy maljakko.

![](https://github.com/petri1807/LookingGlass/blob/master/Assets/LightfieldPhotoApp/quilt-ruusulaakso.jpg)
- Ruusulaakson paviljonki Aulangolla, Hämeenlinnassa. Kivijalka tehty photogrammetrialla, kaikki muu käsin.

![](https://github.com/petri1807/LookingGlass/blob/master/Assets/LightfieldPhotoApp/quilt-karhuluola.jpg)
- Karhut-patsas Aulangolla, Hämeenlinnassa. Photogrammetrialla tehty malli. 


Quilt-kuvia voi avata menemällä Quilts-välilehdelle. Quilt kuvien avaus on huomattavasti nopeampaa, mutta muokkaus ei enää onnistu.

Quilt-kuvia käyttämällä mallin teossa ei tarvitse murehtia vertexien määrästä tai muista rajoitteista. 

Parhaan tuloksen Blenderissä saa käyttämällä Cycles-rendermoottoria joka tuottaa realistisen path tracing valaistuksen. Tämä kuitenkin vie huomattavasti enemmän aikaa renderöinnissä, jonka takia denoiserin käyttö on suositeltavaa

## Denoiserin eli kohinan poistimen käyttö Cycles-rendermoottorilla

![](/Assets/LightfieldPhotoApp/Dia31.JPG)
**Intel Open Image Denoiserin käyttö**
- Varmista että Render Engine on Cycles.
- Jos koneessasi on erillinen näytönohjain, valitse Device kohdasta GPU Compute.
- Sampling-menusta voit hallita sample määrää. Render valmiille kuvalle, Viewport livenä editorissa. Enemmän sampleja == parempi laatu mutta vie enemmän aikaa.

![](/Assets/LightfieldPhotoApp/Dia32.JPG)
- Siirry Layer Properties-välilehdelle ja valitse Denoising Data 

![](/Assets/LightfieldPhotoApp/Dia33.JPG)
- Siirry Compositing-workspaceen ylhäältä
- Valitse Use Nodes

![](/Assets/LightfieldPhotoApp/Dia34.JPG)
- Lisää Filter -> Denoise node ja raahaa se Render Layers ja Composite nodejen väliin
- Renderöi kuva. Vasen yläkulma, Render -> Render Image

![](/Assets/LightfieldPhotoApp/Dia35.JPG)
- Yhdistä node kuten kuvassa, eli korvaa Image yhteys Noisy Imagella, ja yhdistä Denoising Normal -> Normal sekä Denoising Albeido -> Albeido
- Valmis. Voit tarkastella eroa vaihtamalla Composite nodeen yhdistyvää lähdettä.

### Denoiser vertailu
![](/Assets/LightfieldPhotoApp/Dia36.JPG)


Denoisen ollessa käytössä jokainen kuva käy filtterin läpi ennen tallennusta. RenderBurstilla renderöidän tämä siis tarvitsee tehdä vain kerran, ja kaikki kuvat käsitellään automaattisesti.

Denoise toimii pelkästään Cyclesin kanssa. Jos käytät Eevee-rendermoottoria muista muuttaa Render Layers-Composite yhteys alkuperäiseen muotoon tai ota Use Nodes pois päältä.

Käytettävien samplejen määrä on laadun ja nopeuden tasapainottelua. Yksinkertaisissa kohteissa voidaan käyttää hyvin matalia lukuja ilman että laatu kärsii huomattavasti. Lasi jonka läpi heijastetaan valoa on hyvä esimerkki kohteesta joka saattaa vaatia verrattaen suuren määrän sampleja näyttääkseen hyvältä.
