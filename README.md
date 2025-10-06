# Sensor Storytelling Hackathon

Dieses Repository dient als Referenz für die Sensor Storytelling Hackathon Website. Im Source Ordner sind die Dokumente gesammlt und unten mit Kommentaren versehen. 

## Hackathon


Der Sensor Storytelling Hackathon widmet sich den Fragen: Welche neuen Wege bietet moderne 
Sensortechnologie, um Bewegung, Klang und 
Raumgestaltung auf der Bühne zu verknüpfen? 
Wie können interaktive Sensortechnik im Objekt- und Figurentheater und in 
partizipativen Theaterformaten eingesetzt werden? 
Welche Erlebnisqualitäten werden damit möglich?

Die Teilnehmenden des Hackathons haben sich in drei Gruppen aufgeteilt: [Screen](#Screen), [Sound](#Sound) und [Space](#Space).

Die Idee für den Hackathon entwickelte sich aus dem Projekt "Interface Marionette". Eine Marionette die mit Hilfe von IMU Sensoren in der Lage ist, ihre Bewegungen an eine digitale Marionette zu übertragen. 

![alt text](src/GENERAL/Hackathon-24.jpg)

<code style="color : red">Bei der Auswahl der Fotos habe ich versucht zu zeigen wie sich die einzelnen Projekte entwickelt haben. Wenn wir die Personen noch mehr im Vordergrund haben wollen kann ich auch nochmal durschschauen.</code><br/>
<code style="color : red">Ansonsten ist ein bisschen die Frage, was wir alles teilen wollen/können. Also sollen Code Snippets auch hochgeladen werden? Oder geht es nur darum einen Eindruck vom Hackathon zu bekommen?</code>

## Screen
![alt text](<src/SCREEN/3D Models/Renderings/room.png>)
### We are Blender

A Blender tutorial comes to life on stage. Six performers in an office setting collaboratively model a new 3D character – but instead of using computers, they become the software itself.


Each person embodies a single tool: one controls object rotation, another the camera position, someone clicks the mouse, another switches between edit and sculpt mode. Simple actions become full-body movements – a mouse click transforms into pulling on a power strip, gestures are exaggerated, everyday objects are hacked into interfaces.

The hidden complexity of our everyday interactions with technology is exposed by the performance. It humorously mirrors human cognition and behavior with computer interfaces, making visible the effort behind seemingly simple digital tasks.
The team collaboratively creates a digital character, evoking the traditions of puppet theater, in which several actors bring a single figure to life. The real theater space exists as a 3D scan within Blender, blurring the barriers between physical and virtual worlds.

![alt text](src/SCREEN/Fotos/Hackathon-009.jpg)|![alt text](src/SCREEN/Fotos/Hackathon-19.jpg)
|:---------:|:----------:|
![alt text](src/SCREEN/Fotos/Hackathon-054.jpg)|![alt text](src/SCREEN/Fotos/Hackathon-32.jpg)<br/>

![alt text](<src/SCREEN/3D Models/Renderings/ball.png>)<br/>
### Technical Description:

A set of ESP32 microcontrollers equipped with IMU sensors were used to capture movement and rotation data from various real objects on stage. The data was transmitted to a central Blender instance running on our server via OSC protocol, using the AddRoutes plugin (https://blender-addons.org/addroutes/). 
A 3D room scan was generated with Polycam (https://poly.cam/) and subsequently scaled to match real-world dimensions. In a separate Unity application, both virtual environments (Blender and Unity) were spatially aligned using spatial anchors, enabling the use of a Head Mounted Display as a virtual camera within the Blender scene. 
Additionally, several custom scripts were developed to handle virtual clicking and mouse movement, allowing for big clicks, beautiful screen interactions and smooth modeling operations.


![alt text](src/SCREEN/Fotos/Hackathon-77.jpeg)|![alt text](src/SCREEN/Fotos/Hackathon-043.jpg)
|:---------:|:----------:|
![alt text](src/SCREEN/Fotos/Hackathon-23.jpg)|![alt text](src/SCREEN/Fotos/Hackathon-53.jpg)<br/>
### Credits:

Edda Rabold<br />
Helene Kummer<br />
Ronja Lindemann<br />
Ruxin  Liuu<br />
Julian Jungel<br />
Fabian Töpfer


## Sound

### The Word for World is Forrest

Hat hier jemand Bedarf zu flanieren?
Im Raum befindet sich ein Flanierkreis. Mehrere Menschen können darauf gleichzeitig flanieren. Und es müssen nicht immer die gleichen Menschen sein.

The text passage that the audience can hear by walking is from FLEXEN. Flâneusen* schreiben Städte by Lea Sauer, Mia Göhring, Özlem Özgül Dündar, Ronya Othmann (Hg.)
https://www.verbrecherverlag.de/shop/flexen-flaneusen-schreiben-staedte/ 

The song is not by Taylor Swift but by Joni Mitchell, "Big Yellow Taxi":
https://www.youtube.com/watch?v=94bdMSCdw20 

The title of our project, which we agreed upon 10 minutes before presenting our project, is inspired by the title of Ursula K. Le Guin’s novel which deals with ideas of preserving vs. conquering novel cultures and ecologies.
https://en.wikipedia.org/wiki/The_Word_for_World_Is_Forest


![Flaneur](https://github.com/georgesipp/sensorstorytelling/blob/main/src/SOUND/flaneur_wikipedia_screenshot.png "Flaneur")

<code style="color : red">Für Github habe ich einen Wikipedia Screenshot gemacht. Für die Website ist es vielleicht charmanter die Wikipedia Page einzubetten anstatt nur den Text einzufügen.</code>


|![alt text](<src/SOUND/Circuit/Screenshot 2025-09-26 at 18.17.05.png>) | ![alt text](src/SOUND/Fotos/Hackathon-02.jpeg)|
|:---------:|:----------:|
|![alt text](src/SOUND/Fotos/Hackathon-031.jpg)                         |   ![alt text](<src/SOUND/Circuit/Screenshot 2025-09-26 at 18.17.12.png>)|

### Technical Description

#### HARDWARE (SENSORS + ARDUINO)
The flanierkreis is made up of 24 handmade pressure sensors similar to these:
https://www.kobakant.at/DIY/?p=429
The sensors are made from copper, alu and silverized nylon tapes stuck to plastic sheets with a layer of Velostat piezoresistive plastic on top.
One side of each sensor is connected to a digital pin on an Arduino Mega, the other side of all sensors is inter-connected to analog pin A0. The pressure range of the sensors is around 10,000 - 200 Ohm. We used a voltage dividing resistor of 1K between A0 and +5V to detect a person stepping on a sensor.

#### ARDUINO CODE
The code on the Arduino parses through the 24 pressure sensors, similar to the code for reading this pressure-sensor matrix:
https://www.kobakant.at/DIY/?p=7943

The Arduino code sends out 24 comma separated values that each represent the 10bit pressure value for each sensor, and as a last 25th value the arduino sends a number that should be interpreted as follows:
 100 - nobody on the circle
 0 - people walking on the circle
 1-99 - # people standing still on the circle


|![alt text](<src/SOUND/Circuit/Screenshot 2025-09-26 at 18.17.26.png>) | ![alt text](src/SOUND/Fotos/Hackathon-61.jpg)|
|:---------:|:----------:|
|![alt text](src/SOUND/Fotos/Hackathon-96.jpg)                         | ![alt text](src/SOUND/Fotos/Hackathon-40.jpg)|
|![alt text](src/SOUND/Fotos/Hackathon-13.jpg)                         | ![alt text](src/SOUND/Fotos/Hackathon-20.jpg)|
<br/>

[Forestwalk](https://github.com/user-attachments/files/22621128/forestwalk.mp3)<br/>
<code style="color : red">Ich hab die Atmo und ein paar Schritte zusammengeschnitten. Für die Website wäre es natürlich gut wenn es direkt im Browser gespielt wird.</code>

![alt text](src/SOUND/maxmsp_screenshot.png)<br/>

### Credits:
Jonas Olbrich <br />
Lisa Passing <br />
Hannah Perner-Wilson <br />
Laura Pföhler <br />
Jan Schulten


## Space

![alt text](src/SPACE/Ideensammlung.png)

|![alt text](src/SPACE/ESP8266+BNO055.jpg) | ![alt text](src/SPACE/HID.jpg) | ![alt text](src/SPACE/MobilePlatform.jpg)|
|:---:|:---:|:---:|


[Wesen-Objektsubjekt](https://github.com/user-attachments/files/22635362/wesen-objektsubjekt.mp3)
<code style="color : red">Hier das gleiche wie bei der Waldatmo.</code>



![alt text](src/SPACE/Fotos/Hackathon-08.jpg) | ![alt text](src/SPACE/Fotos/Hackathon-43.jpg)
|:---------:|:----------:|
![alt text](src/SPACE/Fotos/Hackathon-06.jpeg) | ![alt text](src/SPACE/Fotos/Hackathon-25.jpg)
![alt text](src/SPACE/Fotos/Hackathon-071.jpg) | ![alt text](src/SPACE/Fotos/Hackathon-88.jpg)

![alt text](src/SPACE/Baustellen.png)

![alt text](src/SPACE/Fotos/Hackathon-10.jpg) | ![alt text](src/SPACE/Fotos/Hackathon-48.jpg)
|:---------:|:----------:|
![alt text](src/SPACE/Fotos/Hackathon-18.jpg) | ![alt text](src/SPACE/Fotos/Hackathon-11.jpg)