const int speedA = 90;
const int speedB = 90;
const int enA = 5;
const int enB = 6;
const int In1 = A2;
const int In2 = A3;
const int In3 = A4;
const int In4 = A5;
const int driverTime = 400;
const int offTime = 150;
const int trig = 3; 
const int echo = 2;

void setup() {
Serial.begin(9600);
pinMode(enA,OUTPUT);
pinMode(enB,OUTPUT);
pinMode(In1,OUTPUT);
pinMode(In2,OUTPUT);
pinMode(In3,OUTPUT);
pinMode(In4,OUTPUT);
pinMode(trig,OUTPUT);
pinMode(echo,INPUT);
}
void off()
{
analogWrite(enA,0);
analogWrite(enB,0);
digitalWrite(In1,LOW);
digitalWrite(In2,LOW);
digitalWrite(In3,LOW); 
digitalWrite(In4,LOW); 
}
void straight()
{
analogWrite(enA,speedA);
analogWrite(enB,speedB);
digitalWrite(In1,LOW);
digitalWrite(In2,HIGH);
digitalWrite(In3,LOW); 
digitalWrite(In4,HIGH);   
delay(driverTime);
off();
}
void backward()
{
  analogWrite(enA,speedA);
analogWrite(enB,speedB);
digitalWrite(In1,HIGH);
digitalWrite(In2,LOW);
digitalWrite(In3,HIGH); 
digitalWrite(In4,LOW);   
delay(driverTime);
off();
}
void left()
{
   analogWrite(enA,speedA);
analogWrite(enB,speedB);
digitalWrite(In1,LOW);
digitalWrite(In2,HIGH);
digitalWrite(In3,HIGH); 
digitalWrite(In4,LOW);   
delay(driverTime);
off();
}
void right()
{
analogWrite(enA,speedA);
analogWrite(enB,speedB);
digitalWrite(In1,HIGH);
digitalWrite(In2,LOW);
digitalWrite(In3,LOW); 
digitalWrite(In4,HIGH);   
delay(driverTime);
off();
}
void Ultrasonic()
{
   long duration, cm;      
  digitalWrite(trig, LOW);
  delayMicroseconds(2);
  digitalWrite(trig, HIGH);
  delayMicroseconds(5);
  digitalWrite(trig, LOW);
  
  duration = pulseIn(echo, HIGH);
  cm = microsecondsToCentimetres(duration);
   Serial.print(cm);
  Serial.print("cm");
  Serial.println();  
  delay(100);
}

long microsecondsToCentimetres(long microseconds)
{
  return microseconds / 29 / 2;
}
void loop() {
straight();
straight();

}
