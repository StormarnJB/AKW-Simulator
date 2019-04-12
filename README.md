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

Das Spiel „Bario“ handelt von einem Alpakafarmer, der von dem bösen „Carpeto“ verfolgt wird und auf fliegende Teppiche springen muss um zu überleben. Carpeto möchte alle Camelidae (Kamele, Lamas, Alpakas etc.) unterwerfen und so auch die Alpakas von Bario. Dieser kann sich mithilfe einer Rakete, die er als Hobby-Ingenieur entwickelt hat, zur Wehr setzten und Carpeto angreifen, fällt Bario allerdings herunter hat Carpeto gewonnen und das Spiel ist vorbei. Carpetos Angriffe bestehen darin die Teppiche mit seinen Angriffen zu zerstören, sodass Bario leichter herunterfallen kann. Die Teppiche verschwinden ebenfalls wenn man sich zu lange auf einem aufhält. Carpeto kann besiegt werden indem man ihn mit der Rakete abschießt. Schafft man dies fällt er von seinem individuell gesteuerten Teppich (lebt aber noch weiter) und kann endgültig besiegt werden indem er hinunterfällt. Das gelingt durch die alle 10 Sekunden erscheinenden Kamele, die ebenfalls mit der Rakete abgeschossen werden können und sich so zu Alpakas verwandeln. Die Kamele gehen auf Bario los, verlangsamen ihn und lassen die Teppiche schneller verschwinden, die Alpakas tun das gleiche bei Bario. Carpeto kann die Alpakas allerdings auch wieder zurück zu Kamelen verwandeln die dann wieder auf Bario losgehen. Wenn Carpeto herunterfällt ist er besiegt, das Spiel ist vorbei und man hat gewonnen.
Das Spiel kann nach dem Scheitern direkt durch einen Linksklick neugestartet werden, sodass man nicht jedes Mal wieder die Einleitung anschauen muss.

#### Greenfoot <a name="Greenfoot"></a>

Greenfoot ist eine interaktive Java-Entwicklungsumgebung, die primär für Ausbildungszwecke entwickelt wurde. Die Erstveröffentlichung war 2006. Sie erlaubt die einfache Entwicklung zweidimensionaler graphischer Anwendungen wie z. B. Simulationen und Spiele.
Die Entwickler geben als Zielgruppe "Programmieranfänger ab 15 Jahren aufwärts" an. Da die unterstützte Programmiersprache Standard-Java ist, können allerdings auch recht komplexe und anspruchsvolle Projekte implementiert werden.
Greenfoot-Szenarios können auf die Greenfoot Gallery exportiert werden, wo sie live ausgeführt werden können.
Die Hauptattraktion für Lernende ist, dass sehr schnell und interaktiv animierte graphische Projekte implementiert werden können. Einfache Spiele sind selbst für Anfänger nach kurzer Zeit erreichbar, was oft zu guter Motivation führt. Die Attraktion für Lehrende ist, dass Greenfoot wichtige Konzepte der objektorientierten Programmierpraxis gut illustriert. Klassen, Objekte, Vererbung, Methodenaufrufe und Objekt-Instanziierung sind für Benutzer sichtbar und erfahrbar. Diese konkrete Illustration abstrakter Konzepte unterstützt die Programmierlehre.


## Aufbau <a name="Aufbau"></a>

### Die Welten


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

Die `act()`Methode besteht aus 4 Teilen.  
Im ersten Teil wird überprüft ob der Nutzer die Leertaste drückt um so den Startbildschirm zu überspringen.  

Der zweite Teil ist für das Verhalten der am Anfang hinzugefügten Alpakas zuständig, da es sich bei den Alpakas um `Sprite` Objekte handelt, welche kein eigenes Verhalten besitzen wird dieses innerhalb der Welt definiert. Am Anfang der Klasse wurde der Integer i definiert, dieser wird in jedem Durchlauf um 1 erhöht und wird benutzt um den Ablauf der Animationen zu steuern.
In den ersten 400 Durchläufen der `act()` Methode bewegen die Alpakas sich jeweils um 0-2 Pixel, außerdem besteht eine 1:50 Chance dass die Alpacs sich drehen. Dafür werden die Alpacas um 180° gedreht, was jedoch dazu führt dass sie falsch herum sind, deshalb wird ihr Bild an ihrer vertikalen Achse gespiegelt.  
Im 401sten Durchlauf werden ihre Bilder auf ein nach links schauendes Alpaka gesetzt ('Alpaca.png' schaut nach rechts) und sie werden in Richtung des linken Bildschirmrands gedreht. 
In allen Durchläüfen danach bewegen sie sich um jewils zwei Felder (mit der im Konstruktor defnierten Seitenlänge von einem Pixel). Sobald sie den Bildschirmrand erreicht haben werden sie aus der Welt entfernt. Gleichzeitig wird durch `alpacasremoved` mitgezählt wie viele Alpakas bereits entfernt wurden. Sobald die Anzahl der entfernten Alpakas der Anzahl der anfangs hinzugefügten Alpakas entspricht wird das Spiel gestartet, indem die Welt zu `MyWorld` geändert wird.

Der dritte Teil ist für den restlichen Teil des Geschehens auf dem Bildschirm zuständig. Beim 121sten Durchlauf wird "Carpeto", der Bösewicht, vergrößert, gespiegelt und anschließend hinzugefügt. Im 226sten Durchlauf wird Carpetos Dialogtext hinzugefügt, im 401sten Barios Aufruf an seine Alpakas zu fliehen. Im 461sten Durchlauf wird Barios Text dann auf eine Antwort an Carpeto geändert.
![Start Bildschirm bei i > 460](https://github.com/StormarnJB/BarioTheGame/blob/master/Screenshots/StartScreen2.PNG)

</details>
