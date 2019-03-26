# Stundenlog

## *Inhalt:* <a name="Inhalt"></a>
* [November](#November)
* [Dezember](#Dezember)
* [Januar](#Januar)
* [15. Januar - Neubeginn](#Neu)
* [Februar](#Februar)
* [März](#März)
<hr>

## November <a name="November"></a>

### 27. November - Einführung

Heute war die erste Stunde nach der Projektabgabe, deshalb wurden wir zuerst über den weiteren Verlauf des Unterrichtgeschehens informiert und dazu angeregt neue Ideen für unser zweites Projekt zu finden. Da uns zwar die Arbeit an einer Android-App gefallen hat, wir aber etwas neues machen wollten entschlossen wir uns, uns von App Inventor zu trennen und mit Android Studio weiter zu arbeiten. Unsere erste Idee war es, einen Simulator zu erstellen. 
<hr>

## Dezember <a name="Dezember"></a>

### 11. Dezember - Beginn mit Android Studio

Heute wurden innerhalb der Stunde einige Projekte unserer Mitschüler vorgestellt. Außerdem haben wir Android Studio eingerichtet und für die folgenden Stunden vorbereitet. Wir haben das Projekt erstellt und unsere Handys so konfiguriert, dass wir über die Entwicklungsumgebung die App starten und testen können. 
<hr>

### 17. Dezember - Aufbau des Layouts

Unsere Simulation soll aus mehreren Menüs bestehen, deshalb haben wir heute für die einzelnen Untermenüs Layout Dateien erstellt. Wir wollen allerdings die zentralen Informationen immer anzeigen. Da wir das in der heutigen Stunde nicht realisieren konnten werden wir in den nächsten Stunden weiter daran arbeiten. Unsere handys hatten einige Einstellungen wieder auf ihre Standardeinstellungen gesetzt, deshalb mussten wir diese erneut einstellen, was leider viel zeit gekostet hat, da wir zuerst nicht wussten wieso die Verbindung nicht aufgebaut werden konnte. 
<hr>

### 18. Dezember  - Einbindung der unteren Leiste

Heute haben wir begonnen die Untermenüs so einzubinden, dass man durch die untere Leiste das Untermenü wechseln kann. Dies gestaltetete sich jedoch schwerer als erwartet, das Layout wurde zwar übernommen, aber wir konnten die Werte der einzelnen Layoutelemente nicht mehr mit den alten Variablen verändern. Deshalb haben wir uns generell mit dem Layout-System bei Android auseinandergesetzt, welches um einiges komplizierter war als von uns zuerst angenommen und uns Hintergrundwissen fehlt.
<hr>

## Januar <a name="Januar"></a>

### 8. Januar - Einbindung der unteren Leiste Teil 2

Trotz kleiner Fortschritte am Projekt während der Ferien konnten wir das Grundgerüst nicht fertigstellen. Während der Stunden haben wir einige Änderungen an den Layoutänderungen vorgenommen. In der aktuellen Version der App bleibt zwar die Leiste immer an der unteren Seite bestehen, jedoch muss der EventListener (für uns unerklärlich) jedes mal neu registriert werden. Anders als in der vorherigen Version wird das geöffnete Layout auf der Leiste korrekt angezeigt. Da wir seit Beginn kaum Fortschritte an unserem Projekt gemacht hatten, haben wir uns überlegt ob es nicht besser wäre auf ein anderes Projekt umzusteigen.
<hr>

### 14. Januar - Ende erstes Projekt

Da wir es heute erneut nicht geschafft haben das Layout fertigzustellen, keine weiteren Ansätze hatten und auch gar nicht wissen warum unsere Lösung nicht funktioniert, haben wir uns entschieden das Simulator-Projekt hinter uns zu lassen und ein anderes Projekt zu beginnen. 
Da wir weiterhin gerne mit Java arbeiten wollten entschieden wir uns für Greenfoot und begannen erneut Ideen zu sammeln. Wir haben uns letztendlich für ein "Jump n' Run" entschieden. Am Ende der Stunde haben wir Greenfoot installiert und uns den Namen "Bario" für unser Projekt ausgedacht.
<hr>

### 15. Januar - Beginn mit Greenfoot<a name="Neu"></a>

Heute haben wir mit unserem neuen Projekt angefangen. Wie bereits erwähnt begannen wir mit Greenfoot um unsere neue Idee zu realisieren. Da wir vorher noch nicht mit Greenfoot gearbeitet haben mussten wir erstmal das Programm kennenlernen, dafür haben wir ein Testprojekt erstellt. Da der Einstieg zu Greenfoot sich einfacher gestaltete als erwartet haben wir direkt mit unserem projekt begonnen. Als erstes haben wir die Klassen für Bario, ein peruanischer Alpakafarmer und der Protagonist unseres Spiels, und seine Waffe, eine Rakete, erstellt. Derzeit kann sich Bario in jede Richtung bewegen, wir werden in den nächsten Stunden Gravitation hinzufügen. Seine Waffe kann mit der Leertaste abgefeuert werden und bewegt sich konstant nach rechts.
<hr>

### 21. Januar - Erstellung der Grundlagen

Da man in einem Jump'n'Run springen können sollte, was ohne Gravitation nicht wirklich funktioniert, haben wir diese erstellt. Jedes vorher registrierte Objekt wird bei jedem Ausführen der `act()`-Methode in unserer `MyWorld`-Klasse nach unten bewegt, wobei die Geschwindigkeit zunimmt. Außerdem dreht die Rakete jetzt nach einiger Zeit und kehrt an seine Startposition zurück.
<hr>

### 22. Januar - Erweiterung der Spielphysik

Heute haben wir bereits  vorhandene Funktionen (wie die Gravitation) überarbeitet und einige Werte für Bewegungsgeschwindigkeiten angepasst. 
Außerdem haben wir den ersten Gegner, ein Kamel, hinzugefügt. Um zu verhindern dass der Spieler einen unendlichen Strom an Raketen starten kann haben wir einen Cooldown hinzugefügt, haben dabei aber einen Fehler gemacht. Da wir den Cooldown in der `act()`-Funktion platziert haben, wartet das ganze Programm, was es nicht tun soll.
![`World`-Klasse](https://raw.githubusercontent.com/StormarnJB/BarioTheGame/master/Screenshots/Screenshot%202019-01-22%20at%2016.29.01.png) Neue Version der `World`-Klasse mit Gravitation auf alle zuvor registrierten Objekte.
![Ergebnis](https://raw.githubusercontent.com/StormarnJB/BarioTheGame/master/Screenshots/Screenshot%202019-01-22%20at%2016.26.30.png) Spielwelt nach Start des Programms 
<hr>

### 29. Januar - Überarbeitung der Rakete

Heute haben wir den Cooldown so überarbeitet, dass nicht das ganze Programm wartet, sondern dass in der World Klasse ein Timer läuft und sich erst eine neue Rakete starten lässt wenn der Cooldown auf 0 steht. Dafür verwenden wir die Sytsmzeit zum Zeitpunkt des letzten Starts einer Rakete und dem aktuellen Zeitpunkt. Der Cooldown wird in der oberen linken Ecke angezeigt, hierfür verwenden wir die `showText()`-Methode<hr>

## Februar <a name="Februar"></a>

### 4. Februar - Überarbeitung des Stundenlogs

Heute haben wir einige Texte in unserem Stundenlog überarbeitet und erweitert, zusätzlich haben wir einige ältere Screenshots hochgeladen und eingefügt. <hr>


### 12. Februar - Erstellung der Plattformen

Wir hatten zwar bereits Gravitation hinzugefügt (in der `MyWorld`-Klasse), aber es gab noch keine Plattformen, auf welchen die `Actor` stehen können, diese haben wir heute als `Ground` hinzugefügt. Die `Ground`-Klasse selbst ist leer, da die Plattformen nur eine passive Funktion haben. Bei der Berechnung benutzen wir die `getObjectsAtOffset`-Methode von Greenfoot. Es kann jedoch vorkommen, dass der `Actor` nach/bei einem Sprung durch diesen hindurchfällt, wir hatten jedoch nicht mehr genug Zeit diese Problem anzugehen.
<hr>

### 19. Februar - Überarbeitung der Grundelemente

In Heimarbeit haben wir einen GameOver Bildschirm eingefügt und die Gravitation/Sprungfunktionen so überarbeitet, dass man nicht mehr durch die Boden fallen kann. Außerdem haben wir einzelne Funktionen entfernt, welche keinen Sinn mehr hatten. Damit die `Actor` nicht mehr durch den Boden fallen können, bewegen wir jeden `Actor` der mit einem Boden überschneidet auf diesen Boden. Zusätzlich haben wir einen hintergrund eingefügt und die Raketenfunktion erweitert. Wenn die Rakete auf ein Kamel trifft verschwinden die Rakete und das Kamel.
<hr>

### 25. Febrauar - Überarbeitung des Stundenlogs

Zu Beginn der Stunde fand ein Gespräch über die Abgabetermine statt, anschließend haben wir einige Einträge des Stundenlogs überarbeitet und unser Projekt auf Fehler getestet und diese (nicht schwerwiegenden) anschließend entfernt. 
<hr>


### 26. Februar - Verschiebung der `gravity()`-Funktion in die `GravityActor`-Klasse

Auf Hinweis von Herrn Buhl haben wir die Gravitation aus der `MyWorld` in die neu erstellte `GravityActor`-Klasse verschoben. Bario und die Kamele sind unterklassen von `GravityActor`, wodurch wir innerhalb der `gravity()` besser auf die Klassen `Bario` und `Camel` zugreifen können. Innerhalb dieser Klassen müssen wir jetzt nur in der `act()` einmal `gravity()` ausführen. Außerdem haben wir Carpeto, den Bösewicht welcher alle Camelidae (Kamele, Lamas, Alpakas etc.) der Welt unterwerfen möchte, hinzugefügt. Zusätzlich haben wir einen Startbildschirm erstellt.
![Aktueller Stand](https://github.com/StormarnJB/BarioTheGame/blob/master/Screenshots/0403201910_58_42.gif?raw=true) 
Derzeitiger Stand des Spiels inkl. Startbildschirm
<hr>

## März <a name="März"></a>

### 4. März - Überarbeitung des Stundenlogs

Heute haben wir das Aussehen des Stundenlogs verbessert und ein Gif erstellt und eingefügt um den aktuellen Stand des Spiels zu visualisieren.
<hr>

### 5. März  - Erstellen eines Weltgenerators

Vor dieser Stunde wurden zu Beginn des Spiels immer zwei plattformen an der selben Stelle erstellt, das haben wir heute geändert. Dafür haben wir in unserer `MyWorld`-Klasse die `generateWorld()`-Funktion erstellt, anfangs haben wir die Plattformen komplett zufällig erstellt, was jedoch teilweise zu unmöglichen Leveln geführt hat. Um das zu vermeiden erstellen wir jetzt Stück für Stück die Welt. Nur die erste Plattform wird zufällig in die Welt gesetzt, die nächsten Plattformen werden nach füür nach um einen zufälligen Betrag innerhalb eines Intervalls nach oben und rechts verschoben. Da dieser Betrag nicht sehr hoch ist (jeweils ~1/3 der Seitenlängen) existiert fast immer eine erreichbare Plattform.
<hr>

### 18. März - Überarbeitung des Stundenlogs

Zuhause haben wir die Werte des Weltgenerators angepasst, neue Texturen erstellt und eingefügt, die Bewegungen von Carpeto und dem Kamel überarbeitet und die Gravitation angepasst und verbessert. Außerdem verschwinden die Teppiche, welche einen 3D-Effekt erhalten haben (`Ground`) nun nach einiger Zeit.
In der Schulstunde haben wir das Stundenlog überarbeitet
![Aktueller Stand](https://github.com/StormarnJB/BarioTheGame/raw/master/Screenshots/2603201915_22_20.gif)Aktueller Stand


### 25. März - Überarbeitung des Stundenlogs

Heute haben wir den Stundenlog erneut überarbeitet, wir haben ein neues Gif vorbereitet und die Screenshots neu organisiert.
Zusätzlich haben wir uns heute Gedanken über die Weiterarbeit während der Ferien gemacht. Um unser Spiel fertigzustellen müssen wir den Bösewicht besiegbar machen, das Kamel überarbeiten, den Startbildschirm ansprechender gestalten und falls möglich in den Start und Gameoverbildschirm Animationen einfügen welche die Hintergrundgeschichte erklären.


### 26. März - Überarbeitung des Stundenlogs

Da heute der Abgabetag für das Stundenlog ist, haben wir zu Anfang der Stunden uns dessen Überarbeitung konzentriert. Da uns klar wurde, dass wir innerhalb der übrigen Zeit in der Schule sowieso nicht fertig werden und da wir noch Screenshots von unseren Heimgeräten hochladen wollten haben wir unser Spiel getestet und den Weltgenerator leicht überarbeitet.
<hr>

