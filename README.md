# C-digo-para-girar-o-motor
const int chaveDireita = 2;
const int chaveEsquerda = 3;
const int pin1 = 4;
const int pin2 = 5;
const int pinEnable = 6;
const int pinPot = A0;

void setup() {

  pinMode(pin1, OUTPUT);
  pinMode(pin2, OUTPUT);
  pinMode(pinEnable, OUTPUT);

  pinMode(chaveDireita, INPUT_PULLUP);
  pinMode(chaveEsquerda, INPUT_PULLUP);

}

void loop() {

  int leituraPot = analogRead(pinPot);
  int velocidade = map(leituraPot, 0, 1023, 0, 255); // Regra de três para conversão de valores

  analogWrite(pinEnable, velocidade);

  if (digitalRead(chaveEsquerda) == LOW && digitalRead(chaveDireita) == LOW) {

    digitalWrite(pin1, LOW);
    digitalWrite(pin2, LOW);

  }

  else if (digitalRead(chaveDireita) == LOW) {

    digitalWrite(pin1, HIGH);
    digitalWrite(pin2, LOW);

  }

  else if (digitalRead(chaveEsquerda) == LOW) {

    digitalWrite(pin1, LOW);
    digitalWrite(pin2, HIGH);

  }

  else {

    digitalWrite(pin1, LOW);
    digitalWrite(pin2, LOW);

  }
}
