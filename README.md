# Internet-Of-Things



**word document**<br>
C:\Users\cs\Documents\INTERNET OF THINGS.docx<br>

1.https://wokwi.com/projects/333797089965245011<br>
 2.https://wokwi.com/projects/333806073021465171<br>

**Temparature and humidity sensor**<br>
https://wokwi.com/projects/334344386331542099<br>

**IR sensor**<br>
https://wokwi.com/projects/334347782067323474<br>

**PIR sensor**<br>
https://wokwi.com/projects/334347041012449875<br>


**Ultra sonic sensor**<br>
https://wokwi.com/projects/334346755679191635<br>

**LED fade**<br>
https://wokwi.com/projects/334432117252424275<br>

**LED button**<br>
https://wokwi.com/projects/334433004924437074<br>

**Motion sensor**<br>
https://wokwi.com/projects/334433247916196435<br>

**Motion sensor with LED**<br>
https://wokwi.com/projects/334433528781472340<br>

**Motion senser with buzzer**<br>
https://wokwi.com/projects/334433841383998034<br>

**Ultrasonic buzzer**<br>
https://wokwi.com/projects/334434213071684180<br>


**Ultra sonic LED**<br>
https://wokwi.com/projects/334434780177236562<br>

**Servomotor**<br>
https://wokwi.com/projects/334976347856175699<br>

**Servo motor contrlled by potentiometer**<br>
https://wokwi.com/projects/334976852055556691<br>

**Button servo motor**<br>
https://wokwi.com/projects/334977481574449747<br>

**servo meter using ultrasonic**<br>
https://wokwi.com/projects/334979604864303699<br>

**buzzer beep**<br>
https://wokwi.com/projects/335066186469343826<br>

**Buzzer beep using pushbutton**<br>
https://wokwi.com/projects/335068830961238612<br>

**Ultra sonic buzzer beep**<br>
https://wokwi.com/projects/334434213071684180<br>

**Ultrasonic buzzer with LED**<br>
https://wokwi.com/projects/335610630487671378<br>


https://wokwi.com/projects/336966830711112275 - LED<br>
https://wokwi.com/projects/336967978479256147 - 3 LED<br>

//HARDWARE<br>

   ULTRASONIC_SENSOR<br>

   const int trigPin = 13; //D7<br>
   const int echoPin = 12; //D6<br>

   long duration;<br>
   float distanceCm;<br>
   float distanceInch;<br>

   void setup()<br> {<br>
           Serial.begin(9600); // Starting Serial Terminal<br>
   }<br>

   void loop()<br> {<br>
      long duration, inches, cm;<br>
      pinMode(trigPin, OUTPUT);<br>
      digitalWrite(trigPin, LOW);<br>
      delayMicroseconds(2);<br>
      digitalWrite(trigPin, HIGH);<br>
      delayMicroseconds(10);<br>
      digitalWrite(trigPin, LOW);<br>
      pinMode(echoPin, INPUT);<br>
      duration = pulseIn(echoPin, HIGH);<br>
      inches = microsecondsToInches(duration);<br>
      cm = microsecondsToCentimeters(duration);<br>
      Serial.print(inches);<br>
      Serial.print("in, ");<br>
      Serial.print(cm);<br>
      Serial.print("cm");<br>
      Serial.println();<br>
      delay(1000);<br>
   }<br>

   long microsecondsToInches(long microseconds)<br> {<br>
       return microseconds / 74 / 2;<br>
   }<br>

  long microsecondsToCentimeters(long microseconds)<br> {<br>
    return microseconds / 29 / 2;<br>
   }<br>



DHT11<br>

    #include <Adafruit_Sensor.h><br>
    #include <DHT.h>;<br>
    #define DHTPIN 13 <br>    // what pin we're connected to
    #define DHTTYPE DHT11 <br>  // DHT 22  (AM2302)
    DHT dht(DHTPIN, DHTTYPE);<br> //// Initialize DHT sensor for normal 16mhz Arduino
    //Variables
    int chk;<br>
    float hum; <br> //Stores humidity value
    float temp;<br> //Stores temperature value
    void setup()<br>
    {<br>
      Serial.begin(9600);<br>
      dht.begin();<br>
    }<br>
    void loop()<br>
   {<br>
       delay(2000);<br>
       //Read data and store it to variables hum and temp<br>
       hum = dht.readHumidity();<br>
       temp= dht.readTemperature();
       //Print temp and humidity values to serial monitor
       Serial.print("Humidity: ");<br>
       Serial.print(hum);<br>
       Serial.print(" %, Temp: ");<br>
       Serial.print(temp);<br>
       Serial.println(" Celsius");<br>
       delay(1000);<br> //Delay 2 sec.
   }<br>
 
 
 RGB<br>
 
 int red = D1;<br>
 int green = D6;<br>
 int blue = D7;<br>
 //GROUND IS CON<br>NECTED TO 3V 
 void setup()<br> {
   pinMode(red, OUTPUT);<br>
   pinMode(green, OUTPUT);<br>
   pinMode(blue, OUTPUT);<br>

 }<br>

 void loop() {<br>
   displayColor(0b100);<br> //RED
   delay(1000);<br>
   displayColor(0b010); <br>//GREEN
   delay(1000);<br>
   displayColor(0b001); <br>//BLUE
   delay(1000);<br>
   displayColor(0b101); <br>//MAGENTA
   delay(1000);<br>
   displayColor(0b011); <br>//CYAN
   delay(1000);<br>
   displayColor(0b110); <br>//YELLOW
   delay(1000);<br>
   displayColor(0b111);<br> //WHITE
   delay(1000);<br>
 }<br>

 void displayColor(byte color)<br> {<br>
   digitalWrite(red, !bitRead(color, 2));<br>
   digitalWrite(green, !bitRead(color, 1));<br>
   digitalWrite(blue, !bitRead(color, 0));<br>
 }<br>


IR_LED<br>
  int ir=D7;<br>
 int led=D5;<br>
 void setup()<br> {<br>
   // put your setup code here, to run once:<br>
   pinMode(ir,INPUT);<br>
     pinMode(led,OUTPUT);<br>
     Serial.begin(9600);<br>

 }<br>

 void loop()<br> {<br>
   // put your main code here, to run repeatedly:<br>
   int irvalue=digitalRead(ir);<br>
   if(irvalue==LOW)<br>
   {<br>
     Serial.println("LOW");<br>
     digitalWrite(led,HIGH);<br>
   }<br>
   else<br>
   {<br>
     Serial.println("HIGH");<br>
     digitalWrite(led,LOW);<br>
   }<br>
 delay(100);<br>
 }<br>
</br>
</br>
</br>
     LDR<br>
     const int ldrPin=A0;<br>
     void setup() {<br>
       Serial.begin(9600);<br>
       pinMode(ldrPin,INPUT);<br>
     }<br>
     void loop()<br> {<br>
       int rawData = analogRead(ldrPin);  <br> 
       Serial.println(rawData);<br>
       delay(1000);<br>
     }<br>
</br><br>
</br><br>
</br><br>

 LDR_LED<br>

 int ldr=A0;//Set A0(Analog Input) for LDR.<br>
 int value=0;<br>
 int led=D1;<br>
 void setup()<br> {<br>
 Serial.begin(9600);<br>
 pinMode(led,OUTPUT);<br>
 }<br>

 void loop()<br> {<br>
 value=analogRead(ldr);//Reads the Value of LDR(light).<br>
 Serial.println("LDR value is :");//Prints the value of LDR to Serial Monitor.<br>
 Serial.println(value);<br>
 if(value<50)<br>
   {<br>
     digitalWrite(led,HIGH);//Makes the LED glow in Dark.<br>
   }<br>
   else<br>
   {<br>
     digitalWrite(led,LOW);//Turns the LED OFF in Light.<br>
   }<br>
   delay(1000);<br>
 }\<br>
 </br><br>
 </br><br>
 LED_CHASER<br>
 
int pinsCount=6;                        // declaring the integer variable pinsCount
int pins[] = {D0,D1,D7,D5,D3,D2};          // declaring the array pins[]

void setup() {                
  for (int i=0; i<pinsCount; i=i+1){    // counting the variable i from 0 to 9
    pinMode(pins[i], OUTPUT);            // initialising the pin at index i of the array of pins as OUTPUT
  }
}

void loop() {
  for (int i=0; i<pinsCount; i=i+1){    // chasing right
    digitalWrite(pins[i], HIGH);         // switching the LED at index i on
    delay(100);                          // stopping the program for 100 milliseconds
    digitalWrite(pins[i], LOW);          // switching the LED at index i off
  }
  for (int i=pinsCount-1; i>0; i=i-1){   // chasing left (except the outer leds)
   digitalWrite(pins[i], HIGH);         // switching the LED at index i on
    delay(100);                          // stopping the program for 100 milliseconds
    digitalWrite(pins[i], LOW);          // switching the LED at index i off

  }
}


Liquid crystal-https: //wokwi.com/projects/322062421191557714<br>
LED chaser- https://wokwi.com/projects/340779157917008467<br>


Sound sensor
int led = 6;
int sound_digital = 7;
int sound_analog = A0;

void setup(){
  Serial.begin(9600);
  pinMode(led, OUTPUT);
  pinMode(sound_digital, INPUT);  
}

void loop(){
  int val_digital = digitalRead(sound_digital);
  int val_analog = analogRead(sound_analog);

  Serial.print(val_analog);
  Serial.print("\t");
  Serial.println(val_digital);

  if (val_digital == HIGH)
  {
    digitalWrite (led, HIGH);
    delay(3000);
    }
  else
  {
    digitalWrite (led, LOW);
    }
}


* Seven segment digit**
https://wokwi.com/projects/342585727360434772
