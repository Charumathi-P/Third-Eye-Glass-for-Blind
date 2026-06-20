const int trigPin = 9;
const int echoPin = 10;
const int buzzer = 8;
const int vibrationMotor = 7;

long duration;
int distance;

void setup() {
  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);
  pinMode(buzzer, OUTPUT);
  pinMode(vibrationMotor, OUTPUT);
  Serial.begin(9600);
}

void loop() {

  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);

  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);

  digitalWrite(trigPin, LOW);

  duration = pulseIn(echoPin, HIGH);

  distance = duration * 0.034 / 2;

  Serial.print("Distance: ");
  Serial.print(distance);
  Serial.println(" cm");

  if (distance <= 100) {
    digitalWrite(buzzer, HIGH);
    digitalWrite(vibrationMotor, HIGH);
    delay(200);
  } else {
    digitalWrite(buzzer, LOW);
    digitalWrite(vibrationMotor, LOW);
  }

  delay(100);
}
