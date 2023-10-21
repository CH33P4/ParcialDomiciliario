# Documentación
![Tinkercad](./img/ArduinoTinkercad.jpg)

## Integrantes 
- Matias A. Espinoza
- Tomas Zampella

## Proyecto: Contador binario.
![Proyecto](https://cdn.discordapp.com/attachments/1158565907921109100/1165369244909850735/image.png)

## Descripción
El proyecto consiste en una maqueta básica utilizando pocos componentes para llevar cuenta de números desde el 0 (cero) hasta el 99 (noventa y nueve) mediante la pulsación de botones: uno que incrementa el valor actual, otro que lo decrementa y un tercero cuya funcionalidad es retornar la cuenta nuevamente a cero.

## Función principal
Utilizamos las variables **buttonUpState**, **buttonDownState** y **resetButtonState** para evaluar que se haya apretado un botón y lo comparamos con su estado anterior (el cual siempre es cero al no ser botones tipo pull-up). Mediante esta lógica simple, el presionar de cada botón incrementa, decrementa o restaura los valores de **counter** (unidad) y **counter2** (decena) para luego representar los números en los displays correspondientes haciendo uso de la función **showNumbers()** e informando el valor actual de la cuenta en el serial a través de la función **printOnSerial()**.

~~~ C
void loop() {
  buttonUpState = digitalRead(plusOne); 
  buttonDownState = digitalRead(minusOne);
  resetButtonState = digitalRead(resetButton);
  if (buttonUpState != lastButtonUpState) {
    if (buttonUpState == HIGH) {
      if(counter < 9){
        counter++;    
      }
      if(counter == 9) {
        counter = 0;
        counter2++;
      }
      printOnSerial(counter, counter2);
      delay(200); 
   	}  
  }
  if (buttonDownState != lastButtonDownState) {
    if (buttonDownState == HIGH) {
      if(counter == 0 && counter2 == 1) {
        counter = 9; 
        counter2--;
      }
      if (counter == 0 && counter2 == 0){
        counter = 0;
      } 
      counter--;
      printOnSerial(counter, counter2);
      delay(200); 
    }
  } 
  if (resetButtonState != lastResetButtonState){
    if (resetButtonState == HIGH){
      counter = 0;
      counter2 = 0;
    }
  }
  showNumbers(counter, counter2);
} 
~~~

## Link al proyecto
- [Proyecto en Tinkercad](https://www.tinkercad.com/things/5phVSGHaVt5-shiny-gaaris/editel?sharecode=mA6AAz2ZPzN4UItgF8Y0vRSVJJgpHxs3HxNfU2h01Ms)
