# Tarea 1 ejercicio de medicion
### Nombre: Kenly Augusto Fernandez Barbuis
### Carné: 23-6317

###### La funcion del codigo es el ingreso de un numero cualquiera que pasa a centimetros y apartir de ahi usando los centrimetros puede usar otros metodos de medicion para asi crear una conversion de esos centrimetros.

## Ejercicio en C++
```C++
#include <iostream>

using namespace std;

int main() {
    double centimetros, metros, yardas, varas, pulgadas, pies;
    string unidad_objetivo;

    cout << "Ingrese la longitud en centimetros: ";
    cin >> centimetros;

    cout << "Opciones para trabajar : metros, yardas, varas, pulgadas, pies" << endl;
    cout << "A qué unidad desea convertir: ";
    cin >> unidad_objetivo;

    if (unidad_objetivo == "metros") {
        metros = centimetros / 100;
        cout << metros << " metros" << endl;
    } else if (unidad_objetivo == "yardas") {
        yardas = centimetros / 91.44;
        cout << yardas << " yardas" << endl;
    } else if (unidad_objetivo == "varas") {
        varas = centimetros / 50.8;
        cout << varas << " varas" << endl;
    } else if (unidad_objetivo == "pulgadas") {
        pulgadas = centimetros / 2.54;
        cout << pulgadas << " pulgadas" << endl;
    } else if (unidad_objetivo == "pies") {
        pies = centimetros / 30.48;
        cout << pies << " pies" << endl;
    } else {
        cout << "Sistema de medicion no coincide" << endl;
    }

    return 0;
}
```




## Ejercicio python

```python

centimetros = float(input("Ingrese la longitud en centimetros: "))
unidad_objetivo = input("Opciones para trabajar: metros, yardas, varas, pulgadas, pies\nA qué unidad desea convertir: ")

if unidad_objetivo == "metros":
    metros = centimetros / 100
    print(metros, "metros")
elif unidad_objetivo == "yardas":
    yardas = centimetros / 91.44
    print(yardas, "yardas")
elif unidad_objetivo == "varas":
    varas = centimetros / 50.8
    print(varas, "varas")
elif unidad_objetivo == "pulgadas":
    pulgadas = centimetros / 2.54
    print(pulgadas, "pulgadas")
elif unidad_objetivo == "pies":
    pies = centimetros / 30.48
    print(pies, "pies")
else:
    print("Sistema de medicion no coincide")
```
## Ejercicio PSeInt
```
Algoritmo ConversionUnidadesLongitud
    Definir centimetros, metros, yardas, varas, pulgadas, pies Como Real
    Definir unidad_objetivo Como Cadena
	
    Escribir "Ingrese la longitud en centimetros:"
    Leer centimetros
	
    Escribir "Opciones para trabajar : metros, yardas, varas, pulgadas, pies"
    Escribir "A qué unidad desea convertir:"
    Leer unidad_objetivo
	
    Si unidad_objetivo = "metros" Entonces
        metros <- centimetros / 100
        Escribir metros, " metros"
	Sino Si unidad_objetivo = "yardas" Entonces
			yardas <- centimetros / 91.44
			Escribir yardas, " yardas"
		Sino Si unidad_objetivo = "varas" Entonces
				varas <- centimetros / 50.8
				Escribir varas, " varas"
			Sino Si unidad_objetivo = "pulgadas" Entonces
					pulgadas <- centimetros / 2.54
					Escribir pulgadas, " pulgadas"
					
				Sino Si  unidad_objetivo = "pies" Entonces
						pies <- centimetros / 30.48
						Escribir pies, " pies"
					Sino
						Escribir "Sistema de medicion no coincide"
					FinSi
				FinSi
			FinSi
		FinSi
	FinSi
	
FinAlgoritmo
```