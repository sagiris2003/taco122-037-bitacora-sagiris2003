## Encargo 4
debemos usar la estructura if para alterar el brillo del led

```
int potPin = A0;   // potenciómetro
int ledPin = 6;    // LED en pin PWM
int valorPot = 0; 
int intensidadLed = 0;

unsigned long tiempoAnterior = 0; // guarda el último tiempo
unsigned long intervalo = 0;    // intervalo que cambia con el potenciómetro

void setup() {
  pinMode(ledPin, OUTPUT);
  Serial.begin(9600);
}

void loop() {
  unsigned long tiempoActual = millis();

  valorPot = analogRead(potPin); // leer el potenciómetro (0 a 1023)

  
  if (tiempoActual - tiempoAnterior >= intervalo) {
    tiempoAnterior = tiempoActual;

    // Cambiar el brillo con if, pero con otros rangos
    if (valorPot < 300) {
      intensidadLed = 50;   // brillo muy bajo
    } 
    else if (valorPot < 600) {
      intensidadLed = 150;  // brillo medio
    } 
    else if (valorPot < 900) {
      intensidadLed = 220;  // brillo alto
    } 
    else {
      intensidadLed = 255;  // brillo máximo
    }

    analogWrite(ledPin, intensidadLed);

    Serial.print("Potenciometro: ");
    Serial.print(valorPot);
    Serial.print("  -> Brillo: ");
    Serial.print(intensidadLed);
    Serial.print("  -> Intervalo: ");
    Serial.println(intervalo);
  }
}
```
Este código lo hice basándome en los demás códigos que vimos en la clase y me ayudé con chatgpt
para comprender cómo funcionaban las cosas.
al principio chatgpt me daba un código con map()
pero encontré que no era necesario, porque sino debía esperar 
que acabara el intervalo para que cambiara la intensidad del led
