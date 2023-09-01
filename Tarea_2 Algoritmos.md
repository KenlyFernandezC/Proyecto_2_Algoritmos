# Tarea_2 Algoritmos
### Nombre: Kenly Augusto Fernandez Barbuis
### Carné: 23-6317 
### Sección: C

### Algoritmo que genera triangulos rectangulos

## Ejercicio en Pseint

```Pseint
Algoritmo TriangulosRectangulos
    Definir g, h, j Como Entero
    Escribir "Ingresa un número entero positivo:"
    Leer j
    
    Si j > 0 Entonces
        Escribir "Elige el tipo de triángulo rectángulo:"
        Escribir "1. Triángulo rectángulo con base en la parte inferior izquierda."
        Escribir "2. Triángulo rectángulo con base en la parte inferior derecha."
        Escribir "3. Triángulo con catetos arriba."
        Escribir "4. Triángulo con catetos abajo."
        Leer h
		
        Segun h Hacer
            1:
                para g = 1 Hasta j Con Paso 1 Hacer
                    para h = 1 Hasta g Con Paso 1 Hacer
                        Escribir "*"," " Sin Saltar
                    FinPara
                    Escribir ""
                FinPara
            2:
                para g = 1 Hasta j Con Paso 1 Hacer
                    para h = 1 Hasta j - g Con Paso 1 Hacer
                        Escribir " "," " Sin Saltar
                    FinPara
                    para h = 1 Hasta g Con Paso 1 Hacer
                        Escribir "*"," " Sin Saltar
                    FinPara
                    Escribir ""
                FinPara
            3:
                para g = j Hasta 1 Con Paso -1 Hacer
                    para h = 1 Hasta g Con Paso 1 Hacer
                        Escribir "*"," " Sin Saltar
                    FinPara
                    Escribir ""
                FinPara
            4:
                para g = 1 Hasta j Con Paso 1 Hacer
                    para h = 1 Hasta g - 1 Con Paso 1 Hacer
                        Escribir " "," " Sin Saltar
                    FinPara
                    para h = 1 Hasta j - g + 1 Con Paso 1 Hacer
                        Escribir "*"," " Sin Saltar
                    FinPara
                    Escribir ""
                FinPara
   
                Escribir "Opción no válida"
        Fin Segun
    Sino
        Escribir "El número debe ser positivo."
    Fin Si
	
FinAlgoritmo
```

## Ejercicio en C++
```C++
//Este algoritmo solicita al usuario ingresar un numero entero positivo y seguidamente pedira que ingrese una de las 4 opcines para generar un triangulo rectanguloEste algoritmo solicita al usuario ingresar un numero entero positivo y seguidamente pedira que ingrese una de las 4 opcines para generar un triangulo rectangulo
#include <iostream>
using namespace std;

int main() {
    int g, h, j;
    cout << "Ingresa un numero entero positivo:" << endl;
    cin >> j;
    
    if (j > 0) {
        cout << "Elige el tipo de triangulo rectangulo:" << endl;
        cout << "1. Triangulo rectángulo con base en la parte inferior izquierda." << endl;
        cout << "2. Triangulo rectángulo con base en la parte inferior derecha." << endl;
        cout << "3. Triangulo con catetos arriba." << endl;
        cout << "4. Triangulo con catetos abajo." << endl;
        cin >> h;
		
        if (h == 1) {
            for (g = 1; g <= j; g++) {
                for (h = 1; h <= g; h++) {
                    cout << "* ";
                }
                cout << endl;
            }
        } else if (h == 2) {
            for (g = 1; g <= j; g++) {
                for (h = 1; h <= j - g; h++) {
                    cout << "  ";
                }
                for (h = 1; h <= g; h++) {
                    cout << "* ";
                }
                cout << endl;
            }
        } else if (h == 3) {
            for (g = j; g >= 1; g--) {
                for (h = 1; h <= g; h++) {
                    cout << "* ";
                }
                cout << endl;
            }
        } else if (h == 4) {
            for (g = 1; g <= j; g++) {
                for (h = 1; h <= g - 1; h++) {
                    cout << "  ";
                }
                for (h = 1; h <= j - g + 1; h++) {
                    cout << "* ";
                }
                cout << endl;
            }
        } else {
            cout << "Opcion no valida" << endl;
        }
    } else {
        cout << "El numero debe ser positivo." << endl;
    }
    
    return 0;
}
```

## Ejercicio en Python
```Py
#Este algoritmo solicita al usuario ingresar un numero entero positivo y seguidamente pedira que ingrese una de las 4 opcines para generar un triangulo rectangulo
def main():
    g, h, j = 0, 0, 0
    print("Ingresa un número entero positivo:")
    j = int(input())
    
    if j > 0:
        print("Elige el tipo de triángulo rectángulo:")
        print("1. Triángulo rectángulo con base en la parte inferior izquierda.")
        print("2. Triángulo rectángulo con base en la parte inferior derecha.")
        print("3. Triángulo con catetos arriba.")
        print("4. Triángulo con catetos abajo.")
        h = int(input())
		
        if h == 1:
            for g in range(1, j+1):
                for h in range(1, g+1):
                    print("*", end=" ")
                print()
        elif h == 2:
            for g in range(1, j+1):
                for h in range(1, j-g+1):
                    print(" ", end=" ")
                for h in range(1, g+1):
                    print("*", end=" ")
                print()
        elif h == 3:
            for g in range(j, 0, -1):
                for h in range(1, g+1):
                    print("*", end=" ")
                print()
        elif h == 4:
            for g in range(1, j+1):
                for h in range(1, g):
                    print(" ", end=" ")
                for h in range(1, j-g+2):
                    print("*", end=" ")
                print()
        else:
            print("Opción no válida")
    else:
        print("El número debe ser positivo.")

if __name__ == "__main__":
    main()
```