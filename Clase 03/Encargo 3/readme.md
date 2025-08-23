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

//estableceré una función que genere un punto
void punto(){
//prendemos el punto
digitalWrite(ledPin,HIGH);
    Serial.println("punto");
    //esperamos el punto encendido
    delay(tiempoPunto);
    //apagamos el punto
    digitalWrite(ledPin,LOW);
    //el espacio despues del punto
    delay(separador);
}

//establezco una función que genere una raya
void raya(){
  //prendemos la raya
   digitalWrite(ledPin,HIGH);
    Serial.println("raya");
    //espero el tiempo de la raya
    delay(tiempoRaya);
    //apagamos la raya
    digitalWrite(ledPin,LOW);
}

//ahora estableceré una función por cada letra del abecedario
//para poder escribir libremente
void a(){
  punto();raya();
}

void b(){
raya();punto();punto();punto();
}

void c(){
  raya();punto();raya();punto();
}

void d(){
  raya();punto();punto();
}

void e(){
  punto();
}

void f(){
  punto();punto();raya();punto();
}
```

en este punto me pregunté qué pasa si en vez de que la función sea "raya" o "punto"
que sea "." o "-"
por esto abrí otro sketch de arduino para probarlo
escribí lo siguiente

```
int ledPin = 13;
int tiempoPunto = 200;
int separador = 100;
int tiempoRaya = 500;
int finLetra = 500;

void setup() {
  pinMode(ledPin,OUTPUT);
  //9600 es el baudrate
  //o tasa de baudios
  Serial.begin(9600);

}

//estableceré una función que genere un punto
void .(){
//prendemos el punto
digitalWrite(ledPin,HIGH);
    Serial.println("punto");
    //esperamos el punto encendido
    delay(tiempoPunto);
    //apagamos el punto
    digitalWrite(ledPin,LOW);
    //el espacio despues del punto
    delay(separador);
}

//establezco una función que genere una raya
void -(){
  //prendemos la raya
   digitalWrite(ledPin,HIGH);
    Serial.println("raya");
    //espero el tiempo de la raya
    delay(tiempoRaya);
    //apagamos la raya
    digitalWrite(ledPin,LOW);
}

//ahora estableceré una función por cada letra del abecedario
//para poder escribir libremente
void a(){
  .();-();
}

void loop(){
a()
}
```
no funcionó así que seguí estableciendo el abecedario
así quedó el código

```
//debo escribir el texto "para nosotros el cine comienza
// con cada nuevo zumbido del proyector"

int ledPin = 13;
int tiempoPunto = 200;
int separador = 100;
int tiempoRaya = 500;
int finLetra = 500;

void setup() {
  pinMode(ledPin,OUTPUT);
  //9600 es el baudrate
  //o tasa de baudios
  Serial.begin(9600);

}

//estableceré una función que genere un punto
void punto(){
//prendemos el punto
digitalWrite(ledPin,HIGH);
    Serial.println("punto");
    //esperamos el punto encendido
    delay(tiempoPunto);
    //apagamos el punto
    digitalWrite(ledPin,LOW);
    //el espacio despues del punto
    delay(separador);
}

//establezco una función que genere una raya
void raya(){
  //prendemos la raya
   digitalWrite(ledPin,HIGH);
    Serial.println("raya");
    //espero el tiempo de la raya
    delay(tiempoRaya);
    //apagamos la raya
    digitalWrite(ledPin,LOW);
}

//ahora estableceré una función por cada letra del abecedario
//para poder escribir libremente
void a(){
  punto();raya();
}

void b(){
raya();punto();punto();punto();
}

void c(){
  raya();punto();raya();punto();
}

void d(){
  raya();punto();punto();
}

void e(){
  punto();
}

void f(){
  punto();punto();raya();punto();
}

void g(){
  raya();raya();punto();
}

void h(){
  punto();punto();punto();punto();
}

void i(){
  punto();punto();
}

void j(){
  punto();raya();raya();raya();
}

void k(){
  raya();punto();raya();
}

void l;(){
  punto();raya();punto();punto();
}

void m;(){
  raya();raya();
}

void n();{
  raya();punto();
}

void o();{
  raya();raya();raya();
}

void p();{
  punto();raya();raya();punto();
}

void q();{
  raya();raya();punto();raya();
}

void r();{
  punto();raya();punto();
}

void s();{
  punto();punto();punto();
}

void t();{
raya();
}

void u();{
  punto();punto();raya();
}

void v();{
  punto();punto();punto();raya();
}

void w();{
  punto();raya();raya();
}

void x();{
  raya();punto();punto();raya();
}

void y();{
  raya();punto();raya();raya();
}

void z();{
  raya();raya();punto();punto();
}

//estableceré el loop
void loop() {
  // escribo el texto con las funciones de letras
p();
a();
r();
a();
n();
o();
s();
o();
t();
r();
o();
s();
e();
l();
c();
i();
n();
e();
c();
o(),
m();
i();
e();
n();
z();
a();
c();
o();
n();
c();
a();
d();
a();
n();
u();
e();
v();
o();
z();
u();
m();
b();
i();
d();
o();
d();
e();
l();
p();
r();
o();
y();
e();
c();
t();
o();
r();
}
```
no funcionó porque cuando establezco la función de las letras (desde la l)
pongo un ; después del paréntesis, por lo que tengo que corregirlo.

habiéndolo corregido, fui ajustando los tiempos de los puntos, las rayas, los separadores y los fines de letra.
me di cuenta que no separaba entre letra y letra y es porque al establecer 
las funciones de las letras, no le puse el fin de letra

la función de las letras quedaría así

```
void a(){
  punto();raya();delay(finLetra);
}
``

además agregué las siguientes variables
```
int finPalabra = 2000;
int finFrase = 5000;
```
el código de mi texto en morse queda así

```
//debo escribir el texto "para nosotros el cine comienza
// con cada nuevo zumbido del proyector"

int ledPin = 13;
int tiempoPunto = 300;
int separador = 250;
int tiempoRaya = 700;
int finLetra = 1000;
int finPalabra = 2000;
int finFrase = 5000;
void setup() {
  pinMode(ledPin,OUTPUT);
  //9600 es el baudrate
  //o tasa de baudios
  Serial.begin(9600);

}


//estableceré una función que genere un punto
void punto(){
//prendemos el punto
digitalWrite(ledPin,HIGH);
    Serial.println("punto");
    //esperamos el punto encendido
    delay(tiempoPunto);
    //apagamos el punto
    digitalWrite(ledPin,LOW);
    //el espacio despues del punto
    delay(separador);
}

//establezco una función que genere una raya
void raya(){
  //prendemos la raya
   digitalWrite(ledPin,HIGH);
    Serial.println("raya");
    //espero el tiempo de la raya
    delay(tiempoRaya);
    //apagamos la raya
    digitalWrite(ledPin,LOW);
    delay(separador);
}


//ahora estableceré una función por cada letra del abecedario
//para poder escribir libremente
void a(){
  punto();raya();delay(finLetra);
}

void b(){
raya();punto();punto();punto();delay(finLetra);
}

void c(){
  raya();punto();raya();punto();delay(finLetra);
}

void d(){
  raya();punto();punto();delay(finLetra);
}

void e(){
  punto();delay(finLetra);
}

void f(){
  punto();punto();raya();punto();delay(finLetra);
}

void g(){
  raya();raya();punto();delay(finLetra);
}

void h(){
  punto();punto();punto();punto();delay(finLetra);
}

void i(){
  punto();punto();delay(finLetra);
}

void j(){
  punto();raya();raya();raya();delay(finLetra);
}

void k(){
  raya();punto();raya();delay(finLetra);
}

void l(){
  punto();raya();punto();punto();delay(finLetra);
}

void m(){
  raya();raya();delay(finLetra);
}

void n(){
  raya();punto();delay(finLetra);
}

void o(){
  raya();raya();raya();delay(finLetra);
}

void p(){
  punto();raya();raya();punto();delay(finLetra);
}

void q(){
  raya();raya();punto();raya();delay(finLetra);
}

void r(){
  punto();raya();punto();delay(finLetra);
}

void s(){
  punto();punto();punto();delay(finLetra);
}

void t(){
raya();delay(finLetra);
}

void u(){
  punto();punto();raya();delay(finLetra);
}

void v(){
  punto();punto();punto();raya();delay(finLetra);
}

void w(){
  punto();raya();raya();delay(finLetra);
}

void x(){
  raya();punto();punto();raya();delay(finLetra);
}

void y(){
  raya();punto();raya();raya();delay(finLetra);
}

void z(){
  raya();raya();punto();punto();delay(finLetra);
}

//estableceré el loop
void loop() {
  // escribo el texto con las funciones de letras
p();
a();
r();
a();
delay (finPalabra);
n();
o();
s();
o();
t();
r();
o();
s();
delay (finPalabra);
e();
l();
delay (finPalabra);
c();
i();
n();
e();
delay (finPalabra);
c();
o(),
m();
i();
e();
n();
z();
a();
delay (finPalabra);
c();
o();
n();
delay (finPalabra);
c();
a();
d();
a();
delay (finPalabra);
n();
u();
e();
v();
o();
delay (finPalabra);
z();
u();
m();
b();
i();
d();
o();
delay (finPalabra);
d();
e();
l();
delay (finPalabra);
p();
r();
o();
y();
e();
c();
t();
o();
r();
delay (finFrase);

}
```


