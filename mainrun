// Inputs = Ultra Sonic Sensor (motion), Controller/Joystick, Motors
// Outputs = Wheels, Fans, Ultra Sonic Sensor (motion)

#include <DIYables_IRcontroller.h>  // DIYables_IRcontroller library

#define IR_RECEIVER_PIN 9  // The Arduino pin connected to IR receiver
#define ENA_PIN 8          // First Motor
#define IN1_PIN 6          // The Arduino pin connected to the IN1 pin L298N
#define IN2_PIN 5          // The Arduino pin connected to the IN2 pin L298N
#define IN3_PIN 4          // The Arduino pin connected to the IN3 pin L298N
#define IN4_PIN 3          // The Arduino pin connected to the IN4 pin L298N
#define ENB_PIN 2          // The Arduino pin connected to the ENB pin L298N

DIYables_IRcontroller_17 irController(IR_RECEIVER_PIN, 200);  // debounce time is 200ms

void setup() {
  Serial.begin(9600);
  irController.begin();

  pinMode(ENA_PIN, OUTPUT);
  pinMode(IN1_PIN, OUTPUT);
  pinMode(IN2_PIN, OUTPUT);
  pinMode(IN3_PIN, OUTPUT);
  pinMode(IN4_PIN, OUTPUT);
  pinMode(ENB_PIN, OUTPUT);

  digitalWrite(ENA_PIN, HIGH);  // set full speed
  digitalWrite(ENB_PIN, HIGH);  // set full speed
}

void loop() {
  Key17 key = irController.getKey();
  if (key != Key17::NONE) {
    switch (key) {
      case Key17::KEY_UP:
        Serial.println("MOVING FORWARD");
        CAR_moveForward();
        break;

      case Key17::KEY_DOWN:
        Serial.println("MOVING BACKWARD");
        CAR_moveBackward();
        break;

      case Key17::KEY_LEFT:
        Serial.println("TURNING LEFT");
        CAR_turnLeft();
        break;

      case Key17::KEY_RIGHT:
        Serial.println("TURNING RIGHT");
        CAR_turnRight();
        break;

      case Key17::KEY_OK:
        Serial.println("STOP");
        CAR_stop();
        break;

      default:
        Serial.println("WARNING: unused key:");
        break;
    }
  }
}

vvoid CAR_moveForward() {
  digitalWrite(IN1_PIN, HIGH);
  digitalWrite(IN2_PIN, LOW);
  digitalWrite(IN3_PIN, HIGH);
  digitalWrite(IN4_PIN, LOW);
}

void CAR_moveBackward() {
  digitalWrite(IN1_PIN, LOW);
  digitalWrite(IN2_PIN, HIGH);
  digitalWrite(IN3_PIN, LOW);
  digitalWrite(IN4_PIN, HIGH);
}

void CAR_turnLeft() {
  digitalWrite(IN1_PIN, HIGH);
  digitalWrite(IN2_PIN, LOW);
  digitalWrite(IN3_PIN, LOW);
  digitalWrite(IN4_PIN, LOW);
}

void CAR_turnRight() {
  digitalWrite(IN1_PIN, LOW);
  digitalWrite(IN2_PIN, LOW);
  digitalWrite(IN3_PIN, HIGH);
  digitalWrite(IN4_PIN, LOW);
}

void CAR_stop() {
  digitalWrite(IN1_PIN, LOW);
  digitalWrite(IN2_PIN, LOW);
  digitalWrite(IN3_PIN, LOW);
  digitalWrite(IN4_PIN, LOW);
}
