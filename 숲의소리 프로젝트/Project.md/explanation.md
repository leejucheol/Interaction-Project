## 숲의 소리

이 작품은 숲의 소리를 구현한 작품입니다.
나뭇잎을 만지면 각각 다른 소리가 납니다. 이를 통해 숲을 구성하는 나뭇잎의 소리를 들려드리고자 생각한 작품입니다.

## 조도센서로 소리가 나오게 하는 코드

const int buzzerPin1 = 7;
const int buzzerPin2 = 6;
const int buzzerPin3 = 5;

int melody1[] = {392, 330, 330, 349, 294, 294, 262, 294, 330, 350, 392, 392, 392, 392, 330, 330, 330, 349, 294, 294, 262, 330, 392, 392, 330, 330, 330};
int melody3[] = {523, 523, 523, 523, 523, 659, 784, 784, 659, 523, 784, 784, 659, 784, 784, 659, 523, 523, 523, 784, 784, 659, 523, 784, 784, 784, 784, 784, 659, 523, 784, 784, 784, 784, 784, 659, 523, 784, 784, 784, 880, 784, 1047, 784, 1047, 784, 659, 587, 523};

int beat1[] = {1, 1, 2, 1, 1, 2, 1, 1, 1, 1, 1, 1, 2, 1, 1, 1, 1, 1, 1, 2, 1, 1, 1, 1, 1, 1, 2};
int beat3[] = {2, 1, 1, 2, 2, 2, 1, 1, 2, 2, 1, 1, 2, 1, 1, 2, 2, 2, 4, 2, 2, 2, 2, 2, 2, 4, 2, 2, 2, 2, 2, 2, 4, 2, 2, 2, 2, 1, 1, 1, 1, 2};

int melodyNum1 = 27;
int melodyNum3 = 42;

void setup() {
Serial.begin(9600);
pinMode(buzzerPin1, OUTPUT);
pinMode(buzzerPin2, OUTPUT);
pinMode(buzzerPin3, OUTPUT);
}

void loop() {
// 조도 센서를 통해서 나비야 음악이 나온다.
int sensorValue1 = analogRead(A0);
int sensorValue2 = analogRead(A1);
int sensorValue3 = analogRead(A2);

Serial.print("센서 1 밝기: ");
Serial.println(sensorValue1);
Serial.print("센서 2 밝기: ");
Serial.println(sensorValue2);
Serial.print("센서 3 밝기: ");
Serial.println(sensorValue3);

if(sensorValue1 > 1004){
for(int i =0; i<melodyNum1; i++){
tone(buzzerPin1, melody1[i]);
delay(250*beat1[i]);
delayMicroseconds(10);
noTone(buzzerPin1);
}
} else if(sensorValue2 >= 1000){
digitalWrite(buzzerPin2, HIGH);  
 delay(1000);
digitalWrite(buzzerPin2, LOW);
} else if(sensorValue3 >= 1010){
for(int i =0; i<melodyNum3; i++){
tone(buzzerPin3, melody3[i]);
delay(200*beat3[i]);
delayMicroseconds(10);
noTone(buzzerPin3);
}
}
delay(600);
}

## 초음파 센서를 통해 숲을 밝혀주는 LED 코드

int echoPin = A0;
int trigPin = A1;

//별
int ledPin1 = 5;
int ledPin2 = 6;
int ledPin3 = 7;
int ledPin4 = 2;
int ledPin5 = 3;
int ledPin6 = 4;
//달
int ledPinm1 = 8;
int ledPinm2 = 9;
int ledPinm3 = 10;
int ledPinm4 = 11;
int ledPinm5 = 12;
int ledPinm6 = 13;

void setup() {
Serial.begin(9600);

pinMode(trigPin, OUTPUT);
pinMode(echoPin, INPUT);

pinMode(ledPin1, OUTPUT);
pinMode(ledPin2, OUTPUT);
pinMode(ledPin3, OUTPUT);
pinMode(ledPin4, OUTPUT);
pinMode(ledPin5, OUTPUT);
pinMode(ledPin6, OUTPUT);
}

void loop() {
// 초음파 센서로 led 켜기
digitalWrite(trigPin,LOW);
delayMicroseconds(2);
digitalWrite(trigPin, HIGH);
delayMicroseconds(10);
digitalWrite(trigPin, LOW);

unsigned long time = pulseIn(echoPin, HIGH);
float distance = ((float)(34000\*time)/1000000)/2;

Serial.print(distance);
Serial.println("cm");

if(distance <= 70.0){
digitalWrite(ledPinm1,HIGH);
digitalWrite(ledPinm2,HIGH);
digitalWrite(ledPinm3,HIGH);
digitalWrite(ledPinm4,HIGH);
digitalWrite(ledPinm5,HIGH);
digitalWrite(ledPinm6,HIGH);

    for(int i=0; i<255; i++){
    analogWrite(ledPin1,i);
    delay(5);
    }
    for(int i=255; i>0; i--){
    analogWrite(ledPin1,i);
    delay(5);
    }
    for(int i=0; i<255; i++){
    analogWrite(ledPin2,i);
    delay(5);
    }
    for(int i=255; i>0; i--){
    analogWrite(ledPin2,i);
    delay(5);
    }
    for(int i=0; i<255; i++){
    analogWrite(ledPin3,i);
    delay(5);
    }
    for(int i=255; i>0; i--){
    analogWrite(ledPin3,i);
    delay(5);
    }
        for(int i=0; i<255; i++){
    analogWrite(ledPin4,i);
    delay(5);
    }
    for(int i=255; i>0; i--){
    analogWrite(ledPin4,i);
    delay(5);
    }
    for(int i=0; i<255; i++){
    analogWrite(ledPin5,i);
    delay(5);
    }
    for(int i=255; i>0; i--){
    analogWrite(ledPin5,i);
    delay(5);
    }
    for(int i=0; i<255; i++){
    analogWrite(ledPin6,i);
    delay(5);
    }
    for(int i=255; i>0; i--){
    analogWrite(ledPin6,i);
    delay(5);
    }

}
else{
analogWrite(ledPin1,LOW);
analogWrite(ledPin2,LOW);
analogWrite(ledPin3,LOW);
analogWrite(ledPin4,LOW);
analogWrite(ledPin5,LOW);
analogWrite(ledPin6,LOW);

    // digitalWrite(ledPinm1,LOW);
    // digitalWrite(ledPinm2,LOW);
    // digitalWrite(ledPinm3,LOW);
    // digitalWrite(ledPinm4,LOW);
    // digitalWrite(ledPinm5,LOW);

}
delay(300);
}
