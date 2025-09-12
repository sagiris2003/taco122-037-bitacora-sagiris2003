# Encargo 5
En este encargo haré que una frase que escogí vaya subiendo letra a letra por el centro de la pantalla
y que al llegar arriba se vaya para el costado

me ayudé con chatgpt

```
#include <Wire.h>
#include <Adafruit_GFX.h>
#include <Adafruit_SSD1306.h>

#define ANCHO_PANTALLA 128
#define ALTO_PANTALLA 64
#define OLED_ADDR 0x3C  

Adafruit_SSD1306 pantallita(ANCHO_PANTALLA, ALTO_PANTALLA, &Wire);

String frase = "y cuando llegue la aurora llena de goce, se fundan en una sola tu alma y la mia";

void setup() {
  Serial.begin(9600);
  if(!pantallita.begin(SSD1306_SWITCHCAPVCC, OLED_ADDR)) {
    Serial.println(F("No se encontró pantalla SSD1306"));
    for(;;);
  }
  pantallita.clearDisplay();
  pantallita.setTextSize(1);
  pantallita.setTextColor(SSD1306_WHITE);
}

void loop() {
  int xColumna = ANCHO_PANTALLA / 2 - 3; // columna centrada
  int yBase = ALTO_PANTALLA;             // empieza desde abajo

  for (int i = 0; i < frase.length(); i++) {
    pantallita.clearDisplay();

    for (int j = 0; j <= i; j++) {
      int y = yBase - ((i - j + 1) * 8);

      int x = xColumna;

      // si la letra está llegando al top, animamos de izquierda a derecha
      if (y < 16) { // umbral de 16 px desde arriba
        // calculamos desplazamiento horizontal desde la izquierda
        x = map(y, 0, 16, 0, xColumna);
      }

      pantallita.setCursor(x, y);
      pantallita.write(frase[j]);
    }

    pantallita.display();
    delay(150); // velocidad de animación
  }

  delay(1000); // espera antes de reiniciar
} // <- esta llave cierra loop()

```
