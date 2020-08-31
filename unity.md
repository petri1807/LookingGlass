# Oman Unity-sovelluksen teko

Tässä osiossa käymme läpi vaiheet jotta onnistut tekemään ensimmäisen Unityllä kehitetyn sovelluksesi Looking Glassille.

## Vaiheet
- [**Projektin luonti**](#projektin-luonti)
- [**Tuo Holoplay SDK projektiisi**](#tuo-holoplay-sdk-projektiisi)
- [**Lisää Holoplay Capture ja mallit**](#lisää-holoplay-capture-ja-mallit)
- [**Lisää sovellukseen toiminnallisuutta**](#lisää-sovellukseen-toiminnallisuutta)
- [**Rakenna sovelluksesta executable versio**](#rakenna-sovelluksesta-executable-versio)
- [**Leap Motion + Unity**](#leap-motion--unity)

## Tarvittavat lataukset

- [**Unity**](https://store.unity.com/#plans-individual)-pelimoottori. Rekisteröidy, valitse Personal tai Student lisenssi, ja lataa Unity (2017.4 tai uudempi).
- [**Holoplay Unity SDK**](https://lookingglassfactory.com/devtools/holoplay-unity-plugin) plugin.

### Projektin luonti

![](/Assets/unity/Capture1.PNG)
- Avaa Unity
- Valitse NEW
- Valitse 3D template
- Nimeä projekti ja valitse tallennuskansio
- Paina Create

### Tuo Holoplay SDK projektiisi

![](/Assets/unity/Capture2.PNG)
- Tuo HoloPlay SDK projektiin valikosta Assets -> Import Package -> Custom Package

![](/Assets/unity/Capture3.PNG)
- Etsi lataamasi HoloplaySDK-1.3.1.unitypackage tiedosto
- Paina Open

![](/Assets/unity/Capture4.PNG)
- Import Unity Package ikkunasta voit valita mitä haluat paketista tuoda projektiisi
- Paina Import

![](/Assets/unity/Capture5.PNG)
- Unity ehdottaa käyttämään tiettyjä projektiasetuksia Holoplayn kanssa.
- Paina Apply Changes

### Lisää Holoplay Capture ja mallit

![](/Assets/unity/Capture6.png)
- Poista Main Camera

![](/Assets/unity/Capture7.png)
- Lisää Holoplay Capture Hierarchy-ikkunaan, hiiren oikea -> Holoplay Capture

![](/Assets/unity/Capture8.png)
- Lisää Project-ikkunaan uusi kansio malleille, hiiren oikea -> Create -> Folder.
- Tuo mallisi tänne, hiiren oikea -> Import New Asset.

![](/Assets/unity/Capture9.PNG)
- Valitse mallisi ja tekstuurit jos niitä on.

![](/Assets/unity/Capture10.PNG)
- Raahaa mallisi Hierachy-ikkunaan.
- Korjaa kohteen koko ja sijainti niin, että se mahtuu Holoplay Capturen sisään.
- Holoplay Capturen sisällä oleva violetti kohta on ns. Zero Parallax Plane jossa kohteet ovat tarkimmillaan.
- Testaa lasilla livenä painamalla Ctrl + E, tai yläpalkista Holoplay -> Toggle Preview, tai Inspector ikkunasta Holoplay Capture valittuna Toggle Preview.
- Jos mitään ei ilmesty lasille, tarkista että Target Display on asetettu oikein.

### Lisää sovellukseen toiminnallisuutta

![](/Assets/unity/Capture11.png)
- Lisätään sovellukseen skripti jolla voimme ohjata Holoplay Capturea. Pystymme liikuttamaan kameraa, zoomaamaan sisään ja ulos, vaihtamaan kiintopistettä ja niin edelleen.
- Valitse Holoplay Capture.
- Mene Project-ikkunassa Holoplay/Scripts kansioon.
- Raahaa OrbitControl-tiedosto Inspector ikkunaan Add Componentin alle, eli yhdistä skripti Holoplay Captureen.
- Mene Holoplay/Prefabs kansioon.
- Raahaa 3D Cursor prefab Hierarchy-ikkunaan.
- Tutustu tarkemmin OrbitControl-skriptiin osoitteessa https://docs.lookingglassfactory.com/Unity/Scripts/OrbitControl/

### Rakenna sovelluksesta executable versio

![](/Assets/unity/Capture12.png)
- Valitse Holoplay Capture, ja avaa Inspector ikkunasta Quilt Settings.
- Valitse resoluutio asetus jota haluat käyttää. Tämä ei vaikuta preview-näkymään.

![](/Assets/unity/Capture13.png)
- Rakennetaan sovelluksestasi ajettava versio. Mene ylävalikosta File -> Build Settings.

![](/Assets/unity/Capture14.png)
- Valite alusta jolle haluat sovelluksesi rakentaa, ja paina Build.
- Valitse kansio johon tiedostot tallennetaan.

![](/Assets/unity/Capture15.png)
- Nyt voit ajaa sovelluksesi .exe-tiedostosta.

### Leap Motion + Unity

[Looking Glassin ohjeistus](https://docs.lookingglassfactory.com/Unity/Leap/) Leap Motionin käyttöön Unityssä.

Leap Motionin [Unity Modules](https://leapmotion.github.io/UnityModules/index.html)-sivulta löytyy erittäin kattava ohjeistus ohjaimen käyttöön Unityssä.

[Leap Motion ajuri](https://developer.leapmotion.com/setup/desktop)
[Leap Motion Unity Core Assets](https://github.com/leapmotion/UnityModules/releases/tag/Release-CoreAsset-4.4.0) paketti Unityyn.
[Looking Glassin demopaketista](http://docfiles.lookingglassfactory.com/LKG%2BLEAP.unitypackage) löytyy esimerkki Leap Motionin käyttämiseen.
