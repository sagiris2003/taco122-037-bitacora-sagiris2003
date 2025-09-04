# Clase 5
Hoy trabajaremos con la pantallita OLED

## Array
Array: se puede entender como una cajonera
por ejemplo un ARRAY que se llame "estudiantes" (en esta cajonera tendremos a cada estudiante), en vez de crear 20 variables,
una por cada estudiante, puedo crear esta estructura que agrupe a todos los estudiantes

para declarar el array se hace así

´´´
int numerosLost[] = {4, 8, 15, 16, 23, 42};
String lineasPoema[];
{
"Señor",
"La jaula se ha vuelto pájaro",
"y se ha volado",
"y mi corazón está loco",
"porque aúlla a la muerte",
"y sonríe detrás del viento",
"a mis delirios",
}
void setup() {
Serial.begin(9600);
  // para usar la variable en un array
  //debo ir a buscarlo con nombreArray [indice]
Serial.println(numerosLost[0]);
Serial.println(numerosLost[1]);
Serial.println(numerosLost[2]);
Serial.println(numerosLost[3]);
Serial.println(numerosLost[4]);
Serial.println(numerosLost[5]);
Serial.println(numerosLost[6]);



Serial.println("empezando ciclo for");
//evitamos este tedio usando un ciclo for
//para declarar un ciclo for, debemos tener claras 3 cosas
//1. donde empieza -> 0 -> para esto se crea una variable local
//2. donde termina (condicion de salida)-> 5
//3. como varía -> de 1 en 1
for (int i = 0; i <=5; i++ ){
    Serial.print("i vale ");
    Serial.print(i);
    Serial.print(" so ");
    Serial.println(numerosLost[i]);
    delay(1000);
  }
  }
  Serial.println("salí del ciclo for");
}
void loop() {
  // put your main code here, to run repeatedly:
for (int i = 0; i < 7; i++ ){
Serial.println(lineasPoema[i]);
}
}
´´´
## Pantalla OLED
### Protocolos
usb/serial
i2c (siempre que hay un i2c, en arduino se deben usar los pines 4 y 5)

el pin scl se debe conectar al pin a5 y el sda al pin a4

scl: S.clock
sda: S.data

## Próxima entrega






