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

####//GIF

### 22. Januar - Erweiterung der Spielphysik

Heute haben wir bereits  vorhandene Funktionen (wie die Gravitation) überarbeitet und einige Werte für Bewegungsgeschwindigkeiten angepasst. 
Außerdem haben wir den ersten Gegner, ein Kamel, hinzugefügt. Um zu verhindern dass der Spieler einen unendlichen Strom an Raketen starten kann haben wir einen Cooldown hinzugefügt, haben dabei aber einen Fehler gemacht. Da wir den Cooldown in der `act()`-Funktion platziert haben, wartet das ganze Programm, was es nicht tun soll.
![`World`-Klasse](https://raw.githubusercontent.com/StormarnJB/BarioTheGame/master/Screenshots/Screenshot%202019-01-22%20at%2016.29.01.png) Neue Version der `World`-Klasse mit Gravitation auf alle zuvor registrierten Objekte.
![Ergebnis](https://raw.githubusercontent.com/StormarnJB/BarioTheGame/master/Screenshots/Screenshot%202019-01-22%20at%2016.26.30.png) Spielwelt nach Start des Programms <hr>


### 29. Januar - Überarbeitung der Rakete

Heute haben wir den Cooldown so überarbeitet, dass nicht das ganze Programm wartet, sondern dass in der World Klasse ein Timer läuft und sich erst eine neue Rakete starten lässt wenn der Cooldown auf 0 steht. Dafür verwenden wir die Sytsmzeit zum Zeitpunkt des letzten Starts einer Rakete und dem aktuellen Zeitpunkt. Der Cooldown wird in der oberen linken Ecke angezeigt, hierfür verwenden wir die `showText()`-Methode<hr>

## Februar <a name="Februar"></a>

### 4. Februar - Überarbeitung des Stundenlogs

Heute haben wir einige Texte in unserem Stundenlog überarbeitet und erweitert, zusätzlich haben wir einige ältere Screenshots hochgeladen und eingefügt. <hr>


### 12. Februar - Erstellung der Plattformen

Wir hatten zwar bereits Gravitation hinzugefügt ( in die World), aber es gab noch keine Plattformen o.ä. auf welchen die `Actor` stehen können, diese haben wir heute hinzugefügt. Die `Ground`-Klasse ist zwar leer, dies ist aber gewollt da alles in der Gravitation ausgeführt wird. (GetObjectsAtOffset())
Zusätzlich haben wir die Gravitation so angepasst, dass sie nur gilt, solange man nict auf einem Ground steht. Man fällt jedoch teilweise noch hindurch. Wir müssen die Sprung funktion also überarbeiten <hr>


### 19. Februar - Überarbeitung der Grundelemente

Zuhause haben wir einen GameOver Bildschirm eingefügt, die Gravitation/sprungfunktionen (und aufegräumt) überarbeitet, sodass man nicht mehr durch die Boden fallen kann. Dafür bewegen wir jeden Actor der mit einem Boden überschneidet auf diesen Boden. Das ganze sieht noch ein wenig unschön aus.
in der Stunde haben wir die Raketenfunktion überarbeitet, sie hat nun einen Sinn, da das kamel verschwindet.
In de Stunde haben wir Ground überabeitet hintergrund rakete macht bumm. <hr>


### 25. Febrauar - Überarbeitung des Stundenlogs

Gespräch Abgabe - Stundenlog überarbeitet - getestet / überarbeitet <hr>


### 26. Februar - Verschiebung der `gravity()`-Funktion in die `GravityActor`-Klasse

Gravitation in GravityActor fertig, Start Bildschirm eingeführt, Carpeto eingeführt.
Da wir die Gravitation in der MyWorld hatten und das Probleme macht haben wir es (nach Aufforderung) in die neu erschaffene GravityActor Klasse verschoben. Bario und Camel sind jetzt Subklassen von dieser.
Da das Spiel derzeit sofort beginnt wenn man die Anwendung startet und das nicht angenehm ist haben wir einen STartbildschirm eingefügt.
Zusätzlich haben wir Carpeto, den Bösewicht, hinzugefügt. 

![Aktueller Stand](https://github.com/StormarnJB/BarioTheGame/blob/master/Screenshots/0403201910_58_42.gif?raw=true) <hr>

## März <a name="März"></a>

### 4. März - Überarbeitung des Stundenlogs

Heute haben wir die Formalität des Stundenlogs verbessert. Außerdem haben wir einen kurzen Clip aufgenommen, als GIF gespeichert und anschließend bei Github hochgeladen und ins Stundenlog eingefügt. <hr>


### 5. März  - Erstellen eines Weltgenerators

Heute haben wir mehrere Platformen die zufällig in der Welt erschaffen werden eingefügt. Diese Funktion wollen wir aber später noch anpassen und wenn möglich zwei Spielmodi erstellen. <hr>



### 18. März - Überarbeitung des Stundenlogs

In Heimarbeit haben wir:
  ß. Welt Generator
  ß. KaKI
  ß. Texturen
  ß. Gravitation <hr>
Stundenlog überarbeitet (layout + inhalt) <hr>


### 25. März - Überarbeitung des Stundenlogs

Heute haben wir den Stundenlog erneut überarbeitet, wir haben ein neues Gif vorbereitet und Screenshots neu organisiert.
Morgen schließen wir dann das Stundenlog ab und haben heute pläne für die weiterarbeit während der Ferien gemacht. Der Bösewicht muss besiegt werden können, der Startbildschirm <hr>


### 26. März - Überarbeitung des Stundenlogs

Da heute der Abgabetag für das Stundenlog ist, haben wir uns erneut auf dessen Überarbeiuntung fokussiert.
![Aktueller Stand](https://github.com/StormarnJB/BarioTheGame/raw/master/Screenshots/2603201915_22_20.gif)<hr>

