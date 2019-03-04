# Stundenlog

## *Inhalt:* <a name="Inhalt"></a>
* [November](#November)
* [Dezember](#Dezember)
* [Januar](#Januar)
* [15. Januar - Neubeginn](#Neu)
* [Februar](#Februar)
* [März](#März)

## November <a name="November"></a>

### 27. November

Heute war die erste Stunde nach der Projektabgabe. deshalb wurden wir zuerstvüber den weiteren Verlauf des Unterrichtgeschehens informiert und dazu angeregt neue Ideen für unser zweites Projekt zu finden. Da uns zwar die Arbeit an einer Android-App gefallen hat, wir aber etwas neues machen wollten entschlossen wir uns, uns von App Inventor zu trennen und mit Android Studio weiter zu arbeiten. Unsere erste Idee war einen Simulator zu erstellen. 


## Dezember <a name="Dezember"></a>

### 11. Dezember

Heute wurden innerhalb der Stunde einige Projekte unserer Mitschüler vorgestellt. Außerdem haben wir Android Studio eingerichtet und für die folgenden Stunden vorbereitet. Wir haben das Projekt erstellt und unsere Handys so konfiguriert, dass wir über die Entwicklungsumgebung die App starten und testen können.


### 17. Dezember

Heute haben wir für die einzelnen Untermenüs Layout Dateien erstellt, diese sollen es ermöglichen dass nur ein Teil des Layouts geändert wird und wir so nicht jedes mal neue Werte festlegen sollen. Zusätzlich mussten wir erneut Android Studio so einrichten, dass die Handys sich verbinden können, da dies nicht gespeichert wurde und deshalb nicht  mehr funktionierte.

### 18. Dezember 

Heute haben wir begonnen die Untermenüs so einzubinden, dass man durch die untere Leiste das Untermenü wechseln kann. Dies gestaltetete sich jedoch schwerer als erwartet.
Zusätzlich haben wir uns generell mit Layouts einer Android App beschäftigt, da uns Hintergrundwissen fehlte.


## Januar <a name="Januar"></a>

### 8. Januar

Heute haben wir einige Layoutänderungen durchgeführt. Zusätzlich haben wir das untere Menü so bearbeitet, dass es immer angezeigt wird, auch wenn das obere Menü geändert wird. Wir hatten zwar Erfolg damit, dass die untere Leiste sich nicht ändert, obwohl wir den Inhalt der oberen Hälfte ändern, (für uns) unerklärlicherweise muss jedoch der Listener für die Leiste nach jedem Wechsel neu registriert werden.

### 14. Januar

Da wir es heute erneut nicht geschafft haben das Layout fertigzustellen und auch keine weiteren Ansätze hatten haben wir uns entschieden das Simulator-Projekt hinter uns zu lassen und ein anderes Projekt zu beginnen. Da wir weiterhin gerne mit Java arbeiten wollten entschieden wir uns für Greenfoot und begannen erneut Ideen zu sammeln. Wir haben uns für ein "Jump n' Run" entschieden.

### 15. Januar (Neubeginn)<a name="Neu"></a>

Heute haben wir mit unserem neuen Projekt angefangen. Wie bereits erwähnt begannen wir mit Greenfoot um unsere neue Idee zu realisieren. 
Als erstes haben wir die jeweiligen Klassen für Bario und seine Waffe erstellt. Bario kann sich bewegen, es gibt jedoch noch keine Gravitation, er kann sich also noch in jede Richtung gleichmäßig bewegen.

### 21. Januar

Heute haben wir Gravitation hinzugefügt, sodass sich jedes Objekt, welches wir vorher registriert haben, nach unten bewegt. Seine Waffe bewegt sich jetzt nicht mehr unendlich nach rechts, sondern macht eine U-Drehung und kehrt an seine Startposition zurück.

### 22. Januar

Heute haben wir bereits  vorhandene Funktionen überarbeitet und Werte für Bewegungsgeschwindigkeiten angepasst. Außerdem haben wir den ersten Gegner, ein Kamel, hinzugefügt. Um zu verhindern dass der Spieler einen unendlichen Strom an Raketen starten kann haben wir einen Cooldown hinzugefügt, haben dabei aber einen Fehler gemacht. Da wir den Cooldown in der `act()`-Funktion platziert haben, hat das gesamte Programm 5 Sekunden gewartet.
![`World`-Klasse](https://raw.githubusercontent.com/StormarnJB/BarioTheGame/master/Screenshots/Screenshot%202019-01-22%20at%2016.29.01.png) Neue Version der `World`-Klasse mit Gravitation auf alle zuvor registrierten Objekte.
![Ergebnis](https://raw.githubusercontent.com/StormarnJB/BarioTheGame/master/Screenshots/Screenshot%202019-01-22%20at%2016.26.30.png) Spielwelt nach Start des Programms


### 29. Januar

Haute haben wir den COoldown so überarbeitet, dass nicht das ganze Programm wartet, sondern dass in der World Klasse ein Timer läuft und sich erst eine neue Rakete starten lässt wenn der Cooldown auf 0 steht.


### 4. Februar <a name="Februar"></a>

Heute haben wir den Stundenlog überarbeitet und Screenshots eingefügt.


### 12. Februar

Heute haben wir einen Untergrund hinzugefüt, die Sprung und Gravitation überarbeitet.


### 19. Februar

Zuhause haben wir einen GameOver Bildschirm eingefügt, die Gravitation/sprungfunktionen (und aufegräumt) überarbeitet.
In de Stunde haben wir Ground überabeitet hintergrund rakete macht bumm


### 25. Febrauar

Gespräch Abgabe - Stundenlog überarbeitet - getestet / überarbeitet


### 26. Februar

Gravitation in GravityActor fertig, Start Bildschirm eingeführt, Carpeto eingeführt.

![Aktueller Stand](https://github.com/StormarnJB/BarioTheGame/blob/master/Screenshots/0403201910_58_42.gif?raw=true)


### 4. März <a name="März"></a>

Stundenlog verbessert gif

