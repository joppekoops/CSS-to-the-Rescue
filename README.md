# CSS-to-the-Rescue

## De opdracht

## 💡Mijn Idee
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

## 👨‍💻Voortgang 1 (01-03-2024)
Vandaag hebben we onze ideeën doorgesproken. Daaruit kwamen een aantal vragen en tips om te kunnen beginnen.

- Wil je dat de *joystick* weer teruggaat naar het midden of dat de *joystick* blijft staan in de positie waarin je die zet?
- Je kan de *joystick* laten werken met een aantal *buttons* eromheen. Sanne had een [voorbeeld](https://codepen.io/shooft/pen/BaEabXy) van een *D-pad* die zo werkt. Voor een *joystick* zijn er natuurlijk meer mogelijkheden voor richtingen dan 4.
- Het blokje kan je een animatie geven voor helemaal van links naar rechts. Die kan je vervolgens op pauze te zetten als er niets wordt ingedrukt en voorwaarts of achterwaarts afspelen als de *joystick* naar links of rechts gaat. Ditzelfde kan dan voor naar boven en beneden. Je kan tegenwoordig twee animaties op één element zetten, of je kan er nog een *div*-element omheen zetten.

Jop maakt toevallig ook een *joystick*, hoewel hij juist wil dat de *joystick* blijft staan als je die loslaat. Dat gaat waarschijnlijk werken met een verticale en een horizontale *slider*.

