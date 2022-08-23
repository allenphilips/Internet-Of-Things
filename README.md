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
# Internet-Of-Things<br>
1.Arduino LED:<br>
https://wokwi.com/projects/333795777062109780

2.Arduino RGB LED:<br>
https://wokwi.com/projects/333799378069226066

https://wokwi.com/projects/333805648701555283

3.LCD:<br>
https://wokwi.com/projects/333806682158137939

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
