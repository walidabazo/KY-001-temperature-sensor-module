# KY-001-temperature-sensor-module
KY-001 temperature sensor module with Oled display 
<h2><strong>KY-001 temperature sensor module OLED DISPLAY</strong></h2>

   [![Watch the video](https://img.youtube.com/vi/QYI763sviUk/0.jpg)](https://youtu.be/QYI763sviUk)
   
<hr />
<p><strong>short description :</strong></p>

<p>KY-001 Temperature Sensor Module allows ambient temperature measurement using the digital serial bus.&nbsp;&nbsp;</p>

<p><img alt="" src="https://blog.edafait.com/sensorimages/001/temperature_sensor_module.jpg" style="height:318px; width:500px" /></p>

<h2>ARDUINO CODE&nbsp;</h2>

<h2><strong>Case 1 :&nbsp;</strong></h2>

<div style="background:#eeeeee; border:1px solid #cccccc; padding:5px 10px"><cite><span dir="ltr">#include &lt;OneWire.h&gt;<br />
#include &lt;DallasTemperature.h&gt;<br />
// Data wire is plugged into pin 2 on the Arduino<br />
#define Temperature_wire 4<br />
// Setup a oneWire instance to communicate with any OneWire devices (not just Maxim/Dallas temperature ICs)<br />
OneWire oneWire(Temperature_wire);<br />
// Pass our oneWire reference to Dallas Temperature.&nbsp;<br />
DallasTemperature sensors(&amp;oneWire);<br />
void setup(void)<br />
{<br />
&nbsp; // start serial port<br />
&nbsp; Serial.begin(9600);<br />
&nbsp; Serial.println(&quot;Dallas Temperature IC Control Library Demo&quot;);<br />
&nbsp; // Start up the library<br />
&nbsp; sensors.begin(); // IC Default 9 bit. If you have troubles consider upping it 12. Ups the delay giving the IC more time to process the temperature measurement<br />
}<br />
void loop(void)<br />
{&nbsp;<br />
&nbsp; // call sensors.requestTemperatures() to issue a global temperature&nbsp;<br />
&nbsp; // request to all devices on the bus<br />
&nbsp; //Serial.print(&quot;Requesting temperatures...&quot;);<br />
&nbsp; sensors.requestTemperatures(); // Send the command to get temperatures<br />
&nbsp; Serial.println(&quot;DONE&quot;);<br />
&nbsp; //Serial.print(&quot;Temperature &nbsp;&quot;);<br />
&nbsp; &nbsp; Serial.print(&quot;Temperature: &quot;);<br />
&nbsp; Serial.println(sensors.getTempCByIndex(0)); // Why &quot;byIndex&quot;? You can have more than one IC on the same bus. 0 refers to the first IC on the wire<br />
&nbsp; delay(10000);<br />
}</span></cite></div>

<h2><strong>Case 2 with OLED DISPLAY</strong></h2>

<p><img alt="" src="https://blog.edafait.com/sensorimages/001/temperature_sensor_module_oled.png" style="height:457px; width:500px" /></p>

<div style="background:#eeeeee; border:1px solid #cccccc; padding:5px 10px">
<p>#include &lt;OneWire.h&gt;<br />
#include &lt;DallasTemperature.h&gt;<br />
#include &lt;SPI.h&gt;<br />
#include &lt;Wire.h&gt;<br />
#include &lt;Adafruit_GFX.h&gt;<br />
#include &lt;Adafruit_SSD1306.h&gt;</p>

<p>Adafruit_SSD1306 display(-1);<br />
// Data wire is plugged into pin 2 on the Arduino<br />
#define Temperature_wire 4<br />
// Setup a oneWire instance to communicate with any OneWire devices (not just Maxim/Dallas temperature ICs)<br />
OneWire oneWire(Temperature_wire);<br />
// Pass our oneWire reference to Dallas Temperature.&nbsp;<br />
DallasTemperature sensors(&amp;oneWire);<br />
void setup(void)<br />
{<br />
&nbsp; // start serial port<br />
&nbsp; Serial.begin(9600);<br />
&nbsp; Serial.println(&quot;Dallas Temperature IC Control Library Demo&quot;);<br />
&nbsp; // Start up the library<br />
&nbsp; sensors.begin(); // IC Default 9 bit. If you have troubles consider upping it 12. Ups the delay giving the IC more time to process the temperature measurement</p>

<p>&nbsp; // initialize with the I2C addr 0x3C<br />
&nbsp; display.begin(SSD1306_SWITCHCAPVCC, 0x3C); &nbsp;</p>

<p>&nbsp; // Clear the buffer.<br />
&nbsp; display.clearDisplay();</p>

<p>&nbsp; // Display Text<br />
&nbsp; display.setTextSize(1);<br />
&nbsp; display.setTextColor(WHITE);<br />
&nbsp; display.setCursor(10,0);<br />
&nbsp; display.println(&quot;Hello world!&quot;);<br />
&nbsp; display.display();<br />
&nbsp; delay(2000);<br />
&nbsp; display.clearDisplay();<br />
}<br />
void loop(void)<br />
{&nbsp;<br />
&nbsp; // call sensors.requestTemperatures() to issue a global temperature&nbsp;<br />
&nbsp; // request to all devices on the bus<br />
&nbsp; //Serial.print(&quot;Requesting temperatures...&quot;);<br />
&nbsp; sensors.requestTemperatures(); // Send the command to get temperatures</p>

<p>&nbsp; //Serial.print(&quot;Temperature &nbsp;&quot;);<br />
&nbsp; &nbsp; Serial.print(&quot;Temperature: &quot;);<br />
&nbsp; Serial.println(sensors.getTempCByIndex(0)); // Why &quot;byIndex&quot;? You can have more than one IC on the same bus. 0 refers to the first IC on the wire</p>

<p>&nbsp; display.setTextSize(1);<br />
&nbsp; display.setTextColor(WHITE);<br />
&nbsp; display.setCursor(10,0);<br />
&nbsp; display.println( String(sensors.getTempCByIndex(0)) +&quot; C&quot;);<br />
&nbsp; display.display();<br />
&nbsp; delay(2000);<br />
&nbsp; display.clearDisplay();<br />
&nbsp; delay(1000);<br />
}</p>
</div>

<p>&nbsp;</p>

<h2>SPECIFICATIONS :&nbsp;</h2>

<table>
	<tbody>
		<tr>
			<td>Operating Voltage</td>
			<td>3.0V to 5.5V</td>
		</tr>
		<tr>
			<td>Temperature Measurement Range</td>
			<td>-55&deg;C to 125&deg;C [-57&deg;F to 257&deg;F]</td>
		</tr>
		<tr>
			<td>Measurement Accuracy Range</td>
			<td>&plusmn;0.5&deg;C</td>
		</tr>
		<tr>
			<td>Board Dimensions</td>
			<td>18.5mm x 15mm [0.728in x 0.591in]</td>
		</tr>
	</tbody>
</table>

<p>&nbsp;</p>

<p>&nbsp;</p>

<p>&nbsp;</p>
