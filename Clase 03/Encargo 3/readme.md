# Encargo 3
Debemos escribir en morse el texto que escogimos en la primera clase, esto a través del ledPin que tiene nuestro Arduino UNO.
Mi texto es "para nosotros el cine comienza con cada nuevo zumbido del proyector" del "Manifiesto por los Cien Años del Cine" de Jonas Mekas

```
//comienzo estableciendo los tiempos de los puntos y las rayas

int ledPin = 13;
int tiempoPunto = 200;
int separador = 100;
int tiempoRaya = 500;
int finLetra = 500;

//le indico al arduino que el pin 13 (del led) será OUTPUT
void setup() {
  pinMode(ledPin,OUTPUT);
  //9600 es el baudrate
  //o tasa de baudios
  Serial.begin(9600);

}
