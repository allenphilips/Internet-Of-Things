ESP32<br>
https://wokwi.com/projects/336966830711112275 - LED<br>
https://wokwi.com/projects/336967978479256147 - 3 LED<br>
https://wokwi.com/projects/340880463446934098 - RGB<br>
https://wokwi.com/projects/340882358612787796 - LCD<br>
https://wokwi.com/projects/340886369600537172 - Servo Motor + Pushbutton<br>
https://wokwi.com/projects/340888468071645780 - Servo Motor + Sliding Potentiometer<br>
https://wokwi.com/projects/340890155914101331 - Buzzer + Pushbutton_<br>
https://wokwi.com/projects/340890489300451922 - Buzzer + UltraSonic Sensor<br>
https://wokwi.com/projects/340890896679567955 - Potentiometer + LED<br>
https://wokwi.com/projects/340892440485429842 - DHT22<br>
https://wokwi.com/projects/340893919446303316 - LED CHASER<br>
https://wokwi.com/projects/340936317213868626 - LDR<br>
https://wokwi.com/projects/340936847717827156 - LDR + LED<br>
<br>

# LAB LIST
1)program1: LED WITH BUZZER
https://wokwi.com/projects/337602112497123922

2)program2: LED with PUSH BUTTON:
https://wokwi.com/projects/334431214876230226

3)Program3:DHT 22 sensor:
https://wokwi.com/projects/337603663792964179

4)Program 4: relay with arduino ie Servo motor with BUTTON:
https://wokwi.com/projects/337603967810798163

5)Program 5: LCD DHT 22
https://wokwi.com/projects/337605922532622930

6)Flood Monitoring System:<br>
#include "ThingSpeak.h"<br>
#include <ESP8266WiFi.h><br>
const int trigPin1 = D1;<br>
const int echoPin1 = D2;<br>
#define redled D3<br>
#define grnled D4<br>
//#define BUZZER D5 //buzzer pin<br>
unsigned long ch_no = 1838852;//Replace with Thingspeak Channel number<br>
const char * write_api = "B09P3G8RR3PGTIT6";//Replace with Thingspeak write API<br>
char auth[] = "mwa0000027193634";<br>
char ssid[] = "m";<br>
char pass[] = "Csdept@1234";<br>
unsigned long startMillis;<br>
unsigned long currentMillis;<br>
const unsigned long period = 10000;<br>
WiFiClient  client;<br>
long duration1;<br>
int distance1;<br>
void setup()<br>
{<br>
  pinMode(trigPin1, OUTPUT);<br>
  pinMode(echoPin1, INPUT);<br>
  pinMode(redled, OUTPUT);<br>
  pinMode(grnled, OUTPUT);<br>
  digitalWrite(redled, LOW);<br>
  digitalWrite(grnled, LOW);<br>
  Serial.begin(115200);<br>
  WiFi.begin(ssid, pass);<br>
  while (WiFi.status() != WL_CONNECTED)<br>
  {<br>
    delay(500);<br>
    Serial.print(".");<br>
  }<br>
  Serial.println("WiFi connected");<br>
  Serial.println(WiFi.localIP());<br>
  ThingSpeak.begin(client);<br>
  startMillis = millis();  //initial start time<br>
}<br>
void loop()<br>
{<br>
  digitalWrite(trigPin1, LOW);<br>
  delayMicroseconds(2);<br>
  digitalWrite(trigPin1, HIGH);<br>
  delayMicroseconds(10);<br>
  digitalWrite(trigPin1, LOW);<br>
  duration1 = pulseIn(echoPin1, HIGH);<br>
  distance1 = duration1 * 0.034 / 2;<br>
  Serial.println(distance1);<br>
  delay(1500);<br>
  if (distance1 <= 10)<br>
  {<br>
    digitalWrite(D3, HIGH);<br>
    //tone(BUZZER, 300);<br>
    digitalWrite(D4, LOW);<br>
    delay(1500);<br>
    //noTone(BUZZER);<br>
  }<br>
  else<br>
  {<br>
    digitalWrite(D4, HIGH);<br>
    digitalWrite(D3, LOW);<br>
  }<br>
  currentMillis = millis();<br>
  if (currentMillis - startMillis >= period)<br>
  {<br>
    ThingSpeak.setField(1, distance1);<br>
    ThingSpeak.writeFields(ch_no, write_api);<br>
    startMillis = currentMillis;<br>
  }<br>
}<br><br>

7)LED Chaser:<br>
int pinsCount=6;                        // declaring the integer variable pinsCount<br>
int pins[] = {D0,D1,D7,D5,D3,D2};          // declaring the array pins[]<br>
 <br>
void setup() {         <br>       
  for (int i=0; i<pinsCount; i=i+1){    // counting the variable i from 0 to 9<br>
    pinMode(pins[i], OUTPUT);            // initialising the pin at index i of the array of pins as OUTPUT<br>
  }<br>
}<br>
 
void loop() {<br>
  for (int i=0; i<pinsCount; i=i+1){    // chasing right<br>
    digitalWrite(pins[i], HIGH);         // switching the LED at index i on<br>
    delay(100);                          // stopping the program for 100 milliseconds<br>
    digitalWrite(pins[i], LOW);          // switching the LED at index i off<br>
  }<br>
  for (int i=pinsCount-1; i>0; i=i-1){   // chasing left (except the outer leds)<br>
   digitalWrite(pins[i], HIGH);         // switching the LED at index i on<br>
    delay(100);                          // stopping the program for 100 milliseconds<br>
    digitalWrite(pins[i], LOW);          // switching the LED at index i off<br>
  
  }<br>
}<br><br>

8)Soil Moisture Sensor:<br>
const int sensor_pin = A0;  /* Connect Soil moisture analog sensor pin to A0 of NodeMCU */<br>
void setup() {<br>
  Serial.begin(9600); /* Define baud rate for serial communication */<br>
}<br>
void loop() {<br>
float moisture_percentage;<br>
moisture_percentage = ( 100.00 - ( (analogRead(sensor_pin)/1023.00) * 100.00 ) );<br>
Serial.print("Soil Moisture(in Percentage) = ");<br>
Serial.print(moisture_percentage);<br>
Serial.println("%");<br>
delay(1000);<br>
}<br><br>

# Internet-Of-Things<br>
1.Arduino LED:<br>
https://wokwi.com/projects/333795777062109780

2.Arduino RGB LED:<br>
https://wokwi.com/projects/333799378069226066

https://wokwi.com/projects/333805648701555283

3.LCD:<br>
https://wokwi.com/projects/333806682158137939
ESP32:<br>
https://wokwi.com/projects/341022750895243858<br>

4.Ultrasonic sensor:<br>
https://wokwi.com/projects/334346755679191635

5.Temperature and Humidity:<br>
https://wokwi.com/projects/334346231606149714

6.IR:<br>
https://wokwi.com/projects/334347782067323474

7.PIR:<br>
https://wokwi.com/projects/334347041012449875

8.LED Fade:<br>
https://wokwi.com/projects/334436349103833683

9.Motion Sensor:<br>
https://wokwi.com/projects/334431854492910163

10.Motion Sensor Buzzer:<br>
https://wokwi.com/projects/334433831716127314

11.Ultrasonic Sensor LED:<br>
https://wokwi.com/projects/334434440478458452

12.Button LED:<br>
https://wokwi.com/projects/334431013706924626

13.Servo motor:<br>
https://wokwi.com/projects/335615739430961747

14.Servo motor controlled by potentiometer:<br>
https://wokwi.com/projects/334978058200023635

15.Servo motor controlled by push button:<br>
https://wokwi.com/projects/334980736128909908

16.Buzzer:<br>
https://wokwi.com/projects/335066289535976018

17.Buzzer with push button:<br>
https://wokwi.com/projects/335070852899930708

18.Buzzer with ultrasonic sensor:<br>
https://wokwi.com/projects/335072341158527571

19.Buzzer with ultrasonic sensor and LED:<br>
https://wokwi.com/projects/335614105184371284
