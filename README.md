<h1> Bi-Color LED Matrix mit dem Arduino </h1>

<h3> Inhalt </h3>
<ul style="list-stlye-type:none">
<li><a href="#EINl">1. Einleitung</a></li>
<li><a href="#INBE">2. Inbetriebnahme des Arduino</a>
</li>
<li><a href="#MATR">3. Die LED-Matrix</a>
<ul> 
<li><a href="#ZUSA">3.1 Zusammenbau </a></li>
<li><a href="#TEST">3.2 Test </a></li>
</ul> 
</li>
<li><a href="#PROG">4.Programme mit der Matrix</a>
<ul>
<li><a href="#LICH">4.1 Die Lichtorgel </a></li>
<li><a href="#52">4.2 Nachrichtenticker</a></li>
<li><a href="#53">4.3 Snake </a></li>
</ul>
</li>
<li><a href="#ANHA">5. Anhang</a>
<ul>
<li><a href="#LIBR">5.1 Installieren von Libraries </a></li>
<li><a href="#SOUR">5.2 Quellen</a></li>
<li><a href="#CODE">5.3 Links zum Code </a></li>
</ul>
</li>
</ul>

<h3 id="EINL">Einleitung </h3>
<p>
Der Arduino ist ein Microcontrollerboard, das auf dem ATmega328P basiert (<a href ="http://www.atmel.com/images/Atmel-8271-8-bit-AVR-Microcontroller-ATmega48A-48PA-88A-88PA-168A-168PA-328-328P_datasheet_Complete.pdf">Weitere Informartionen </a>) Er verfügt über 14 digitale Ein-/ bzw. Ausgänge, 6 analoge Eingänge, einen USB-Anschluss, einen Stromanschluss, einen 16 MHz Quartzkristall (zur Zeitbestimmung) und einen Reset-Knopf. Mit dem Arduino kann man LEDs, Motoren oder ähnliches anschließen und diverse Sensoren auslesen. Auch kleine LCD-Displays oder LED-Matrizen kann man ansteuren und Dinge auf ihnen anzeigen.<sup><a href="#A1">[1]</a></sup> Im Folgenden wird sich auf die 8x8 Bicolor LED Matrix von Adafruit bezogen, die man sich  <a href = "https://www.adafruit.com/product/902">hier </a> bestellen kann.<sup><a href="#A2">[2]</a></sup>
</p>
<h3 id="INBE">Inbetriebnahme des Arduino </h3>
<p>
Um den Arduino in Betrieb zu nehmen ist lediglich ein <a href = "https://img.conrad.de/medias/global/ce/9000_9999/9800/9860/9868/986899_LB_00_FB.EPS_1000.jpgUSB-A">USB-A auf USB-B </a> Kabel nötig, das mitgeliefert wurde. Um Programme für den Arduino zu schreiben und sie auf den Arduino zu überspielen, benötigt man die Arduino Software. Downloadlink: <a href = "https://www.arduino.cc/download_handler.php">Windows, </a> <a href = "https://www.arduino.cc/download_handler.php">Mac, </a> <a href = "https://www.arduino.cc/download_handler.php">Linux </a> Für die Projekte sind lediglich Grundkentnisse des Arduinos erforderlich. 
</p>
<h3 id="MATR">Die LED-Matrix </h3>
<p>
Die LED-Matrix besteht aus ingesamt 128 LEDs, von denen 64 rot und 64 grün sind. Sie können abwechselnd oder zusammen leuchten, sodass die Farben rot, grün und gelb/orange dargestellt werden können. Wie zu erkennen ist, verfügt die Matrix lediglich über 24 Pins, das heißt, dass auf einen Pin mehr als fünf LEDs entfallen. Um dennoch alle LEDs korrekt anzusteuern, kommt der Microcontroller ins Spiel. Mit einer Technik namens <a href = "https://de.wikipedia.org/wiki/Multiplexverfahren">Multiplexing </a> ist es möglich, mehrere Signale gebündelt zu übermittlen, um so die Übertragungsstrecke zu optimieren. Die Multiplexarbeit verrichten der Arduino und der Microcontroller, die als Sender und Empfänger die Signale erst bündeln und dann wieder aufspalten.
</p>
<h4 id="ZUSA">Zusammenbau </h4>
Damit alles korrekt funktioniert, ist es wichtig, dass Mircocontroller und Matrix korrekt zusammengelötet sind. Falls es das erste mal Löten sein sollte, ist hier ein kleines <a href = "http://mightyohm.com/files/soldercomic/translations/DE_SolderComic.pdf">Tutorial</a>.
</p>
<p><img src="images/allignment.jpeg" alt="allignment" width="240" height="192" style="margin:10px" align="right"></p>
<p> <h5>1.</h5> </p> 
<p>
Man nimmt nun die Matrix zur Hand, und steckt sie auf den Microcontroller. <b> WICHTIG!!! </b> In einer Ecke ist statt einem Quadrat ein Kreis. Auf diese Seite muss die Seite der Matrix, auf die der Text steht (siehe Bild).
</p>
<p></p>
<p><h5>2.</h5></p>
<p>
Jetzt dreht man die Matrix mit dem Chip auf der Rückseite um und lötet alle 24 Pins fest. Anschließend knipst man die langen Enden ab um die Matrix nacher besser auf einem Breadboard platzieren zu könnnen. 
</p>
<p>
<div>
<img src="images/solder1.jpeg" alt="solder1" width="240" height="192" style="margin:10px" float="left">
<img src="images/solder2.jpeg" alt="solder2" width="240" height="192" style="margin:10px" float="left">
<img src="images/solder3.jpeg" alt="solder3" width="240" height="192" style="margin:10px" float="right">
</div>
</p>
<p> <h5> 3. </h5> </p>
<p>
Anschließend lötet man das 4-Pin-Stück an die Platine. Damit das einfacher geht, steckt man diese Stück zuvor mit den <b> langen </b> Pins in ein Breadboard und platziert dann die Matrix darauf. Nun lötet man die vier Pins fest. 
</p>
<div>
<img src="images/4pin1.jpg" alt="4pin1" width="240" height="192" style="margin:10px" float="left">
<img src="images/4pin2.jpg" alt="4pin2" width="240" height="192" style="margin:10px" float="left">
<img src="images/4pin3.jpeg" alt="4pin3" width="240" height="192" style="margin:10px" float="left">
</div>
<p> <h5>4.</h5> </p>
<p>
Zuletzt muss die Matrix noch an den Arduino angeschlossen werden. Dafür benötigt man vier Jumper-Kabel, die man folgendermaßen verbindet:
</p>
<table>
<thead>
<tr>
<th>Oberseite Matrix</th>
<th align="center">Unterseite Matrix</th>
<th align="center">Pin am Arduino</th>
</tr>
</thead>
<tbody>
<tr>
<td>+</td>
<td align="center">VCC</td>
<td align="center">5V</td>
</tr>
<tr>
<td>-</td>
<td align="center">GND</td>
<td align="center">GND</td>
</tr>
<tr>
<td>D</td>
<td align="center">SDA</td>
<td align="center">A4</td>
</tr>
<tr>
<td>C</td>
<td align="center">SCL</td>
<td align="center">A5</td>
</tr>
</tbody>
</table>
<h4 id="TEST">Test </h4>
p><img src="images/succes.JPG" alt="succes" width="240" height="192" style="margin:10px" align="right"></p>
<p>
Jetzt kann man die Matrix testen: Hierzu einfach den Test-Code <a href = "https://github.com/OleMausS/LED-Matrix-Arduino/blob/master/code/Bicolor_Matrix_Test.ino">herunterladen</a> und ausführen. Die Matrix sollte nun den Text <i> Du hast es geschafft! </i> in grün, gelb und rot anzeigen. Anschließend wird ein grüner Smiley eingeblendet. 
<b>ACHTUNG!</b> Damit die Martix funktioniert, müssen zuerst die beiden Bibliotheken von Adafruit heruntergeladen werden: <a href = "https://github.com/adafruit/Adafruit-GFX-Library/archive/master.zip">Adafruit GFX </a> und <a href = "https://github.com/adafruit/Adafruit_LED_Backpack/archive/master.zip">Adafruit LED Backpack </a>. Wie man diese korrekt installiert, siehe <a href="#LIBR"> hier. </a>
</p>
<h3 id="PROG">Programme mit der Matrix </h3>
<p>
Die Matrix kann, wie bereits gesehen, alles mögliche Anzeigen. Damit das "Backpack" die Befehle richtig umsetzt, muss man zuerst die erforderlichen libraries importieren. Dies geschieht über der Befehl <code>#include "Name_der_Library.h</code>. In diesem Falle wären das  <i> Adafruit_GFX.h, Adafruit_LEDBackpack.h und Wire.h </i>. Danach trägt man ein um welches LED-Zubehör es sich handelt: <code>Adafruit_BicolorMatrix matrix = Adafruit_BicolorMatrix();</code>
Im Setup startet man den seriellen Monitor mit dem Befehl <code>Serial.begin(9600);</code>. Optional kann man noch einen Log einfügen, der den Programmstart makiert. Beispiel: <code>Serial.println("Programmstart");</code>. Ganz wichtig ist die Eingabe der IC2-Adresse, was mit dem Befehl <code>matrix.begin(0x70);</code> durchgeführt wird. Dabei ist die Adresse immer 0x70 für die erste Matrix die verbunden wurd, sind zwei verbunden, hat die erste die Adresse 0x70 und die zweite 0x71 und so fort. Ist alles richtig konfiguriert, kann es mit dem Programmieren losgehen. Ein fertiges Schema kann <a href="LED-Matrix-Arduino/code/Standard_Schema.ino">hier</a> heruntergeladen werden. 
</p>
<h4 id="LICH">Die Lichtorgel </h4>
<p>
Dies ist keine <a href="https://de.wikipedia.org/wiki/Lichtorgel"> Lichtorgel</a> im eigentlichen Sinne, sondern lediglich eine Darstellung von Lichtabläufen, Formen und Farben. Man kann jedoch mit verschiedenen Befehlen, viele Effekte darstellen. Um etwas auf der Matrix anzuzeigen verwentet man den Befehl <code>matrix.writeDisplay();</code> und um das was auf dem Bildschirm zu sehen ist zu entfernen, <code>matrix.clear();</code>. Wenn man die Matrix nicht "cleared", und erneut etwas "writed", dann wird es einfach auf das vorhandene projektiert. <b>ACHTUNG!</b> Führt man den Befehle <code>matrix.writeDisplay();</code> nicht aus, wird nichts auf der Matrix geändert!
</p>
<h5> Einzelne Pixel </h5>
<p><img src="images/bitmap.JPG" alt="bitmap" width="200" height="172" style="margin:10px" align="right"></p>
<p>
Um einzelne Pixel zum Leuchten zu bringen, nutzt man den Befehl <code>matrix.drawPixel(x,y, LED_COLOR);</code>. X und Y ersetzt man dabei durch die entsprechenden Koordinaten. <b> ACHTUNG!</b> Die Koordianten beginnen bei (0;0) und enden bei (7;7). Um die Suche nach den richtigen Koordinaten zu vereinfachen, habe ich eine Übersicht (siehe Bild) hergestellt. COLOR steht für die Farbe, wobei die Werte YELLOW(für gelb/orange), GREEN(für grün) und RED(für rot) eingesetzt werden können. Alle <code>matrix.drawPixel(x,y, LED_COLOR);</code> Befehle, die vor einem <code>matrix.writeDisplay();</code> Befehl stehen, werden simultan ausgeführt, möchte man eine Pause einbauen, muss man den Befehl <code>delay(t in ms);</code> mit einbauen. Falls komplexere Formen dargestellt werden Sollen, sollte man auf <a href="#BITM">Bitmaps</a> zurückgreifen. 
<p> Beispiel für einen roten Punkt bei (1;4): <code>matrix.drawPixel(1,4, LED_RED);</code></p>
</p>
<h5> Linien </h5>
<p>
Linien werden ähnlich wie Pixel programmiert. Ihr Befehl lautet <code>matrix.drawLine(x1,y1, x2,y2, LED_COLOR);</code>. Die Koordinaten (x1;y1) geben dabei den Startpunkt und (x2;y2) den Endpunkt der Linie an. So können die Linien beliebig lang und ausgerichtet sein. COLOR gibt wieder die Farbe (YELLOW,GREEN, oder RED) an. Alle Linien, die vor einem <code>matrix.writeDisplay();</code> Befehl stehen, werden parallel eingeblendet. Baut man kleine Pausen mit ein, kann man einen Übergang etc. bauen. 
<p>Beispiel für eine Grüne Linie von (1;2) bis (5;6):<code>matrix.drawLine(1,4, 5,6, LED_GREEN);</code></p>
</p>
