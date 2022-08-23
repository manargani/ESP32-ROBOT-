# ESP32-ROBOT-
#include "BluetoothSerial.h"

BluetoothSerial SerialBT;

char receivedChar;

const int ena =2 ;
const int in1 =15 ;
const int in2 = 4;
const int in3 = 0;
const int in4 =12 ;
const int enb =14 ;


void setup() {
  Serial.begin(9600);
  SerialBT.begin("esm el bluetooth elli t7eb tsammih"); 
;
  pinMode(ena, OUTPUT);
  pinMode(enb, OUTPUT);
  pinMode(in1, OUTPUT);
  pinMode(in2, OUTPUT);
  pinMode(in3, OUTPUT);
  pinMode(in4, OUTPUT);
  digitalWrite(ena,LOW);
  digitalWrite(enb,LOW);
  digitalWrite(in1,LOW);
  digitalWrite(in2,LOW);
  digitalWrite(in3,LOW);
  digitalWrite(in4,LOW);
 
}

void AVANT(){
     
  digitalWrite(ena,HIGH);
  digitalWrite(enb,HIGH);
  digitalWrite(in1,HIGH);
  digitalWrite(in2,LOW);
  digitalWrite(in3,HIGH);
  digitalWrite(in4,LOW);
} 
     
void ARRIERE(){
      
  digitalWrite(ena,HIGH);
  digitalWrite(enb,HIGH);
  digitalWrite(in1,LOW);
  digitalWrite(in2,HIGH);
  digitalWrite(in3,LOW);
  digitalWrite(in4,HIGH);
}
void GAUCHE(){
  digitalWrite(ena,HIGH);
  digitalWrite(enb,HIGH);
  digitalWrite(in1,LOW);
  digitalWrite(in2,HIGH);
  digitalWrite(in3,HIGH);
  digitalWrite(in4,LOW);
}
void DROITE(){
      
  digitalWrite(ena,HIGH);
  digitalWrite(enb,HIGH);
  digitalWrite(in1,HIGH);
  digitalWrite(in2,LOW);
  digitalWrite(in3,LOW);
  digitalWrite(in4,HIGH);
}
void STOP(){
     
       digitalWrite(ena,LOW);
  digitalWrite(enb,LOW);
  digitalWrite(in1,LOW);
  digitalWrite(in2,LOW);
  digitalWrite(in3,LOW);
  digitalWrite(in4,LOW);
}


void loop() {
    receivedChar =(char)SerialBT.read();
    if(receivedChar == '1')
    {
      AVANT();
       Serial.print ("forward");
      Serial.print ("\n");
       
    }
    else if(receivedChar == '3')
    {
 
      ARRIERE();
       Serial.print ("backward");
      Serial.print ("\n");
    }        
     else if (receivedChar == '4')
    {

      GAUCHE();
       Serial.print ("left");
      Serial.print ("\n");
    }        
    else if (receivedChar == '2')
    {

      DROITE();
       Serial.print ("right");
      Serial.print ("\n");
    }
 
    
    else     {
      STOP();
       Serial.print ("stop");
      Serial.print ("\n");
    }
  
  delay(20);
}
