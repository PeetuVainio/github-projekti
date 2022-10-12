#
## 13.9.2022  
### Projektisuunnitelma  
#### Peetu Vainio, Joel Utriainen Ja Luca Lappalainen  
Tehty testejä Arduino UNO laitteella.  
-Blinkin Test  
-Temperature Sensor testi (DHT11)  
Tutustuttu Ardunon Käyttöön  
## 14.9.2022
Testailtu Arduino UNOlla erilaisia asioita  
-Temperature sensor  
-4 digit 7 segment LED display  
-Matrix 8x8 LED  
-Yritetty tehdä 4 digit 7 display lämpösensorin kanssa. (ei onnistunut)  
-Mikrofooni  
-distance sensor (ei toiminut)  
## 16.9.2022
Testailtu Ardunoa raspberryn kanssa  

lataa arduino IDE Raspiin  
Terminal:  
-Sudo apt install arduino =Lataa arduinon  
-Sudo adduser käyttäjänimi dialout  
pyserial_kirjasto  
-pip install pyserial / sudo pip3 install pyserial  
apt list --installed -> python3-serial   

Testataan toimiiko Arduino IDE oikein:  
-Simppeli koodi (Serial)  
-Arduino UNO  
-Com-port  
^
/dev/ttyACM0  
/dev/ttyUSB0  

Laitettu Arduino ja Python koodit raspiin  
Arduino:  

void setup() {  
  // put your setup code here, to run once:  
Serial.begin(9600);  
}  

void loop() {  
  // put your main code here, to run repeatedly:  
Serial.println("Heippa");  
delay(100);  
}  

Python:  

#!/usr/bin/env python3  
#kirjasto  
import serial  

if __name__ == '__main__':  
    #serialin kommunikaatioon alustamisseen kutsutaan muutamilla parametreillä  
    ser = serial.Serial('/dev/ttyACM0', 9600, timeout=1)  
    ser.reset_input_buffer()  

    while True:  
        if ser.in_waiting > 0:  
            line = ser.readline().decode('utf-8').rstrip()  
            print(line)  

Välkkyvä LED valo, joka on yhdistetty ardunosta serialiin  
-Ohjeet: https://forum.arduino.cc/t/blinking-an-led-from-a-raspberry-pi-gpio-signal/695120  

Testattiin Servo moottoria (ei saatu toimimaan)  
## 20.9.2022
apt-get-update, päivittää kaiken ajantasalle  
clear,tyhjentää taulukon  
date, kertoo päivämäärän ja ajan  
find/-name esimerkki.txt, etsii nimetyn tiedoston  
nano example.txt, pystyy muokata jotakin tiedostoa terminaalista  
poweroff, sammuttaa järjestelmän  
raspi-config,pääset muokkaamaan asetuksia  
reboot, käynnistää järjestelmän uudelleen  
shutdowm-h-now,sammuttaa järjestelmän nyt  
shutdown-h-01:22:, sammuttaa järjestelmän tiettyyn kellonaikaan  
startx, komento, jolla voidaan käynnistää x palvelin  
cat esimerkki.txt,yhdistää tiedostoja  
cd/abc/xyz,kopioi tiedoston tai hakemiston ja liittää sen määritettyyn paikkaan  
is-| ei löydy  
mkdir esimerkki_polku,luo hakemiston  
my XXX, ei löydy  
rm esimerkki,poistaa tiedoston  
scp user@10.0.0.32:/some/path/tiedosto.txt, lataa koneelta tietyn tiedoston raspberryyn  
touch example.txt,luo tiedoston tai muokkaa sitä  
ifconfig, verkkoliitännän tarkastelu komento  
iwconfig,langaton ifconfig komento  
iwlist wlan0 scan, skannaa langattoman tukiaseman  
iwlist wlan0I grep ESSID,ei löydy  
nmap,työkalu, jolla tutkia ja turvata nettiä  
ping,kertoo netin nopeuden  
wget :http://www.website.com/example.txt,vie tietylle nettisivulle  
cat/proc/meminfo,määrittää kuinka paljon muista löytyy  
cat/proc/partitions,näyttää dataa osoitteista  
cat/proc/verion,näyttää version  
df-h, näyttää tiedostojärjestelmän levytilastot  
df/,näyttää toedostojärjestelmän tietoja ja käytettävissä olevan tilan  
dpkg--get selections I grep XXX, ei löytynyt  
dpkg--get-selections,antaa luettelon kaikista pakettien nimisistä ja tilasta  
free, hostname-|, näyttää mem:it  
Isusb, näyttää USB- väylistä tietoja  
UP key,pääsee takasinpäin koodeissa, eli voi käyttää jo käytettyjä koodeja uudelleen  
vcgencmd measure_temp, kertoo järjestelmän lämpötilan vcgencmd get_mem arm&& vcgencmd get_mem gpu, kertoo gpu:n ja arm:in tilavuuden.  
### 21.9.2022
Tutustuttiin eri KTinker komentoihin pythonilla ja aloitettiin suomenlipun koodin tekemistä  
#### Esimerkkikoodi
import tkinter as tk = tunnistaa- tkinterin tk:na ja sitä rataa loputkin = koodit window = tk. Tk() lb=tk.Label(text="real python")= Tekstiksi tulee se, mitä suluissa lukee entry = tk.Entry()  
name=entry.get() = nimeksi tulee se, minkä kirjoitat = name lb.pack() = mahdollistaa lb:n käytön entry.pack()= mahdollistaa entryn käytön  
window.mainloop()  
### 23.9.2022
Suunniteltiin käyttöliittymää ja tehtiin sille graafinen ohjelmisto, saatiin myös projekti valmiiksi, joka aloitettiin 21-päivä, ja missä frame koodien avulla saatiin aikaiseksi suomenlippu  
#### Koodi
import tkinter as tk  

window = tk.Tk() = luo tyhjän ruudun  

frame123 = tk.Frame(master=window, width=50, height=50, bg="blue") = tekee framen ja sen korkeuden, leveyden ja värin  
frame123.pack(side=tk.RIGHT) = mahdollistaa framen käytön ja asettelee sen ruutuunsa  
frame134 = tk.Frame(master=window, width=50, height=50, bg="blue")  
frame134.pack(side=tk.RIGHT)  
frame145 = tk.Frame(master=window, width=50, height=50, bg="blue")  
frame145.pack(side=tk.LEFT)  
frame156 = tk.Frame(master=window, width=50, height=50, bg="blue")  
frame156.pack(side=tk.RIGHT)  
frame167 = tk.Frame(master=window, width=50, height=50, bg="blue")  
frame167.pack()  
frame177 = tk.Frame(master=window, width=50, height=50, bg="blue")  
frame177.pack()  
frame1 = tk.Frame(master=window, width=50, height=50, bg="blue")  
frame1.pack()  
## 27.9.2022
Käytiin html anatomiaa  
tehtiin html nettisivua  
## 28.9.2022
-jatkettiin eilistä html sivuston tekemistä/muokkaamista  
#### koodi
</DOCTYPE html>  
<html large="en-US">  
<head>  
	<meta charset="utf-8">  
	<meta name="viewport" content="width=device-width">  
    <title>Peetun sivusto</title>  

</head>  
<body style="background-color:rgb(241, 112, 159)">  
    <style>* {color: rgba(245, 245, 245, 0.769);}</style>  

	<h1>Yleistä sivustosta</h1>  
	öö joo täällä on jotain joo...  

    <h3>Asioita joista tykkään</h3>  
    <ul>  
        <li>Pelaaminen</li>  
    </ul>  

    <h3>Pelit joita pelaan(aina välillä)</h3>  
    <ol>  
        <li>Sea of Thieves</li>  
        <li>OW</li>  
        <li>Roblox</li>  
        <li>CS:GO</li>  
    </ol>  

    <script type="text/javascript">  
        var clicks = 0;  
        function onClick() {  
            clicks += 1;  
            document.getElementById("clicks").innerHTML = clicks;  
        };  
        </script>  
        <button type="button" onClick="onClick()">klikkaa mua</button>  
        <p>Clicks: <a id="clicks">0</a></p>  
    <br>  

    <img src="downloads/humuhumunukunukuapuaa.jpg"alt=humuhumunukunukuapuaa>  
    <br>  
    ^humuhumunukunukuapuaa  
    <br>  
    <br>  
    <br>  
    <a href="https://www.youtube.com/watch?v=xvFZjo5PgG0">Ilmaisia V-Buckseja</a>  

</body>
</html>
## 30.9.2022
Tehtiin html form, jossa oli täytettävänä:  
-nimi  
-ikä  
-päivämäärä  
-tekstiboksi (max 120 merkkiä)  
-formin nollaus nappi  

#### koodi
<!DOCTYPE html>  
<html>  
<head>  
    <title>Tärkeä formi</title>  

</head>  

<body style="background-color:rgb(252, 96, 169)">  
    <style>* {color: rgb(0, 255, 255);}</style>  

<h2>Todella tärkeä formi</h2>  

<form action="/action_page.php">  
    
  <label for="fname">Nimi:</label><br>  
  <input type="text" id="fname" name="fname" value=""><br>  

     Ikä:<br>  
         <input type="number" min="1" max="100"><br>  
	
     Päivämäärä:<br>  
         <input type="date"><br>  

     max 120 merkkiä:<br>  
         <input type="text" maxlength="120" required><br>  

  <input type="reset" value="nollaa">  
  <input type="Submit" value="Lähetä">  

</form>   

</body>  
</html>  

## 4.10.2022
Tein google chartsia  
#### koodi  

<script type="text/javascript" src="https://www.gstatic.com/charts/loader.js"></script>  
<script type="text/javascript">  
  google.charts.load("current", {packages:['corechart']});  
  google.charts.setOnLoadCallback(drawChart);  
  function drawChart() {  
    var data = google.visualization.arrayToDataTable([  
      ["Element", "Density", { role: "style" } ],  
      ["Maanantai", 8, "color: #76A7FA"],  
      ["Tiistai", 8, "color: #76A7FA"],  
      ["Keskiviikko", 10, "color: #76A7FA"],  
      ["Torstai", 13, "color: #76A7FA"],  
      ["Perjantai", 14, "color: #76A7FA"],  
      ["Lauantai", 12, "color: #76A7FA"],  
      ["Sunnuntai", 10, "color: #76A7FA"]  
    ]);  

    var view = new google.visualization.DataView(data);  
    view.setColumns([0, 1,  
    { calc: "stringify",  
    sourceColumn: 1,  
    type: "string",  
    role: "annotation" },  
    2]);  

    var options = {  
   				  title: "Tämän viikon lämpötilat asteina",  
    				  width: 800,  
    				  height: 400,  
    				  bar: {groupWidth: "95%"},  
    				  legend: { position: "none" },  
    };  
    var chart = new google.visualization.ColumnChart(document.getElementById("columnchart_values"));  
    chart.draw(view, options);  
}  
</script>  
<div id="columnchart_values" style="width: 900px; height: 300px;"></div>  

## 5.10.2022
Yritin saada yhdistettyä Azuren tietokantaan (en saanut toimimaan)  
## 11.10.2022
-tein html sivua, jossa käytin css:ää
-Tein githubiin branchejä: main, develop, staging
-Palautin Elsaan arduinon, graafisen ohjeiston, HTML-Perusteet
## 12.10.2022
-tein html sivua, jossa käytin css:ää
-Sain sivun valmiiksi
-Lähetin projektin Elsaan
