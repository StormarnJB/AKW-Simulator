# Informatik Projekt 2 - Bario
*von Julian und Benedict, 12e*

## Inhaltsverzeichnis
* [Projekt](#Projekt)
  * [Spiel](#Idee)
  * [Greenfoot](#Greenfoot)
* [Aufbau](#Aufbau)
* [Stundenlog (*seperate Datei*)](https://github.com/StormarnJB/BarioTheGame/blob/master/Stundenlog.md)
  * [November](https://github.com/StormarnJB/BarioTheGame/blob/master/Stundenlog.md#November)
  * [Dezember](https://github.com/StormarnJB/BarioTheGame/blob/master/Stundenlog.md#Dezember)
  * [Januar](https://github.com/StormarnJB/BarioTheGame/blob/master/Stundenlog.md#Januar)
  * [Februar](https://github.com/StormarnJB/BarioTheGame/blob/master/Stundenlog.md#Februar)
  * [März](https://github.com/StormarnJB/BarioTheGame/blob/master/Stundenlog.md#März)


## Das Projekt <a name="Projekt"></a>

#### Das Spiel <a name="Idee"></a>

Das Spiel „Bario“ handelt von einem Alpakafarmer, der von dem bösen „Carpeto“ verfolgt wird und auf fliegende Teppiche springen muss um zu überleben. Carpeto möchte alle Kamele (*=Camelidae*) (Trampeltier, Lamas, Alpakas etc.) unterwerfen und so auch die Alpakas von Bario. Dieser kann sich mithilfe einer Rakete, die er als Hobby-Ingenieur entwickelt hat, zur Wehr setzten und Carpeto angreifen, fällt Bario allerdings herunter hat Carpeto gewonnen und das Spiel ist vorbei. Carpetos Angriffe bestehen darin die Teppiche mit seinen Angriffen zu zerstören, sodass Bario leichter herunterfallen kann. Die Teppiche verschwinden ebenfalls wenn man sich zu lange auf einem aufhält. Carpeto kann besiegt werden indem man ihn mit der Rakete abschießt. Schafft man dies fällt er von seinem individuell gesteuerten Teppich (lebt aber noch weiter) und kann endgültig besiegt werden indem er hinunterfällt. Das gelingt durch die alle 10 Sekunden erscheinenden Kamele, die ebenfalls mit der Rakete abgeschossen werden können und sich so zu Alpakas verwandeln. Die Kamele gehen auf Bario los, verlangsamen ihn und lassen die Teppiche schneller verschwinden, die Alpakas tun das gleiche bei Bario. Carpeto kann die Alpakas allerdings auch wieder zurück zu Kamelen verwandeln die dann wieder auf Bario losgehen. Wenn Carpeto herunterfällt ist er besiegt, das Spiel ist vorbei und man hat gewonnen.
Das Spiel kann nach dem Scheitern direkt durch einen Linksklick neugestartet werden, sodass man nicht jedes Mal wieder die Einleitung anschauen muss.

#### Greenfoot <a name="Greenfoot"></a>

Greenfoot ist eine interaktive Java-Entwicklungsumgebung, die primär für Ausbildungszwecke entwickelt wurde. Die Erstveröffentlichung war 2006. Sie erlaubt die einfache Entwicklung zweidimensionaler graphischer Anwendungen wie z. B. Simulationen und Spiele.
Die Entwickler geben als Zielgruppe "Programmieranfänger ab 15 Jahren aufwärts" an. Da die unterstützte Programmiersprache Standard-Java ist, können allerdings auch recht komplexe und anspruchsvolle Projekte implementiert werden.
Greenfoot-Szenarios können auf die Greenfoot Gallery exportiert werden, wo sie live ausgeführt werden können.
Die Hauptattraktion für Lernende ist, dass sehr schnell und interaktiv animierte graphische Projekte implementiert werden können. Einfache Spiele sind selbst für Anfänger nach kurzer Zeit erreichbar, was oft zu guter Motivation führt. Die Attraktion für Lehrende ist, dass Greenfoot wichtige Konzepte der objektorientierten Programmierpraxis gut illustriert. Klassen, Objekte, Vererbung, Methodenaufrufe und Objekt-Instanziierung sind für Benutzer sichtbar und erfahrbar. Diese konkrete Illustration abstrakter Konzepte unterstützt die Programmierlehre.


## Aufbau <a name="Aufbau"></a>

Greenfootprojekte bestehen jeweils aus `World` und `Actor` Klassen. Unser Greenfootprojekt besteht aus 4 Welten und 8 Akteuren:  
![Struktur](https://raw.githubusercontent.com/StormarnJB/BarioTheGame/master/Screenshots/Stuktur.PNG)

### Die Welten

<!--- START                                                                                                              -->
<details>
  <summary> Start </summary>

<details>
  <summary>Gesamte Klasse</summary>
 
```java 
import greenfoot.*;
import java.util.Random;
import java.util.List;
import java.util.ArrayList;

public class Start extends World{

    Sprite carpeto;
    ArrayList<Sprite> alpacas = new ArrayList<Sprite>();
    Random r = new Random();
    int i = 0;
    int alpacasremoved = 0;
    Sprite s2 = null;

    public Start(){    
        super(600, 400, 1);
        for(int i = 0; i < 10; i++){
            GreenfootImage alpacaimage = new GreenfootImage("Alpaca.png");
            int scale = r.nextInt(20) + 40;
            alpacaimage.scale(scale, scale);
            Sprite alpaca = new Sprite(alpacaimage);
            addObject(alpaca, r.nextInt(250) + 20, r.nextInt(300) + 50);
            alpacas.add(alpaca);
        }
    }

    public void act(){
        //Teil 1
        if(Greenfoot.isKeyDown("space")){
            Greenfoot.setWorld(new MyWorld());
        }

        //Teil 2
        for(Sprite a : alpacas){
            if(i < 400){
                if(r.nextInt(50) == 10){
                    a.setRotation(a.getRotation() + 180);
                    a.getImage().mirrorVertically();
                }
                a.move(r.nextInt(2));
            } else if (i == 400){
                a.setImage(new GreenfootImage("Alpaca.png"));
                a.getImage().mirrorVertically();
                a.turnTowards(0, 200);
            } else {
                a.move(2);
                if(a.getWorld() != null && a.isAtEdge()){
                    removeObject(a);
                    alpacasremoved++;
                }
            }
            
            if(alpacasremoved == alpacas.size()) Greenfoot.setWorld(new MyWorld());
        }

        //Teil 3
        switch (i){
            case 120:   GreenfootImage carpetoimage = new GreenfootImage("Carpeto.png");
                        carpetoimage.scale(100, 100);
                        carpetoimage.mirrorHorizontally();
                        carpeto = new Sprite(carpetoimage);
                        addObject(carpeto, 550, 100);
                        break;

            case 225:   GreenfootImage text1 = new GreenfootImage("Ich, Carpeto, werde alle Alpacas unterwerfen.", 30, Color.BLACK, null);
                        Sprite s1 = new Sprite(text1);
                        addObject(s1, 350, 30);
                        break;

            case 400:   GreenfootImage text2 = new GreenfootImage("Flieht, ihr Alpacas!", 30, Color.WHITE, null);
                        s2 = new Sprite(text2);
                        addObject(s2, 350, 350);
                        break;

            case 460:   GreenfootImage text3 = new GreenfootImage("Halt!\nIch werde dich mit meiner Rakete aufhalten!", 30, Color.WHITE, null);
                        s2.setImage(text3);
                        break;
        }
        //Teil 4
        i++;        
    }
} 
```
</details>

Die Startwelt lässt sich nicht vom Spieler beeinflussen, sie spielt eine Animation ab, nach welcher das Spiel gestartet wird. Die Animation lässt sich auch überspringen.  
Innerhalb des Konstruktors werden 10 Alpakas mit jeweils unterschiedlichen Größen erstellt und der Welt hinzugefügt. Gleichzeitig werden alle Alpacas in der ArrayList `alpacas` gespeichert.  
![Start Bildschirm](https://github.com/StormarnJB/BarioTheGame/blob/master/Screenshots/StartScreen.PNG)

Die `act()`Methode besteht aus drei Teilen.  
Im ersten Teil wird überprüft ob der Nutzer die Leertaste drückt um so den Startbildschirm zu überspringen.  

Der zweite Teil ist für das Verhalten der am Anfang hinzugefügten Alpakas zuständig, da es sich bei den Alpakas um `Sprite` Objekte handelt, welche kein eigenes Verhalten besitzen wird dieses innerhalb der Welt definiert. Am Anfang der Klasse wurde der Integer i definiert, dieser wird in jedem Durchlauf um 1 erhöht (`i++;`) und wird benutzt um den Ablauf der Animationen zu steuern.
In den ersten 400 Durchläufen der `act()` Methode bewegen die Alpakas sich jeweils um 0-2 Pixel, außerdem besteht eine 1:50 Chance dass die Alpacs sich drehen. Dafür werden die Alpacas um 180° gedreht, was jedoch dazu führt dass sie falsch herum sind, deshalb wird ihr Bild an ihrer vertikalen Achse gespiegelt.  
Im 401sten Durchlauf werden ihre Bilder auf ein nach links schauendes Alpaka gesetzt ('Alpaca.png' schaut nach rechts) und sie werden in Richtung des linken Bildschirmrands gedreht. 
In allen Durchläüfen danach bewegen sie sich um jewils zwei Felder (mit der im Konstruktor defnierten Seitenlänge von einem Pixel). Sobald sie den Bildschirmrand erreicht haben werden sie aus der Welt entfernt. Gleichzeitig wird durch `alpacasremoved` mitgezählt wie viele Alpakas bereits entfernt wurden. Sobald die Anzahl der entfernten Alpakas der Anzahl der anfangs hinzugefügten Alpakas entspricht wird das Spiel gestartet, indem die Welt zu `MyWorld` geändert wird.

Der dritte Teil ist für den restlichen Teil des Geschehens auf dem Bildschirm zuständig. Beim 121sten Durchlauf wird "Carpeto", der Bösewicht, vergrößert, gespiegelt und anschließend hinzugefügt. Im 226sten Durchlauf wird Carpetos Dialogtext hinzugefügt, im 401sten Barios Aufruf an seine Alpakas zu fliehen. Im 461sten Durchlauf wird Barios Text dann auf eine Antwort an Carpeto geändert.  
![Start Bildschirm bei i > 460](https://github.com/StormarnJB/BarioTheGame/blob/master/Screenshots/StartScreen2.PNG)

</details>
<!--- Ende START                                                                                                          -->

<!--- MyWorld                                                                                                              -->
<details>
  <summary> MyWorld </summary>

<details>
  <summary>Gesamte Klasse</summary>
 
```java 
import greenfoot.*; 
import java.util.List;
import java.util.ArrayList;
import java.util.concurrent.ConcurrentHashMap;
import java.util.Map;
import java.util.Random;

public class MyWorld extends World{

    Bario bario;
    Camelidae camelstart;
    Carpeto carpeto;
    int counter = 0;
    private boolean rocketunavailable = false;
    private boolean rocketremoval = false;
    private long cooldown = 0;
    private long cooldownstart;

    public MyWorld(){
        super(600, 400, 1);
        bario = new Bario();
        camelstart = new Camelidae(bario);

        generateWorld();
        //Level

        setPaintOrder(Bario.class, Rocket.class, Camelidae.class, Carpeto.class, Ground.class, Sprite.class);
        showText("Cooldown: " + cooldown, 100, 50);
    }

    public void act(){
        showText(counter + "", 100, 80);
        counter += 1;

        //Raketenmanager
        if(Greenfoot.isKeyDown("space") && !rocketunavailable){
            rocketunavailable = true;
            Rocket rocket = new Rocket();
            addObject(rocket, bario.getX(), bario.getY());
            if(bario.isFacingLeft()) rocket.turn(180);
        }
        //Counter bei Raketenentfernung
        if(rocketremoval){
            cooldown = cooldownstart - System.currentTimeMillis() + 2000;
            showText("Cooldown: " + cooldown, 100, 50);
        }
        //Abschluss der Raketenentfernung
        if(rocketremoval && cooldown <= 0){
            rocketunavailable = false;
            rocketremoval = false;
            cooldown = 0;
            showText("Cooldown: " + cooldown, 100, 50);
        }

        List<Actor> actorlist = getObjects(Actor.class);
        for(Actor a : actorlist){
            a.setLocation(a.getX() - 1, a.getY());
        }
    }

    public void removeRocket(Rocket rocket){
        removeObject(rocket);
        cooldown = 0;
        cooldownstart = System.currentTimeMillis();
        rocketremoval = true;

    }

    public void generateWorld(){
        Random r = new Random();

        int lastx = r.nextInt(100);
        int lasty = r.nextInt(300);
        addObject(new Ground(), lastx, lasty);

        addObject(camelstart, lastx, lasty);

        for(int i = 0; i < 10; i++){
            int x = lastx + r.nextInt(200);
            if(x > 600) x = x - 600;
            lastx = x;
            int y = lasty - r.nextInt(250);
            if(y < 150) y = y + 250;
            if(y > 350) y = y - 50;
            lasty = y;
            addObject(new Ground(), x, y);
        }

        addObject(bario, lastx, lasty);

        carpeto = new Carpeto(bario);
        addObject(carpeto, 100, 100);
        addObject(carpeto.gs, 0 , 0);
    }
    
    public Bario getBario(){
        return bario;
    }
    
    public Carpeto getCarpeto(){
        return carpeto;
    }
}

```
</details>

Die `MyWorld` Welt ist die Spielwelt, weshalb sie am meisten Inhalt hat.  
Innerhalb des Konstruktors werden Bario und ein Kamel erstellt. Anschließend wird die `generateWorld`Funktion aufgerufen, welche für die Weltgenerierung zuständig ist. Zusätzlich wird die "PaintOrder" festgelegt, sie definiert die "Ebenen" auf welchen die Actor angezeigt werden. Die erstgenannten Klassen werden ganz oben angezeigt. Außerdem wird der Text für den Cooldown von Barios Waffe, der Rakete, angezeigt.  
Die `generateWorld()` generiert zufällige Welten, sodass sich jeder Spieldurchlauf unterscheidet. Am Anfang wird die "Startplattform" erstellt. Sie befindet sich zwischen den x-Koordinaten 0-100 und den y-koordinaten 0-300. Ihre Koordinaten werden als `lastx` und `lasty` zwischengespeichert. Auf ihr wird das im konstruktor generierte Kamel platziert.  
Anschließend werden in einer Schleife zehn weitere Plattformen (`Ground`) erstellt. Es wird jeweils eine zufällige Verschiebung in x und y-Richtung auf die Koordinaten der vorherig generierten Plattform angewandt. Liegt der neu generierte x/y Wert jedoch außerhalb des gewünschten Spielbereichs wird er angepasst.  
Sobald alle Plattformen generiert wurden wird Bario aud die zuletzt generierte Plattform gesetzt. Anschließend wird Carpeto und seine durchsichtige Plattform (In Carpeto.class: `gs = new Sprite(new GreenfootImage("groundshadowevil.png"));`) hinzugefügt.  
![Beispielwelten](https://github.com/StormarnJB/BarioTheGame/blob/master/Screenshots/Welten.png)

Innerhalb der `act()` werden die Verfügbarkeit der Rakete definiert und alle Objekte verschoben.  
Am Anfang der `act()` wird der "Counter" aktualisiert, er zeigt die Anzahl der bereits durchgeführten `act()`s.  
Anschließend wird überprüft ob der Spieler Leertaste drückt um die Rakete abzuschießen und ob sie bereits bereit ist. Ist dass der Fall wird die Rakete erstellt und gegebenenfalls gedreht um in die gewünschte Richtung zu starten.
Sobald die Rakete durch Ausführen von `removeRocket(Rocket rocket)` entfernt wurde und so `rocketremoval = true` gesetzt wurde, wird in der `act()` der `cooldown` aktualisiert. Sobald der `cooldown` also die Differenz der Systemzeiten beim Entfernen und Überprüfen kleiner/gleich 0 ist, wird die Rakete wieder verfügbar gemacht.  
Anschließend werden sämtliche `Actor` in der Welt um ein Feld nach links verschoben. Da alle Objekte gleichmäßig verschoben werden entsteht eine Illusion einer unendlichen Welt.  
Die Funktionen `getBario()` und `getCarpeto()` geben das jeweils gewünschte Objekt zurück.

</details>
<!--- Ende MyWorld                                                                                                       -->


<!--- GameOver                                                                                                              -->
<details>
  <summary> GameOver </summary>

<details>
  <summary>Gesamte Klasse</summary>
 
```java 
import greenfoot.*;

public class GameOver extends World{
    
    int i = 0;
    GreenfootImage image1 = new GreenfootImage("GameOver1.jpg");
    GreenfootImage image2 = new GreenfootImage("GameOver2.jpg");
    GreenfootImage image3 = new GreenfootImage("GameOver3.jpg");
    GreenfootImage image4 = new GreenfootImage("GameOver4.jpg");
    GreenfootImage image5 = new GreenfootImage("GameOver5.jpg");
    
    public GameOver(){
        super(600, 400,1);
        getBackground().drawImage(image1, 0, 0);
    }

    public void act(){
        switch(i){
            case 50: setBackground(image2); break;
            case 100: setBackground(image3); break;
            case 150: setBackground(image4); break;
            case 200: setBackground(image5); break;
        }
        
        if(Greenfoot.mouseClicked(this)){
            Greenfoot.setWorld(new MyWorld());
        }
        
        i++;
    }
}
```
</details>

Die `GameOver`Welt ist simpel aufgebaut. Im Konstruktor wird das Hintergrundbild gesetzt. Bei jedem Durchlauf wird der Integer i um 1 erhöht, er zählt also mit. Bei jedem 50sten Durchlauf wird anschließend das hintergrundbild geändert. Die Hintergrundbilder wurden mit einem externen Programm erstellt. Sobald der Nutzer die Welt anklickt wird der `MyWorld`Bildschirm geöffnet, sodass er es erneut versuchen kann.
![GameOver Bildschirm](https://raw.githubusercontent.com/StormarnJB/BarioTheGame/master/Screenshots/BarioGameplay2.gif)

[Benutzte Schriftart](https://fontmeme.com/fonts/mayan-karla-vazquez-font/)
</details>
<!--- Ende GameOver                                                                                                       -->


<!--- Victory                                                                                                           -->
<details>
  <summary> Victory </summary>

<details>
  <summary>Gesamte Klasse</summary>
 
```java 
import greenfoot.*; 
import java.util.Random;
import java.util.ArrayList;

public class Victory extends World{

    Sprite carpeto;
    int i = 0;
    Random r = new Random();
    ArrayList<Sprite> alpacas = new ArrayList<Sprite>();

    public Victory(){
        super(600, 400, 1);

        GreenfootImage carpetoimage = new GreenfootImage("Carpeto.png");
        carpetoimage.scale(100, 100);
        carpetoimage.mirrorHorizontally();
        carpeto = new Sprite(carpetoimage);
        carpeto.turn(70);
        addObject(carpeto, 300, 100); 
    }

    public void act(){

        switch(i){
            case 60:    GreenfootImage text1 = new GreenfootImage("Oh nein! Du hast mich besiegt\nund so alle Alpacas gerettet!", 30, Color.BLACK, null);
                        Sprite s1 = new Sprite(text1);
                        addObject(s1, 350, 30);
                        break;

            case 180:   GreenfootImage text2 = new GreenfootImage("Die Kamele wirst du auch freilassen!", 30, Color.WHITE, null);
                        Sprite s2 = new Sprite(text2);
                        addObject(s2, 350, 350);
                        break;

            case 240:   for(int x = 0; x < 10; x++){
                            GreenfootImage alpacaimage = new GreenfootImage("Alpaca.png");
                            int scale = r.nextInt(20) + 40;
                            alpacaimage.scale(scale, scale);
                            Sprite alpaca = new Sprite(alpacaimage);
                            addObject(alpaca, r.nextInt(40) + 30, r.nextInt(300) + 50);
                            alpacas.add(alpaca);
                        }
                        break;
        }

        for(Sprite a : alpacas){
            if(r.nextInt(30) == 10){
                a.setRotation(a.getRotation() + 180);
                a.getImage().mirrorVertically();
            }
            a.move(r.nextInt(2));
        }

        i++;
    }
}

```
</details>

Die Welt `Victory`, welche nach einem Sieg von Bario geöffnet wird, ist gleich wie die `Start` Welt aufgebaut.  
Im Konstruktor wird ein `Sprite` mit dem Bild von Carpeto erstellt, welches vergrößert und gespiegelt wurde.  
Innerhalb der `act()` wird erneut der Ablauf und das Verhalten der Alpakas gesteuert. Bei jedem urchlauf wird der Integer i um einen erhöht.  
![Victory Bildschirm](https://github.com/StormarnJB/BarioTheGame/blob/master/Screenshots/VictoryScreen.PNG)  
Im 61sten Durchlauf wird Carpetos Text angezeigt, welcher ausdrückt dass er besiegt wurde. Im 181sten Durchlauf Wird Barios Antwort angezeigt. Im 241sten Durchlauf erscheinen dann wieder Barios Alpakas. Es wird der gleiche Code wie bei der `Start`Welt benutzt.  
Im zweiten Teil der `act()` wird das Verhalten der Alpakas definiert. Wie bei der `Start`Welt bewegen sie sich jewils um 2 und wechseln dabei gelegentlich die Richtung.
![Victory Bildschirm bei i > 242](https://github.com/StormarnJB/BarioTheGame/blob/master/Screenshots/VictoryScreen2.PNG)
</details>
<!--- Ende Victory                                                                                                      -->


### Die Akteure

<!--- Sprite                                                                                                      -->
<details>
    <summary>Sprite</summary>
    
<details>
    <summary>Klasse</summary>
    
```java
import greenfoot.*;  // (World, Actor, GreenfootImage, Greenfoot and MouseInfo)

public class Sprite extends Actor{
    
    public Sprite(GreenfootImage g){
        setImage(g);
    }
    
    public void act(){
    }    
}
```
</details>

Die `Sprite`Klasse wird in den Welten `Start`, `MyWorld`, und `Victory` benutzt. Da diese auch ihr Verhalten kontrollieren und die Sprites also eigentlich nur Bilder sind, tun sie auch nichts. Im Konstruktor wird das von ihnen dargestellte Bild definiert.

</details>
<!--- Ende Sprite                                                                                                      -->


<!--- Ground                                                                                                     -->
<details>
    <summary>Ground</summary>
    
<details>
    <summary>Klasse</summary>
    
```java
import greenfoot.*; 

public class Ground extends Actor{

    Sprite gs;
    boolean loweredTransparency = false;

    public Ground(){
        gs = new Sprite(new GreenfootImage("groundshadow.png"));
    }

    public void act(){
        if(isAtEdge()){
            setLocation(600, getY());
        }

        if(gs.getWorld() == null) getWorld().addObject(gs, 100, 100);
        gs.setLocation(getX() - 10, getY() - 10);
        
        if(!loweredTransparency && getImage().getTransparency() != 255){
            lowerTransparency(-1);
        }
        loweredTransparency = false;
    }

    public void lowerTransparency(int x){
        int t = getImage().getTransparency();
        
        if(t - x <= 0){
            getWorld().removeObject(gs);
            getWorld().removeObject(this);
            return;
        }

        getImage().setTransparency(t - x);
        gs.getImage().setTransparency(t - x);
        loweredTransparency = true;
    }

    public void setTransparency(int x){
        getImage().setTransparency(x);
        gs.getImage().setTransparency(x);
    }
}

```
</details>

Die `Ground` Klasse beschreibt das Verhalten der Plattformen.  
Im Konstruktor wird ein `Sprite` mit einem Bild von einem Teppich erstellt. Da es sich um einen Sprite handelt, hat er keinen Effekt.  
In der `act()` wird als erstes überprüft ob die Plattform am Rand des Spielbereichs ist, was passieren kann da sämtliche Akteure in der `MyWorld` konstant nach links verschoben werden. Falls das der Fall ist wird sie an den rechten Rand gesetzt von wo sie sich erneut nach links bewegt.
Anschließend wird ihr "Schatten" verschoben, sodass er an die Plattform selbst anknüpft. Falls er (nach Erstellen der Welt) noch nicht hinzugefügt wurde, wird er hinzugefügt.  
Die Transparenz der Plattformen wird verringert wenn ein `GravityActor` auf ihnen steht (siehe `GravityActor.gravity()`) oder wenn sie von einem `Blob` getroffen werden, sie sollen aber auch regeneriern können, was in der `act()` geschieht. Wenn ihre Transparenz nicht bei 255 (dem Maximalwert) liegt und ihre Transparenz beim letzten Durchlauf nicht verändert wurde (`!loweredtransparency`) wird ihre Transparenz erhöht. Anschließend wird `loweredtransparency` auf `false` gesetzt. Nur wenn es von einem anderen Objekt heruntergesetzt wird soll die Plattform nicht "regenerieren".  
  
Die Funktion `lowerTransparency(int x)` senkt die Transparenz der Plattform um den gewünschten Wert `x`. Bevor das passieren kann wird noch der Wert `x` mit der aktuellen Transparenz verglichen. Wenn die gewünschte Transparenz kleiner/gleich 0 wäre wird die Plattform und ihr "Schatten" entfernt und die Funktion beendet. Ist das nicht der Fall wird die transparenz der Plattform und die ihres Schattens angepasst und `loweredtransparency` auf `true` gesetzt, da sie sonst "regenerieren" würde.  
  
Die Funktion setTransparency wird derzeit nicht benutzt. Sie setzt die Transparenz der Plattform und ihres "Schattens" auf den gewünschten Wert.

</details>
<!--- Ende Ground                                                                                                      -->


<!--- GravityActor                                                                                                      -->
<details>
    <summary>GravityActor</summary>
    
<details>
    <summary>Klasse</summary>
    
```java
import greenfoot.*;  // (World, Actor, GreenfootImage, Greenfoot and MouseInfo)
import java.util.List;

public class GravityActor extends Actor{
    public int v = 0;
    boolean jump = false;
    
    public void gravity(){
        List<Ground> glist = getWorld().getObjectsAt(getX(), getY() + getImage().getHeight()/2, Ground.class);
        if(glist.size() == 0){
            setLocation(getX(), getY() + v);
            v += 1;
        } else {
            v = 0;
            for(Ground g : glist){
                g.lowerTransparency(1);
            }
        }
        
        List<Ground> ig = getIntersectingObjects(Ground.class);
        if(ig.size() != 0 && getOneObjectAtOffset(0, getImage().getHeight()/2, Ground.class) == null){
            setLocation(getX(), ig.get(0).getY() - ig.get(0).getImage().getHeight() / 2 - getImage().getHeight() / 2);
            jump = false;
        }
        
        if(getY()>=390){
            if(this instanceof Bario){
                Greenfoot.setWorld(new GameOver());
            }
            if(this instanceof Carpeto){
                Greenfoot.setWorld(new Victory());
            }
            getWorld().removeObject(this);
        }
    }
}
```
</details>

Die `GravityActor` Klasse selbst tritt im Spiel selbst nicht in Erscheinung, stattdessen handelt es sich bei `Bario`, `Carpeto` und `Camelidae` um Erweiterungen von ihr. Die Klasse selbst besteht nur aus der `gravity()` Funktion.  
Die `gravity()` Funktion ist für die Gravitation zuständig, sie besteht aus drei Teilen.   
  
Im ersten Teil wird überprüft ob unter dem Mittelpunkt des `GravityActors` eine Plattform (`Ground`) existiert. Dafür wird eine Liste mit Plattformen an dieser Stelle abgerufen. Wenn diese Liste leer ist (also 0 Elemente besitzt) wird die Position des `GravityActors` um `v` Felder nach unten verschoben und `v` anschließend um 1 erhöht. Wenn die Liste allerdings mit Inhalt gefüllt ist wird `v` auf 0 gesetzt und die Transparenz der Plattformen um 1 verringert (siehe Ground).  
Im zweiten Teil wird überprüft ob der `GravityActor` sich mit einer Plattform überschneidet während er nicht auf einer Plattform steht. Ist dass der Fall wird er auf die Plattform gesetzt, da er sonst genau auf einer Plattform landen muss um nicht hindurchzufallen. Das kann passieren da die Plattformen (`Ground`) nur wenige Pixel dick sind und der `GravityActor` eine höhere Fallgeschwindigkeit `v` als die Breite der Plattformen besitzen kann. Außerdem wird `jump` auf false gesetzt, falls der `GravityActor` also im Sprung war, ist dieser jetzt beendet.  
Im letzten Teil wird überprüft ob sich der `GravityActor` am unteren Rand des Spielbildschirms befindet. Falls ja wird er entfernt und das Spiel ggf. beendet.

</details>
<!--- Ende GravityActor                                                                                                    -->


<!--- Bario                                                                                                      -->
<details>
    <summary>Bario</summary>
    
<details>
    <summary>Klasse</summary>
    
```java
import greenfoot.*;  // (World, Actor, GreenfootImage, Greenfoot and MouseInfo)
import java.util.List;

public class Bario extends GravityActor{
    
    boolean facingright = true;
    boolean facingleft = false;
    int speed = 5;
    
    public void act(){
        
        if(Greenfoot.isKeyDown("left")){
            setLocation(getX() - speed, getY());
            facingleft = true;
            facingright = false;
        }
        if(Greenfoot.isKeyDown("right")){
            setLocation(getX() + speed, getY());
            facingleft = false;
            facingright = true;
        }
        if(Greenfoot.isKeyDown("up")){
            jump = true;
        }
        if(jump){
            setLocation(getX(), getY() - 15);
        }
        
        gravity();
        
        speed = 5;
    }
    
    public boolean isFacingRight(){ return facingright; }
    public boolean isFacingLeft(){ return facingleft; }
}
```
</details>

Die Klasse `Bario` ist eine Erweiterung der `GravityActor` Klasse.  
In der `act()` wird überprüft ob eine der Pfeiltasten gedrückt wird. Wenn die Pfeiltaste nach links oder rechts gedrückt wird, bewegt sich Bario mit der Geschwindigkeit `speed` in die gewünschte Richtung. Gleichzeitig wird festgehalten in welche Richtung Bario sich zuletzt bewegt hat, was für die Startrichtung der Rakete wichtig ist. Wird die Pfeiltaste nach oben gedrückt wird `jump` auf `true` gesetzt.  
Anschließend wird überprüft ob `jump` `true` ist, falls ja wird Bario um 15 Felder nach oben bewegt. Anschließend wird `gravity()` aus der `GravityActor` Klasse aufgerufen, in welcher `jump` wieder auf `false` gesetzt werden kann. Am Ende wird die, von `Camelidae` beeinflussbare x-Geschwindigkeit `speed` wieder auf 5 gesetzt.  
Die Funktionen `isFacingRight()` und `isFacingLeft()` geben jeweils dern Wert `facingright` oder `facingleft` zurück.

</details>
<!--- Ende Bario                                                                                                      -->


<!--- Carpeto                                                                                                      -->
<details>
    <summary>Carpeto</summary>
    
<details>
    <summary>Klasse</summary>
    
```java
import greenfoot.*;  // (World, Actor, GreenfootImage, Greenfoot and MouseInfo)
import java.lang.Math;
import java.util.Random;

public class Carpeto extends GravityActor{

    Bario b;
    Sprite gs;
    boolean stage2 = false;
    int lifes = 3;
    Random r = new Random();
    int speed = 3;

    public Carpeto(Bario bario){
        b = bario;
        gs = new Sprite(new GreenfootImage("groundshadowevil.png"));
    }

    public void act(){
        
        if(!stage2){
            boolean move = false;
            if(r.nextInt(20) == 0) move = true;

            if(move){
                int bx = b.getX();
                int by = b.getY();
                int cx = getX();
                int cy = getY();

                if(cy != by){
                    if(cy - by > getImage().getHeight()/2){
                        setLocation(getX(), cy - 30);
                    } else if(cx - bx < getImage().getWidth()/2) {
                        setLocation(getX(), cy + 30);
                    }
                }
                if(cx != bx){
                    if(cx - bx > 0){
                        setLocation(cx - 30, getY());
                    } else {
                        setLocation(cx + 30, getY());
                    }
                }
            }

            gs.setLocation(getX(), getY() + getImage().getHeight() / 2);
        }

        if(stage2){

            int bx = b.getX();
            int by = b.getY();
            int cx = getX();
            int cy = getY();

            if(jump) setLocation(getX(), getY() - 15);

            if(getObjectsAtOffset(0, getImage().getHeight()/2, Ground.class).size() == 0)jump = true;

            if(cy - by > getImage().getHeight()) jump = true;

            if(cx != bx){
                if(cx - bx > getImage().getWidth()/2){
                    setLocation(bx - speed, getY());
                } else if (cx - bx < getImage().getWidth()/2) {
                    setLocation(cx + speed, getY());
                }

            }
            
            if(getY() > 375) jump = true;

            speed = 3;
            gravity();
        }
        
        if(r.nextInt(40) == 10){
                Blob blob = new Blob(b);
                getWorld().addObject(blob, getX(), getY());
            }

    }    

    public void hit(){
        lifes--;
        if(lifes == 2)gs.getImage().setTransparency(128);
        if(lifes == 1)gs.getImage().setTransparency(64);
        if(lifes == 0){
            getWorld().removeObject(gs);
            stage2 = true;
        }
    }
}

```
</details>

Die Klasse `Carpeto` ist eine Erweiterung der `GravityActor` Klasse.  
Im Konstruktor wird Carpetos fliegender Teppich (ein `Sprite`) erstellt und `bario` auf den "aktuellen" `Bario`  gesetzt.
Carpetos Verhalten variiert, anfangs (`stage2 = false`) bewegt er sich nur bei ungefär jedem zwanzigsten Durchlauf, dann jedoch sehr weit. Seine Bewegungsrichtung wird dabei durch seine relative Position zu `bario` entschieden. Wenn er sich auf einer anderen Höhe als Bario befindet, bewegt er sich 30 Felder in die Richtung in der sich Bario (`b`) befindet. Das gleiche gilt für die x-Richtung. Da Carpeto zu diesem Zeitpunkt noch seinen Teppich besitzt, wird dessen position auf Carpetos Position angepasst.  
  
Wenn sein Teppich allerdings schon zerstört wurde, `stage2` also zwingend auf `true` gesetzt ist (siehe `hit()`), verhält er sich ähnlich wie `Camelidae`. Da nun die Gravitation auch auf ihn gilt und er sich nicht mehr sprunghaft bewegt, müssen sich seine Bewegungsabläufe den Umständen anpassen. Am Anfang des neuen Bewegungsablaufs wird überprüft ob sich Carpeto in einem Sprung befindet. Falls ja wird er in y-Richtung nach oben bewegt. Anschließend wird überprüft ob sich unter ihm eine Plattform befindet, falls nicht wird `jump` auf `true` gesetzt, er springt also ab dem nächsten Durchlauf. Auch wenn er sich unter `bario` befindet oder seine y-koordinate höher als 375, er also unten auf dem Bildschirm ist wird `jump` auf `true` gesetzt.  
Anschließend bewegt er sich in die Richtung von Bario (`b`), falls er sich nicht bereits mit ihm überschneidet.  
Wie bei `Bario` wird seine Geschwindigkeit wieder auf den Ursprungswert (3) gesetzt und `gravity()` aufgerufen.  
  
Unabhängig von `stage2` generiert er bei ungefär jedem 40sten Durchlauf ein `Blob`, welches auf Bario (`b`) zielt.  
  
Die Funktion `hit()` zieht Bario eins seiner 3 Leben ab. Seine aktuellen Leben kann man an der Transparenz seines Teppiches erkennen, welche bei jedem Abzug von einem Leben abnimmt. Wenn seine Anzahl an Leben `lifes` 0 beträgt wird `stage2` auf `true` gesetzt und sein Teppich entfernt. `hit()` wird in `Rocket` aufgerufen.
</details>
<!--- Ende Carpeto                                                                                                      -->


<!--- Camelidae                                                                                                      -->
<details>
    <summary>Camelidae</summary>
    
<details>
    <summary>Klasse</summary>
    
```java
import greenfoot.*; 
import java.util.List;

public class Camelidae extends GravityActor{

    Actor target;
    boolean evil = true;
    int speed = 2;
    GreenfootImage camelimage = new GreenfootImage("camel.png");
    GreenfootImage alpacaimage = new GreenfootImage("Alpaca.png");

    public Camelidae(Actor t){
        target = t;
    }

    public void act(){
        gravity();
        if(getWorld() == null) return;

        int tx = target.getX();
        int ty = target.getY();
        int cx = getX();
        int cy = getY();

        if(jump) setLocation(getX(), getY() - 18); 

        if(getObjectsAtOffset(0, getImage().getHeight()/2, Ground.class).size() == 0)jump = true;

        if(cy - ty > getImage().getHeight()) jump = true;

        if(cx != tx){
            if(cx - tx > getImage().getWidth()/2){
                setLocation(cx - speed, getY());
            } else if (cx - tx < getImage().getWidth()/2) {
                setLocation(cx + speed, getY());
            }

        }

        speed = 2;

        if(evil){
            if(getOneIntersectingObject(Bario.class) != null){
                Bario bario = (Bario) target;
                bario.speed = 1;
                speed = 0;
            }
        } else {
            if(getOneIntersectingObject(Carpeto.class) != null){
                Carpeto carpeto = (Carpeto) target;
                carpeto.speed = 1;
                speed = 0;
            }
        }

    }

    public void setEvil(boolean e){
        evil = e;
        MyWorld w = (MyWorld) getWorld();
            
        if(evil){
            target = w.getBario();
            setImage(camelimage);
        }
        
        if(!evil){
            target = w.getCarpeto();
            setImage(alpacaimage);
        }
    }
    
    public boolean isEvil(){
        return evil;
    }
}
```
</details>

Die Klasse `Camelidae` ist eine Erweiterung der `GravityActor` Klasse.  
Im Konstruktor wird `target` definiert, was zu Anfang Bario entspricht.  
In der `act()` wird als erstes `gravity()` aufgerufen. Falls das Kamel dabei entfernt wird ist `getWorld() == null` `true` und die Funktion wird beendet, da sonst eine `NullPointerException` auftritt, da das Kamel nicht mehr in der `MyWorld` ist.  
Wie bei `Carpeto` wird überprüft ob `jump` ` true` ist, falls ja wird es auf der nach oben bewegt. Wenn es keinen Boden unter sich hat oder unter `target` ist wird `jump = true` gesetzt.  
Anschließend wird das Kamel auf der x-Ebene in Richtung von `target` bewegt, falls sie sich nicht bereits überschneiden.  
Das Kamel kann entweder böse (`evil = true`) oder gut (`evil = false`) sein. Falls es böse ist und sich mit Bario überschneidet wird `bario.speed` auf 1 und (`this.`)`speed` auf 0 gesetzt. Falls es gut ist passiert dasselbe mit Carpeto.  
  
Die Funktion `setEvil(boolean e)` setzt `evil` auf `e` und passt anchließend `target` an. Falls es böse ist wird das Ziel auf Bario gesetzt, falls es gut ist auf Carpeto. Außerdem wird das bild angepasst um den Spieler einen Überblick zu ermöglichen ob Das Kamel böseoder gut ist. Die Alpacas sind auf Barios Seite, die Trampeltiere (hier camel genannt) sind auf Carpetos Seite.  
  
Die Funktion `isEvil()` gibt `evil` zurück.

</details>
<!--- Ende Camelidae                                                                                                      -->


<!--- Rocket                                                                                                      -->
<details>
    <summary>Rocket</summary>
    
<details>
    <summary>Klasse</summary>
    
```java
import greenfoot.*;  // (World, Actor, GreenfootImage, Greenfoot and MouseInfo)
import java.util.List;

public class Rocket extends Actor{
    int rocket = 0;
    MyWorld w;

    public void addedToWorld(World world){
        w = (MyWorld) world;
    }

    public void act() {
        rocket += 1;

        Camelidae camelidae = (Camelidae) getOneIntersectingObject(Camelidae.class);
        if(camelidae != null && camelidae.isEvil()){
            camelidae.setEvil(false);
            w.removeRocket(this);
            return;
        }

        Carpeto carpeto = (Carpeto) getOneIntersectingObject(Carpeto.class);
        if(carpeto != null){
            if(!carpeto.stage2){
                carpeto.hit();
                w.removeRocket(this);
                return;
            } else {
                carpeto.speed = 0;
                carpeto.jump = false;
            }

        }

        if(rocket<20){
            move(6);
        } else if (rocket >= 20 && rocket <25) {
            turn(-36);
        } else if(rocket != 45){
            move(6);
        } else {
            w.removeRocket(this);
        }

        
    }    
}
```
</details>

Sobald die `Rocket` zur Welt hinzugefügt wurde, wird `w` auf die aktuelle Welt vom Typ `MyWorld` gesetzt. Die `MyWorld` ist für den Cooldown und die Verfügbarkeit der `Rocket` zuständig (siehe MyWorld).  
In der `act()` wird der Integer `rocket` bei jedem Durchlauf um 1 erhöht. Anschließend wird geprüft ob die Rakete sich mit einem `Camelidae` überschneidet und ob dieses ggf. böse ist. Falls ja wird die Rakete entfernt, das `Camelidae` gut (`evil = false`) und die Funktion beendet.  
Anschließend wird überprüft ob sich die Rakete mit Carpeto überschneidet, falls ja wird überprüft in welcher Phase sich Carpeto befindet (`stage2`). Wenn er sich noch in der ersten Phase befindet wird `Carpeto.hit()` aufgerufen, die Rakete entfernt und die Funktion beendet. Wenn er sich nicht mehr in der ersten Phase befindet, also `stage2 = true` gilt wird `carpeto.speed` auf 0 und `carpeto.jump` auf false gesetzt. `carpeto` bleibt also in der Luft stehen, solange er sich mit der Rakete überschneidet.  
Im letzten Teil wird die Bewegung der Rakete gesteuert. Bei den ersten 20 Durchläufen bewegt sie sich geradeaus, danach dreht sie sich ohne sich zu bewegen und fliegt nach der Drehung wieder geradeaus. Sobald sie sich wieder am Ausgangspunkt befindet, `rocket` also 45 ist, wird sie entfernt.

</details>
<!--- Ende Rocket                                                                                                      -->


<!--- Blob                                                                                                      -->
<details>
    <summary>Blob</summary>
    
<details>
    <summary>Klasse</summary>
    
```java
import greenfoot.*;  // (World, Actor, GreenfootImage, Greenfoot and MouseInfo)
import java.util.Random;
import java.lang.Math;
import java.util.List;

public class Blob extends Actor{
    
    int x;
    int y;
    Actor target;
    Random r = new Random();
    boolean remove = false;
    
    public Blob(Actor target){
        x = target.getX();
        y = target.getY();
    }
    
    public void act(){
        turnTowards(x, y);
        move(r.nextInt(5));
        setRotation(r.nextInt(360));
        
        List<Actor> list= getIntersectingObjects(null);
        for(Actor a : list){
            if (a instanceof Ground){
                Ground g = (Ground) a;
                g.lowerTransparency(100);
                remove = true;
                if(g.getWorld() != null && r.nextInt(10) == 3){
                    Camelidae c = new Camelidae( ((MyWorld) getWorld()).getBario() );
                    getWorld().addObject(c, g.getX(), g.getY());
                }
            }
            
            if(a instanceof Camelidae){
                Camelidae c = (Camelidae) a;
                c.setEvil(true);
                remove = true;
            }
        }
        
        if(getX() == x && getY() == y) remove = true;
        
        if(remove) getWorld().removeObject(this);
    } 
    
}
```
</details>

`Blob` ist die Waffe von Carpeto. Im Konstruktor werden die aktuelle x und y-Koordinate eines `Actor` als `x` und `y` gespeichert.  
In der `act()` wird der Blob in Richtung von `x` und `y` gedreht und bewegt sich anschließend um einen zufälligen Wert zwischen 0 und 4. Anschließend wird die Rotation auf einen zufälligen Wert zwischen 0 und 359 gesetzt.  
Danach wird überprüft ob der `Blob` sich mit beliebigen Objekten überschneidet. Falls ja wird überprüft um was für Objekte es sich handelt. Wenn es ein Objekt des Typs `Ground` ist, wird dessen Transparenz mit `g.lowerTransparency(100)` gesenkt und `remove` auf `true` gesetzt. Wenn der `Ground g` danach noch existiert besteht eine 1:20 Chance dass auf ihm ein `Camelidae` auftaucht.  Wenn es ein Objekt des Typs `Camelidae` ist wird dieses böse und `remove` auf `true` gesetzt.  
Es wird überprüft ob der `Blob` seine Zielkoordinaten erreicht hat, falls ja wird `remove` auf `true` gesetzt. Am Ende wird überprüft ob `remove == true` gilt, wenn das der Fall ist wird der `Blob` entfernt.


</details>
<!--- Ende Blob                                                                                                      -->


