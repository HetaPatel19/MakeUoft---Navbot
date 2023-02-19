/*pin config
    d7 - MOsfet left motor
    d6 - Mosfet right motor

    d12 - Ultrasonic sensor input
    d11 - Ultrasonic sensor output

    d10 - Servo
*/

int distancel;
int distancer;
long duration;
int distance;
int defaultDis;
int disturn;
#include<Servo.h>
#include<NewPing.h>
Servo eye;
void setup() {
  Serial.begin(9600);
  eye.attach(10);
  pinMode(7, OUTPUT);
  pinMode(6, OUTPUT);
  pinMode(11, OUTPUT);
  pinMode(12, INPUT);
  eye.write(90);



}

void loop() {
  looks();
  if (distance < 500) {

    Serial.println(distance);
    if (distance < 50) {
      stopp();
      delay(500);
      distancel = lookl();
      delay(500);
      distancer = lookr();
      delay(500);
      if (distancel > distancer) {
        tLeft();
              }
      else {
        tRight(); 
      }
    }
    else{
      str();
    }

  }

}
int lookl() {
  eye.write(160);
  delay(1000);
  ping();
  eye.write(90);
  return distance;

}
int lookr() {
  eye.write(20);
  delay(1000);
  ping();
  eye.write(90);
  return distance;

}
int looks() {
  eye.write(90);
  ping();
  return distance;


}
int ping() {
  digitalWrite(11, LOW);
  delayMicroseconds(2);
  // Sets the 8 HIGH (ACTIVE) for 10 microseconds
  digitalWrite(11, HIGH);
  delayMicroseconds(10);
  digitalWrite(11, LOW);
  // Reads the 9, returns the sound wave travel time in microseconds
  duration = pulseIn(12, HIGH);
  // Calculating the distance
  distance = duration * 0.034 / 2;
  return distance;
}
void tLeft() {
  digitalWrite(7, HIGH);
  digitalWrite(6, LOW);
  delay(500);
  digitalWrite(7, HIGH);
  digitalWrite(6, HIGH);
  
}
void tRight() {
  digitalWrite(6, HIGH);
  digitalWrite(7, LOW);
  delay(500);
  digitalWrite(7, HIGH);
  digitalWrite(6, HIGH);
}
void str() {
  digitalWrite(7, HIGH);
  digitalWrite(6, HIGH);
}
void stopp() {
  digitalWrite(7, LOW);
  digitalWrite(6, LOW);
}
