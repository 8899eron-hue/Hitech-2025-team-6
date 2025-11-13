#include <Servo.h>
 Servo servoCW;    
// Servo searah jarum jam
 Servo servoCCW;   // Servo berlawanan arah 
jarum jam
 int servoAngleCW;  
int servoAngleCCW;
 void setup() {
 servoCW.attach(9);    
// Servo CW di pin 9
 servoCCW.attach(10);  // Servo CCW di pin 
10
 // Posisi awal di tengah (90 derajat)
 servoCW.write(90);
 servoCCW.write(90);
 delay(1000); // Tunggu 1 detik di posisi 
netral
 }
 void loop() {
 // ====== GERAK KE MAKSIMUM ======
 for (int logicAngle = 0; logicAngle <= 88; 
logicAngle++) {
 // Servo CW: 0=90°, +88=178°
 servoAngleCW = map(logicAngle, -88, 88, 
2, 178);
    // Servo CCW: arah berlawanan
    servoAngleCCW = map(logicAngle, -88, 88, 
178, 2);
    servoCW.write(servoAngleCW);
    servoCCW.write(servoAngleCCW);
    delay(15); // kecepatan gerak
  }
  delay(5000); // tunggu 5 detik di posisi 
maksimum
  // ====== KEMBALI KE TENGAH ======
  for (int logicAngle = 88; logicAngle >= 0; 
logicAngle--) {
    servoAngleCW = map(logicAngle, -88, 88, 
2, 178);
    servoAngleCCW = map(logicAngle, -88, 88, 
178, 2);
    servoCW.write(servoAngleCW);
    servoCCW.write(servoAngleCCW);
    delay(15);}
  }
  delay(5000); // tunggu 5 detik di tengah
