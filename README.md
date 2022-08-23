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


https://wokwi.com/projects/336966830711112275 - LED
https://wokwi.com/projects/336967978479256147 - 3 LED

//HARDWARE

   ULTRASONIC_SENSOR

   const int trigPin = 13; //D7
   const int echoPin = 12; //D6

   long duration;
   float distanceCm;
   float distanceInch;

   void setup() {
           Serial.begin(9600); // Starting Serial Terminal
   }

   void loop() {
      long duration, inches, cm;
      pinMode(trigPin, OUTPUT);
      digitalWrite(trigPin, LOW);
      delayMicroseconds(2);
      digitalWrite(trigPin, HIGH);
      delayMicroseconds(10);
      digitalWrite(trigPin, LOW);
      pinMode(echoPin, INPUT);
      duration = pulseIn(echoPin, HIGH);
      inches = microsecondsToInches(duration);
      cm = microsecondsToCentimeters(duration);
      Serial.print(inches);
      Serial.print("in, ");
      Serial.print(cm);
      Serial.print("cm");
      Serial.println();
      delay(1000);
   }

   long microsecondsToInches(long microseconds) {
       return microseconds / 74 / 2;
   }

  long microsecondsToCentimeters(long microseconds) {
    return microseconds / 29 / 2;
   }



DHT11

    #include <Adafruit_Sensor.h>
    #include <DHT.h>;
    #define DHTPIN 13     // what pin we're connected to
    #define DHTTYPE DHT11   // DHT 22  (AM2302)
    DHT dht(DHTPIN, DHTTYPE); //// Initialize DHT sensor for normal 16mhz Arduino
    //Variables
    int chk;
    float hum;  //Stores humidity value
    float temp; //Stores temperature value
    void setup()
    {
      Serial.begin(9600);
      dht.begin();
    }
    void loop()
   {
       delay(2000);
       //Read data and store it to variables hum and temp
       hum = dht.readHumidity();
       temp= dht.readTemperature();
       //Print temp and humidity values to serial monitor
       Serial.print("Humidity: ");
       Serial.print(hum);
       Serial.print(" %, Temp: ");
       Serial.print(temp);
       Serial.println(" Celsius");
       delay(1000); //Delay 2 sec.
   }
 
 
 RGB
 
 int red = D1;
 int green = D6;
 int blue = D7;
 //GROUND IS CONNECTED TO 3V 
 void setup() {
   pinMode(red, OUTPUT);
   pinMode(green, OUTPUT);
   pinMode(blue, OUTPUT);

 }

 void loop() {
   displayColor(0b100); //RED
   delay(1000);
   displayColor(0b010); //GREEN
   delay(1000);
   displayColor(0b001); //BLUE
   delay(1000);
   displayColor(0b101); //MAGENTA
   delay(1000);
   displayColor(0b011); //CYAN
   delay(1000);
   displayColor(0b110); //YELLOW
   delay(1000);
   displayColor(0b111); //WHITE
   delay(1000);
 }

 void displayColor(byte color) {
   digitalWrite(red, !bitRead(color, 2));
   digitalWrite(green, !bitRead(color, 1));
   digitalWrite(blue, !bitRead(color, 0));
 }


IR_LED
  int ir=D7;
 int led=D5;
 void setup() {
   // put your setup code here, to run once:
   pinMode(ir,INPUT);
     pinMode(led,OUTPUT);
     Serial.begin(9600);

 }

 void loop() {
   // put your main code here, to run repeatedly:
   int irvalue=digitalRead(ir);
   if(irvalue==LOW)
   {
     Serial.println("LOW");
     digitalWrite(led,HIGH);
   }
   else
   {
     Serial.println("HIGH");
     digitalWrite(led,LOW);
   }
 delay(100);
 }
</br>
</br>
</br>
     LDR
     const int ldrPin=A0;
     void setup() {
       Serial.begin(9600);
       pinMode(ldrPin,INPUT);
     }
     void loop() {
       int rawData = analogRead(ldrPin);   
       Serial.println(rawData);
       delay(1000);
     }
</br>
</br>
</br>

 LDR_LED

 int ldr=A0;//Set A0(Analog Input) for LDR.
 int value=0;
 int led=D1;
 void setup() {
 Serial.begin(9600);
 pinMode(led,OUTPUT);
 }

 void loop() {
 value=analogRead(ldr);//Reads the Value of LDR(light).
 Serial.println("LDR value is :");//Prints the value of LDR to Serial Monitor.
 Serial.println(value);
 if(value<50)
   {
     digitalWrite(led,HIGH);//Makes the LED glow in Dark.
   }
   else
   {
     digitalWrite(led,LOW);//Turns the LED OFF in Light.
   }
   delay(1000);
 }\
 </br>
 </br>
 LED_CHASER
 
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
