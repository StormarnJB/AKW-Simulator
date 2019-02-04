# Stundenlog

## *Inhalt:* <a name="Inhalt"></a>
* [November](#November)
* [Dezember](#Dezember)
* [Januar](#Januar)
* [15. Januar - Neubeginn](#Neu)


## November <a name="November"></a>

### 27. November

Heute war die erste Stunde nach der Projektabgabe, wir wurden über den weiteren Verlauf des Unterrichtgeschehens informiert und dazu angeregt neue Ideen für unser zweites Projekt zu finden. Da uns zwar die Arbeit an einer Android-App gefallen hat, wir jedoch etwas neues machen wollten entschlossen wir uns, uns von App Inventor zu trennen und mit Android Studio weiter zu arbeiten. Wir entschlossen uns einen Simulator zu erstellen. 


## Dezember <a name="Dezember"></a>

### 11. Dezember

Heute wurden innerhalb der Stunde einige Projekte unserer Mitschüler vorgestellt. Außerdem haben wir Android Studio eingerichtet und für die folgenden Stunden vorbereitet. Wir haben das Projekt erstellt und unsere Handys so konfiguriert, dass wir über die Entwicklungsumgebung die App starten und testen können.


### 17. Dezember

Heute haben wir für die einzelnen Untermenüs Layout Dateien erstellt, diese sollen es ermöglichen dass nur ein Teil des Layouts geändert wird und wir so nicht jedes mal neue Werte festlegen sollen. Zusätzlich mussten wir erneut Android Studio so einrichten, dass die Handys sich verbinden können, da dies nicht mehr funktionierte.

### 18. Dezember 

Heute haben wir begonnen die Untermenüs so einzubinden, dass man durch die untere Leiste das Untermenü wechseln kann. Dies gestaltetete sich jedoch schwerer als erwartet.
Zusätzlich haben wir uns generell mit Layouts einer Android App beschäftigt, da uns Hintergrundwissen fehlte.


## Januar <a name="Januar"></a>

### 8. Januar

Heute haben wir einige Layoutänderungen durchgeführt. Zusätzlich haben wir das untere Menü so bearbeitet, dass es immer angezeigt wird, auch wenn das obere Menü geändert wird. Wir hatten zwar Erfolg damit, dass die untere Leiste sich nicht ändert, obwohl wir den INhalt der oberen Hälfte ändern, (für uns) unerklärlicherweise muss jedoch der Listener für die Leiste nach jedem Wechsel neu registriert werden.

### 14. Januar

Da wir es heute erneut nicht geschafft haben das Layout fertigzustellen und auch keine weiteren Ansätze hatten haben wir uns entschieden ein anderes Projekt zu beginnen. Da wir weiterhin gerne mit Java arbeiten wollten entschieden wir uns für Greenfoot. 

### 15. Januar <a name="Neu"></a>

Heute haben wir mit unserem neuen Projekt angefangen. Wie bereits erwähnt begonnen wir mit Greenfoot um unsere neue Idee zu realisieren. WIr begannen mit "Bario" einem Jump'n'run mit dem Protagonisten Bario. 
Als erstes haben wir die jeweiligen Klassen für Bario und seine Waffe erstellt. Bario kann sich bewegen, es gibt jedoch noch keine Gravitation, er kann sich also noch in jede Richtung gleichmäßig bewegen.

### 21. Januar

Heute haben wir Gravitation hinzugefügt, sodass sich jedes Objekt, welches wir vorher registriert haben, nach unten bewegt. Seine Waffe bewegt sich jetzt nicht mehr unendlich nach rechts, sondern macht eine U-Drehung und kehrt an seine Startposition zurück.

### 22. Januar

Heute haben wir bereits  vorhandene Funktionen überarbeitet und Werte für Bewegungsgeschwindigkeiten angepasst. Außerdem haben wir den ersten Gegner, ein Kamel hinzugefügt. Um zu verhindern dass der Spieler einen unendlichen STrom an Raketen starten kann haben wir einen Cooldown hinzugefügt, haben dabei aber einen Fehler gemacht. Da wir den Cooldown in der 'act()'-Funktion platziert haben, hat das gesamte Programm 5 Sekunden gewartet.

### 29. Januar

Haute haben wir den COoldown so überarbeitet, dass nicht das ganze Programm wartet, sondern dass in der World Klasse ein Timer läuft und sich erst eine neue Rakete starten lässt wenn der Cooldown auf 0 steht.

### 4. Februar

Heute haben wir den Stundenlog überarbeitet und Screenshots eingefügt.
