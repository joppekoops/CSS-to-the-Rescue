# CSS-to-the-Rescue

## De opdracht

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

|<video src="./readme-images/joystick-try_1.mov"/>|<video src="./readme-images/joystick-try_1-issue.mov"/>|
| --- | --- |
| Dit werkt! | Maar dit helaas niet |

Om dit nog op te lossen heb ik gezocht naar een CodePen waar het wel werkt. Deze lijkt op wat ik wil doen:
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