# gesture-vocalizer
arduino code for gesture vocalizer using flex sensor
#include <Wire.h> 
#include <LiquidCrystal_I2C.h>

LiquidCrystal_I2C lcd(0x27,16,4);  // set the LCD address to 0x27 for a 16 chars and 2 line display

int flexPin1 = A0;   //analog pins for sensors
int flexPin2 = A1;
int flexPin3 = A2;
int flexPin4 = A3; 

void setup(){


lcd.init();
  lcd.backlight();
  lcd.setCursor(1,0);
  Serial.begin(9600);
} 
 
void loop() 
{ 
  int flexValue1 = analogRead(flexPin1);  //read values from sensors
  int flexValue2 = analogRead(flexPin2);
  int flexValue3 = analogRead(flexPin3);
  int flexValue4 = analogRead(flexPin4);

 Serial.print("flex sensor 1: ") ;  //display in serial monitor
  Serial.print(flexValue1);
  Serial.print(" flex sensor 2: ");
  Serial.print(flexValue2);
  Serial.print(" flex sensor 3: ");
  Serial.print(flexValue3);
  Serial.print(" flex sensor 4: ");
  Serial.println(flexValue4);
  delay(2000);
  


 if (flexValue1 >=1010 & flexValue1<=1030 & flexValue2 >= 270 & flexValue2 <= 290 & flexValue3 >= 140 & flexValue3 <= 170 & flexValue4 >= 245 & flexValue4 <= 270 )
 {Serial.print("ready"); 
  lcd.setCursor(2,0);
  lcd.print("ready!");
  lcd.setCursor(2,1);
  lcd.print("MUTEATION");    
 }


 
 else if  (flexValue1 <=1000)
 {lcd.setCursor(2,0);
  lcd.print("how are you?");
  lcd.setCursor(2,1);
  lcd.print("i am fine thank you .");  
 delay (2000);
   
  lcd.clear();
 }
else if   (flexValue2 <=240)
 {lcd.setCursor(2,0);
  lcd.print("lets eat food ");
  lcd.setCursor(2,1);
  lcd.print("I am hungry!");  
 delay (2000);

  lcd.clear();
}

 else if  (flexValue3<=130)
 {lcd.setCursor(2,0);
  lcd.print("I LOVE YOU");
 delay (2000);
   
  lcd.clear();
 }

  else if  (flexValue4 <=235)
 {lcd.setCursor(2,0);
  lcd.print("I have to use the ");
  lcd.setCursor(2,1);
  lcd.print("washroom!");  ;
 delay (2000);
   
  lcd.clear();
 }
 
}
