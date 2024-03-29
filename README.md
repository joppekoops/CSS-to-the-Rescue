# CSS-to-the-Rescue
Dit is een opdracht voor het vak 'CSS to the Rescue' van de minor 'Web Design & Development': https://everythingweb.org/

Bekijk mijn resultaat op: https://joppekoops.github.io/CSS-to-the-Rescue/
Dit werkt op dit moment alleen in Chrome met de Experimental Web Platform features aan!


## ⏩️ Snelle samenvatting door chatGPT
Hieronder volgt een overzicht van het proces en de gebruikte technieken:

### Proces
- **Opdrachtkeuze**: De keuze viel op het *control panel*, waarbij inspiratie werd gehaald uit een live videomixer.
- **Ideeontwikkeling**: Belangrijke elementen waren onder meer de *joystick* en een *slider* voor video-overgangen.
- **Voortgangsupdates**: Er werden regelmatige updates gegeven over de voortgang en de uitdagingen die werden aangepakt.
- **Functionaliteit implementatie**: De *joystick* werd ontwikkeld met 8 richtingen en bijbehorende animaties voor interactie.

### Belangrijkste Technieken
- **3D-effecten**: Door gebruik te maken van CSS-transforms en perspectief-effecten werd een 3D-uitstraling gecreëerd.
- **Gradients voor belichting**: Subtiele gradients werden toegepast om een realistisch belichtingsmodel te simuleren.
- **Berekeningen met sinus en cosinus**: Om een cilindervormig 'steeltje' voor de *joystick* te maken werden trigonometrische functies gebruikt.
- **CSS @layer**: Verschillende lagen werden gebruikt voor reset-stijlen, standaard stijlen, layout, thema's en componenten, hoewel dit in dit geval minder noodzakelijk bleek.

De documentatie biedt een diepgaand inzicht in het ontwikkelingsproces en de technische uitdagingen bij het creëren van een interactieve videomixer met alleen HTML en CSS.

### Belangrijkste leerpunten:
- **3D-effect en belichting**: Gebruik van geavanceerde CSS-technieken voor het creëren van een realistisch 3D-effect, met bijzondere aandacht voor belichting met gradients.
- **Structurering van code**: Inzicht verkregen in het structureren van CSS-code door het gebruik van @layers en nesting, waardoor de codebase georganiseerd werd en complexiteit verminderd werd.
- **Oplossingen voor conflicten**: Het vinden van oplossingen voor conflicten tussen animaties en opmaak, met name bij de titel van de mixer, vereiste het sluiten van compromissen om de gewenste opmaak te behouden.
- **Praktische toepassing van complexe CSS**: Toepassing van complexe CSS-vereisten, zoals het ontwerpen van de joystick en het schrijven van uitgebreide selectoren voor dubbele interacties, droeg bij aan een beter begrip van CSS-architectuurtechnieken en de creatieve mogelijkheden van CSS.



## 👨‍🏫 De opdracht
Voor het vak kon ik kiezen uit 4 verschillende opdrachten: Vuurwerk, *Control panel*, Rubik's kubus of papieren vliegtuig. Dit moest worden uitgewerkt door alleen gebruik te maken van HTML en CSS.

Ik heb voor het *control panel* gekozen, waarbij ik een bestaande control panel heb uitgezocht, waarvan ik delen ga nameken met CSS. Het *control panel* moet interactief zijn, met duidelijke *controls*, *states* en *feedback*. Bovendien moet het daadwerkelijk iets aansturen.

## 💡 Mijn Idee
Voor mijn opdracht gebruik ik de volgende live video mixer als inspiratie voor mijn digitale control panel:

| ![Panasonic video mixer](./readme-images/video-mixer_1.webp) | ![Panasonic video mixer top view](./readme-images/video-mixer_2.webp) |
| --- | --- |
| Panasonic video mixer | Panasonic video mixer top view |

Het interessantste aan deze mixer vind ik de *joystick*. Daar ga ik dan ook mee beginnen. Deze zou een simpel element in het schermpje van de mixer kunnen bedienen, wat van links naar rechts en van boven naar beneden kan bewegen.

| ![Schets van de joystick op de controller](./readme-images/joystick-schets.webp) |
| --- |
| Schets van de *joystick* op de *controller* |

Als een volgende stap zou ik de *slider* kunnen maken die de overgang tussen beelden regelt. Of dat ook echt gaat gebeuren weet ik nog niet. In ieder geval kunnen de lampjes er naast wel aan of uit. De video-overgang zou simpel kunnen door de *opacity* van het ene of het andere video-element te animeren.

| ![Schets van de overgang slider](./readme-images/overgang-slider-schets.webp) |
| --- |
| Schets van de overgang *slider* |

Later kan ik altijd nog andere elementen toevoegen zoals de draaiknopjes, die bijvoorbeeld de grootte van het element kunnen aanpassen.



## 👨‍💻 Voortgang 1 (01-03-2024)
Vandaag hebben we onze ideeën doorgesproken. Daaruit kwamen een aantal vragen en tips om te kunnen beginnen.

- Wil je dat de *joystick* weer teruggaat naar het midden of dat de *joystick* blijft staan in de positie waarin je die zet?
- Je kan de *joystick* laten werken met een aantal *buttons* eromheen. Sanne had een [voorbeeld](https://codepen.io/shooft/pen/BaEabXy) van een *D-pad* die zo werkt. Voor een *joystick* zijn er natuurlijk meer mogelijkheden voor richtingen dan 4.
- Het blokje kan je een animatie geven voor helemaal van links naar rechts. Die kan je vervolgens op pauze te zetten als er niets wordt ingedrukt en voorwaarts of achterwaarts afspelen als de *joystick* naar links of rechts gaat. Ditzelfde kan dan voor naar boven en beneden. Je kan tegenwoordig twee animaties op één element zetten, of je kan er nog een *div*-element omheen zetten.

Jop maakt toevallig ook een *joystick*, hoewel hij juist wil dat de *joystick* blijft staan als je die loslaat. Dat gaat waarschijnlijk werken met een verticale en een horizontale *slider*.



## 🕹️ De *joystick* maken

### ⚙️ Werking
| ![Joystick met 8 buttons er omheen](./readme-images/joystick.webp) |
| --- |
| *Joystick* met 8 buttons er omheen |

De manier waarop de *joystick* werkt is dat er 8 *buttons* omheen zitten voor 8 mogelijke richtingen. Wanneer je ergens op de *joystick* klikt en over een van de buttons hovert, kan er vervolgens wat gebeuren. Dit doe ik met de volgende CSS-selector:

```css
body:has(section:nth-of-type(2) div:nth-of-type(1):active):has(section:nth-of-type(2) div:nth-of-type(1) button:nth-child(4):hover)
```

Het is een lange, maar dit zorgt ervoor dat je ook op de *joystick* kan klikken en vervolgens slepen over een van de buttons. Als de *body* een *div*-element heeft dat wordt ingeklikt en daarin een *button* heeft die wordt gehoverd, kan er vervolgens overal in de *body* wat gebeuren. Gewoon op de buttons klikken werkt op deze manier ook. De *joystick* verplaats ik vervolgens in de richting van de button.

Het **maken van het bewegende blokje** ging wat lastiger. Het idee was dat die een gepauzeerde animatie had die weer af zou spelen als de *joystick* gebruikt wordt. Als het blokje een animatie naar beneden en naar rechts had, zou die ook naar boven en naar links kunnen bewegen door de `animation-direction` op `reverse` te zetten.

Hierbij ontstonden een aantal problemen:

1. Je kan tegenwoordig **meerdere animaties op een element** zetten, maar niet als deze dezelfde *property* animeren. Nou blijkt dat `translateX()` en `translateY()` wel als een dezelfde gelden. Dit was snel opgelost door er nog een *div*je omheen te zetten met de andere animatie.
2. Wanneer een ***reversed* animatie gepauzeerd** wordt en de *reverse* er af wordt gehaald springt die naar de positie waar die zou zijn als de animatie niet *reversed* was afgespeeld.

**Dit werkt:**

https://github.com/joppekoops/CSS-to-the-Rescue/assets/112714380/b7191a2f-f196-48bf-91d4-c853a9eb6d04

**Maar dit helaas niet:**

https://github.com/joppekoops/CSS-to-the-Rescue/assets/112714380/0854d24d-f781-4e47-b2dd-14bd46d60344

Om dit nog op te lossen heb ik gezocht naar een *CodePen* waar het wel werkt. Deze lijkt op wat ik wil doen:
https://codepen.io/jkantner/pen/abOBdgV

Deze is wel in *Sass* geschreven en de gecompileerde CSS is heel erg lang. Sanne heeft het voor mij geabstraheerd tot alleen de kern functionaliteit:
https://codepen.io/shooft/pen/bGJVjBM
https://codepen.io/shooft/pen/zYXvLoO

### ✏️ Vormgeving
Mijn doel was om de *controller* (inclusief de *joystick*) een **3 dimensionaal** effect te geven. 

Om het **daadwerkelijk 3D** te maken, ging ik met ***perspective*** aan de gang. Eerst had ik alles een *perspective* gegeven, maar hierdoor werkte niet alles zoals het hoort te werken. Hier kwam ik achter omdat de onderkant van de controller niet goed gedraaid wilde worden.

| ![onderkant die niet goed draait](./readme-images/onderkant-fout.webp) |
| --- |
| Onderkant die niet goed draait |

In plaats van dat die 90° ten opzichte van de hele controller gedraaid moest worden, was dit 70°. Het kwam er op neer dat ik 3D niet goed begreep. Voor 3D in CSS, geef je alleen de hele scene of het hele object een `perspective`. Vervolgens moeten alle element hierin die ook 3D zijn `transform-style: preserve-3d;` krijgen. Er zijn nog een aantal dingen waarmee dit niet samen kan, zie het volgende artikel: 
https://css-tricks.com/things-watch-working-css-3d/

Iets 3 dimensionaals lijkt niet echt 3D zonder dat de **belichting** klopt. Hiervoor heb ik op belichte vlakken ***gradients*** gebruikt. Deze zijn heel subtiel, maar net genoeg om het een beetje glanzend te laten lijken.

Zo ging ik van ongestijld, naar meer realistisch:

| ![joystick ongestijld](./readme-images/joystick.webp) | ![joystick 3d gestijld](./readme-images/joystick-3d-1.webp) |
| --- | --- |
| *Joystick ongestijld* | *Joystick 3D gestijld* |

Verder wilde ik nog een patroontje toevoegen, zoals ook op de originele foto van de mixer. Hiervoor heb ik verschillende dingen geprobeerd in deze *CodePen*: https://codepen.io/jkhvacmd/pen/rNbVQeB, maar alles werd nog te veel herhalend.


De *joystick* is nog niet helemaal af. Hij moet nog een steeltje hebben om er helemaal logisch uit te zien. Nu is het een soort zwevende control. Bovendien moet de werking nog gefixt. Gelukkig heb ik inmiddels een voorbeeld waar dit wel werkt.



## 👨‍💻 Voortgang 2 (08-03-2024)
Vandaag hebben we laten zien hoe ver we waren met het maken en wat we er verder nog mee gaan doen.

Ik ga beginnen met het steeltje maken voor de *joystick* en het aanpassen van de functionaliteit naar de manier waarop het voorbeeld wat ik had gevonden het deed. Dit kan op twee manieren:

- Het kan zoals ik nu heb met twee *div*jes.
- Het kan ook door de animaties bij elkaar op te tellen met *animation compositions*.

Iets anders wat ik nog toe kan voegen is kleine animaties op de *joystick*. Bijvoorbeeld dat als die terugspringt dat die dan even *bounced*. Dit kan met CSS *linear timing functions*: `linear()`.



## 🔧 *Joystick* verbeteren

### ⚙️ Nieuwe functionaliteit
De nieuwe werking van het verplaatsen was niet zo ingewikkeld om toe te passen. Veel paste in de code die ik al had. De bestaande animaties kon ik verwijderen, want die had ik niet meer nodig.

Nu is het wel mogelijk om in beide richtingen te bewegen. Een nadeel is wel dat hoe dichter je al bij een kant zit, hoe langzamer die er heen beweegt.

### 🏑 Het steeltje
Simpel gezien is het steeltje van de *joystick* een kleine cilinder. Nou is een rond 3D object in CSS niet zo simpel. Je kan niet echt gebogen vlakken maken, dus het idee is om veel rechte vlakjes als koorden in een cirkel te zetten.

De cirkel wordt gegeven door een straal. Aan de hand van die straal kan ik vervolgens berekenen wat de breedte van de vlakjes moet zijn door sinus te gebruiken:

```CSS
ul {
	--face-width: calc(2 * var(--radius) * sin(360deg / var(--faces) / 2));
}
```

Hierin is 360° gedeeld door het aantal vlakken de hoek van een vlakje. Deze deel ik door twee zodat ik een rechthoekige driehoek maak van een kant van de driehoek tussen twee stralen en de koorde. Hierin weet ik de straal en de hoek, dus kan ik met sinus de overstaande zijde berekenen door de straal / de schuine zijde keer de sinus van de hoek te doen. Zie ook de volgende tekening:

![Tekening van berekening](./readme-images/math.webp)

Dit ging redelijk makkelijk. Vervolgens heb ik alle vlakjes gedraaid tot een bepaalde hoek, door weer 360° te delen door het aantal vlakjes. Daarna heb ik alle vlakjes de lengte van de straal naar buiten verplaatst. Dit lijkt eerst goed te gaan, maar zodra ik een boven- en onderkant had toegevoegd, zag ik het probleem: de vlakjes staken uit, waardoor er spleten ontstonden.

![Cilinder met gaten](./readme-images/cilinder-met-gaten.webp)

Dit kwam omdat de vlakjes iets naar binnen moesten staan, zodat de uiteinden op de straal kwamen te staan. Deze afstand kon ik gemakkelijk op eenzelfde manier berekenen als de breedte van de vlakjes, maar dan nu met cosinus:

```CSS
ul {
	 --face-distance: calc(var(--radius) * cos(360deg / var(--faces) / 2));
}
```

Ook moest er nog wat schaduw op het steeltje. Dit heb ik gedaan door elk vlakje een gradient te geven, die steeds iets donker werd. De gradient van elk vlakje moest wel weer op de volgende aansluiten. Hierdoor krijg je de volgende code:

```CSS
li {
	background-image: linear-gradient(to right, hsl(var(--h), var(--s), calc(var(--l) * .8)), hsl(var(--h), var(--s), calc(var(--l) * .75)));
}
```

Zie deze *CodePen*: https://codepen.io/jkhvacmd/pen/MWRyXLO

Deze code was wel erg lang en herhaalt veel, dus na een puzzeltje heb ik er de volgende code van gemaakt, waarin aan de hand van de index van het vlakje de kleur en positie wordt berekend:

```CSS
li {
	transform: rotateY(calc(360deg / var(--faces) * var(--index))) translateZ(var(--face-distance));
  		background-image: 
  			linear-gradient(
	  			to right, 
	  			hsl(
	  				var(--h), 
	  				var(--s), 
	  				calc(var(--l) * (((abs((var(--index) - 1) - .5 * var(--faces)) / var(--faces) - .5)) + 1))
	  			), 
	  			hsl(
	  				var(--h), 
	  				var(--s), 
	  				calc(var(--l) * (((abs((var(--index) + 0) - .5 * var(--faces)) / var(--faces) - .5)) + 1))
	  			)

  			)
  		;
}
```

https://codepen.io/jkhvacmd/pen/yLrJemN

Omdat ik hier gebruik maak van ```abs()``` werkt dit helaas alleen in Firefox. Helaas werken andere dingen die ik nodig heb juist niet in Firefox, dus hier zou ik het liefst nog een oplossing voor vinden.


## 👨‍💻 Voortgang 3 (15-03-2024)
Vandaag hebben we weer gekeken naar wat iedereen had gemaakt. Veel is al bijna af.

Verder heb ik nog uitgelegd aan de anderen hoe ik mijn cilinder precies heb gemaakt aan de hand van mijn *CodePen*. Ook had Sanne de oplossing voor het probleem met ```abs()```. In Chrome staat dit namelijk achter een vlag (Experimental Web Platform features), dus die heb ik aangezet.


## 📢 De titel
Voor de titel wilde ik iets wat van metaal lijkt te zijn. Het effect wat ik heb gemaakt, bestaat uit 3 lagen van *gradients* om samen een metaaleffect te maken.

| ![titel laag 1 met streepjes](./readme-images/titel_1.webp) | ![titel laag 2 met belichting](./readme-images/titel_2.webp) | ![titel laag 3 met reflectie](./readme-images/titel_3.webp) | ![titel laag 4 met rand](./readme-images/titel_4.webp) |
| --- | --- | --- | --- |
| Eerste laag: streepjes voor het geborstelde effect | Tweede laag: wit naar transparant voor belichting | Derde laag: witte streep voor licht reflectie | Vierde laag: 2 *drop-shadow* filters voor rand met glimmertje |

### 🎞️ Proberen te animeren
Na de themasessie over film titels in CSS wilde ik mijn titel ook animeren. Ik had daarvoor de volgende code geschreven: 

```CSS
header span {
	animation: fade-in 2s calc(var(--index) * .1s) both;
}

@keyframes fade-in {
	0% {
		opacity: 0;
		filter: blur(10em);
		transform: translateX(10em);
	}
	100% {
		opacity: 1;
		filter: blur(0);
		transform: translateX(0em);
	}
}
```

Dit werkte helaas niet samen met de metaaltextuur die ik de tekst had gegeven. Het was het een of het ander, dus heb ik toch voor het metaal gekozen.

### 🎞️ Toch nog animeren
Nadat ik nog even met Roel had gesproken blijkt dat inderdaad veel animaties niet samen kunnen met ```background-clip```, maar met sommige *properties* kan het wel. Uiteindelijk hebben we een soortgelijke animatie kunnen maken met ```margin``` en een blur animatie op de *parent*.


## 📱↔️💻 Responsive
Met de titel er bij was het ook belangrijk om het geheel een beetje meer *responsive* te maken. Nu verdween de titel op klein scherm achter de controller. Daarnaast was er op groot scherm veel ruimte aan de linker- en rechterkant. Daarom heb ik twee dingen aangepast:

1. De titel komt op klein scherm bovenaan te staan. Daarbij heb ik de grootte afhankelijk gemaakt van de schermbreedte of -hoogte, afhankelijk van waar de titel staat.
2. De mixer wordt op groot scherm 2 kolommen breed. Hierdoor worden alle elementen op de mixer automatisch herordend om naast elkaar te gaan staan.


## 🫥 *Opacity slider*
Nadat ik snel een video had toegevoegd op het scherm wilde ik nog een extra *control* toevoegen om de zichtbaarheid van de *graphic* aan te kunnen passen. Hiervoor heb ik nog een *slider* toegevoegd. Het lastige punt zat hem niet in het 3D maken, maar juist in een simpel iets: een verticale *slider*.

Dit kan met ```appearance```, maar ik had er al ```appearance: none;``` op staan, zodat ik een eigen 3D styling kon toepassen. Uiteindelijk kon het met een combinatie van 2 *properties*:

```CSS
input[type="slider"] {
	writing-mode: vertical-lr; /* Make the slider verticle */
	direction: rtl; /* Reverse the slider */
}
```


## 🍰 CSS @layer 
Als laatste moest ik nog een extra CSS *architecture* techniek toepassen. Ik had eerder al gebruik gemaakt van *nesting*, dus dat had ik automatisch toegepast. Daarnaast heb ik nu *layers* gebruikt.

Ik heb een aantal *layers* gemaakt voor verschillende doeleinden:

1. **reset**: deze laag is voor alle standaard *styling* van de browser die ik reset.
2. **default**: deze laag is voor standaard *styling* toe te passen zoals lettertype en tekstkleur.
3. **theme**: in deze laag geef ik alles aan wat voor bepaalde delen anders is dan de standaard stijl.
4. **layout**: zoals de naam al aangeeft, is deze laag voor alle lay-out, zoals *grid*, *flex* en *position*.
5. **components**: deze laag is voor alle *styling* die voor specifieke onderdelen anders zijn, zoals bijvoorbeeld de *joystick* of de *slider*.

Ik merkte dat deze techniek in dit geval wat minder nuttig is. Omdat ik niet zoveel stijlen en delen hergebruik had ik weinig stijlen die elkaar in de weg zaten door de *cascade*. Ik zie wel dat dit erg handig kan zijn voor grote websites met veel hergebruikte componenten over veel verschillende pagina's die misschien ook nog een verschillend thema hebben.


## 📈 Het resultaat
Het resultaat is een 3D lijkende virtuele video mixer. Om het zo 3D mogelijk te maken heb ik vooral veel geleerd van 3D in CSS en wat er wel niet mee kan. Daarom is het ook zo 3D mogelijk. Als je de mixer kantelt zie je dat niet alles 3D is.

| ![resultaat van de videomixer](./readme-images/resultaat.webp) | ![video mixer een beetje gekanteld, waardoor niet alles 3D meer lijkt](./readme-images/resultaat-gekanteld.webp) |
| --- | --- |
| Videomixer | Video mixer beetje gekanteld |

Het blijst ben ik met hoe dit 3D samen met de belichting door middel van *gradients* het op een echt product laat lijken. Deze combinatie van *fake* en echt 3D is een heel sterk middel om op een simpele manier dingen 3D te maken. Vooral ronde vormen kunnen goed worden nagebootst. Natuurlijk kan dit ook op de moeilijke manier zoals ik met het steeltje heb gedaan:

```CSS
ul {
	--radius: .5rem; /* outer radius of the stick */
	--length: 2.5rem; /* length of the stick */
	--faces: 32; /* amount of faces, should be the same as in the HTML */

	--face-width: calc(2 * var(--radius) * sin(360deg / var(--faces) / 2) + 1px); /* Calculate the width of a face */
	--face-distance: calc(var(--radius) * cos(360deg / var(--faces) / 2)); /* Calculate the distance from the middle to the face: inner radius */
}
```

Maar het meest ingewikkelde was toch wel de werking van de *joystick*. Hiervoor heb ik de meeste verschillende technieken moeten proberen (animaties die omkeerden, 2 animaties die optelden en uiteindelijk transities) die allemaal hun nadelen hadden.

Waar ik uiteindelijk nog tegenaan liep, is dat sommige dingen in CSS niet samen gaan, zoals bijvoorbeeld de animatie en opmaak van de titel. Hierdoor moest ik uiteindelijk voor een mindere animatie gaan om de opmaak te kunnen behouden.

![titel resultaat](./readme-images/titel-resultaat.webp)

Waar ik misschien nog wel het meeste van geleerd heb, is niet per se in de browser te zien, maar gaat om het structureren van code. Vooral hoe ik nieuwe selectoren en architectuur technieken kan gebruiken. Zo weet ik nu beter hoe *@layers* en *nesting* werken, maar bijvoorbeeld ook hoe ik lange selectoren kan schrijven voor dubbele interactie:

```CSS
main:has(section:nth-of-type(2) div:nth-of-type(1):active):has(section:nth-of-type(2) div:nth-of-type(1) button:nth-child(1):hover)
```


## ⛲️ Bronnen
- Panasonic Corporation of North America. (z.d.). AV-UHS500 4K 12G-SDI / HDMI Professional Live Video Production Switcher. Panasonic. https://na.panasonic.com//us/sites/default/files/styles/product_main/public/2020-01/av-uhs500_4k_switcher_with_12g-sdi_inputs_and_hdmi_for_live_video_production.png?itok=GZBrR5Y5%201x,%20/us/sites/default/files/styles/product_main_2x/public/2020-01/av-uhs500_4k_switcher_with_12g-sdi_inputs_and_hdmi_for_live_video_production.png?itok=k5FDN9kj%202x
- 't Hooft, S. (z.d.) d-pad button. CodePen https://codepen.io/shooft/pen/BaEabXy
- Kantner, J. (z.d.) Pure CSS Claw Crane. Codepen https://codepen.io/jkantner/pen/abOBdgV
- 't Hooft, S. (z.d.) crane voor joppe. Codepen https://codepen.io/shooft/pen/bGJVjBM
- 't Hooft, S. (z.d.) crane2 voor joppe. Codepen https://codepen.io/shooft/pen/zYXvLoO
- CSS Grid auto fit with max-content. (2019). Stack Overflow. https://stackoverflow.com/questions/52764726/css-grid-auto-fit-with-max-content
- abs() - CSS: Cascading Style Sheets (2023, 5 augustus). MDN Web Docs. https://developer.mozilla.org/en-US/docs/Web/CSS/abs
- Tudor, A. (2020, 30 januari). Things to Watch Out for When Working with CSS 3D | CSS-Tricks. CSS-Tricks. https://css-tricks.com/things-watch-working-css-3d/
- Coyier, C. (2022, 12 oktober). filter. CSS-Tricks. https://css-tricks.com/almanac/properties/f/filter/
- Green Screen Stock Videos by Vecteezy. https://www.vecteezy.com/free-videos/green-screen
- Stern, D. (2020, 2 juni). Styling Cross-Browser Compatible Range Inputs with CSS. CSS-Tricks. https://css-tricks.com/styling-cross-browser-compatible-range-inputs-css/
- How to reverse the direction in HTML5 range input? (2016). Stack Overflow. https://stackoverflow.com/questions/40275891/how-to-reverse-the-direction-in-html5-range-input
- Suzanne, M. (2022, 19 oktober). A Complete Guide to CSS Cascade Layers | CSS-Tricks. CSS-Tricks. https://css-tricks.com/css-cascade-layers/