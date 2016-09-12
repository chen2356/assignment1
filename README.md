# assignment1
assignment1
int ledgreenPin = 12;
int ledbluePin = 7;
int ledredPin = 8;
int buttongreenPin = 6;
int buttonbluePin = 3;
int buttonredPin = 5;
int pot = A1;
int buttongreenState = 0;
int buttonblueState = 0;
int buttonredState = 0;
int sensorValue = 0;

void setup() {
  Serial.begin(9600);
  pinMode(ledgreenPin, OUTPUT);
  pinMode(ledbluePin, OUTPUT);
  pinMode(ledredPin, OUTPUT);
  pinMode(buttongreenPin, INPUT);
  pinMode(buttonbluePin, INPUT);
  pinMode(buttonredPin, INPUT);
}

void loop() {
  sensorValue = analogRead(pot);
 int  brightness = map(sensorValue, 0, 1024, 0, 255);
  buttongreenState = digitalRead(buttongreenPin);
  buttonblueState = digitalRead(buttonbluePin);
  buttonredState = digitalRead(buttonredPin);
  Serial.print("green button state: ");
  Serial.print(buttongreenState);
  Serial.print("blue button state: ");
  Serial.print(buttonblueState);
  Serial.print("red button state: ");
  Serial.print(buttonredState);
  Serial.print(", Sensor value: ");
  Serial.print(sensorValue);
  Serial.print(", brightnes: ");
  Serial.println(brightness);
  if (buttongreenState == HIGH) {
    analogWrite(ledgreenPin, brightness);
  } else {
  if (buttonblueState == HIGH) {
    analogWrite(ledbluePin, brightness);
  } else {
  if (buttonredState == HIGH) {
    analogWrite(ledredPin, brightness);
  } else {
    analogWrite(ledgreenPin, 0);
    analogWrite(ledbluePin, 0);
    analogWrite(ledredPin, 0);
   }}}
}
