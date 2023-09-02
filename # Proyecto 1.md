# Proyecto 1
### Nombre: Kenly Augusto Fernandez Barbuis
### Carné: 23-6317 
### Sección: C

## Ejercicio A algoritmo triple de pitagoras

## Ejercicio en Pseint
```Pseint
Algoritmo TriplePitagoras
	
    //Este programa busca y muestra todas las ternas de pitagoras en un rango especifico. dado cuya suma de lados sea igual a 500.
    
    // Definir la variable 'limite' para especificar el rango máximo
    Definir limite Como Entero
    limite <- 500
	
    // Realiza todas las combinaciones posibles de numeros enteros en el rango de 1 a limite
    Para lado1 <- 1 Hasta limite Hacer
        Para lado2 <- 1 Hasta limite Hacer
            Para hipotenusa <- 1 Hasta limite Hacer
                // Verifica si la terna actual cumple el teorema de Pitagoras
                Si lado1^2 + lado2^2 == hipotenusa^2 Entonces
					// Muestra si la terna pitagorica cumple con la condicion
                    Mostrar "Triple de Pitagoras:", lado1, lado2, hipotenusa
                FinSi
            FinPara
        FinPara
    FinPara
	
FinAlgoritmo
```

## Ejercicio en C++

```C++
#include <iostream>

/*
 * Este programa busca y muestra todas las ternas de pitagoras en un rango especifico.
 * Una terna de pitagoras es un conjunto de tres numeros enteros positivos (lado1, lado2 y la hipotenusa) que cumplen con la relacion
 * del teorema de Pitágoras: lado1^2 + lado2^2 = hipotenusa^2.
 */

int main() {
    int limite = 500;

    // Realiza todas las combinaciones posibles de numeros enteros en el rango de 1 a limite
    for (int lado1 = 1; lado1 <= limite; lado1++) {
        for (int lado2 = 1; lado2 <= limite; lado2++) {
            for (int hipotenusa = 1; hipotenusa <= limite; hipotenusa++) {
                // Verifica si la terna actual cumple el teorema de Pitagoras
                if (lado1 * lado1 + lado2 * lado2 == hipotenusa * hipotenusa) {
                    // Muestra si la terna pitagorica cumple con la condicion
                    std::cout << "Triple de Pitagoras: " << lado1 << " " << lado2 << " " << hipotenusa << std::endl;
                }
            }
        }
    }

    return 0;
}

```
## Ejercicio en Python

```py
"""
Este programa busca y muestra todas las ternas de pitagoras en un rango especifico.
Una terna de pitagoras es un conjunto de tres numeros enteros positivos (lado1, lado2 y la hipotenusa) que cumplen con la relacion
del teorema de Pitágoras: lado1^2 + lado2^2 = hipotenusa^2.
"""

# Definir el valor maximo para los lados y la hipotenusa
limite = 500

# Realiza todas las combinaciones posibles de numeros enteros en el rango de 1 a limite
for lado1 in range(1, limite + 1):
    for lado2 in range(1, limite + 1):
        for hipotenusa in range(1, limite + 1):
            # Verifica si la terna actual cumple el teorema de Pitágoras
            if lado1 ** 2 + lado2 ** 2 == hipotenusa ** 2:
                    # Muestra la terna pitagórica que cumple con ambas condiciones
                    print("Triple de Pitagoras con suma de lados igual a 500:", lado1, lado2, hipotenusa)
```

### Video:muestra de funcionamiento y explicacion de los algoritmos

[Video de muestra del algoritmo de triple de pitagoras](https://youtu.be/fnPHY5KPVnE?si=ctSR7o1Q7BNbzFQn)

## Ejercicio B algoritmo ahorcado

### Algoritmo que simula juego del ahorcado 

## Ejercicio en Pseint
```Algoritmo Ahorcado
    // Este algoritmo implementa el juego del ahorcado en el que el jugador debe adivinar una palabra oculta letra por letra antes de agotar sus intentos.
    
    // Declaración de variables
	Definir f, g, k, error, c Como Entero
	Definir letra, secreta, vector1, vector2 Como Caracter
	
	// Solicitar al usuario ingresar la palabra oculta
	Escribir "Ingrese la palabra oculta"
	Leer secreta
	
	g = Longitud(secreta)
	Dimension vector1[g], vector2[g]
	
	// Inicializar los vectores con la palabra oculta y con guiones bajos para ocultarla
	Para f = 1 Hasta g Con Paso 1 Hacer
		vector1[f] = Subcadena(secreta, f, f)
		vector2[f] = "_"
	Fin Para
	
	k = 0
	c = 0
	
	// Iniciar el juego mientras el jugador tenga intentos disponibles
	Mientras k < 6 Hacer
		// Mostrar el estado actual de la palabra oculta
		Para f = 1 Hasta g Con Paso 1 Hacer
			Escribir vector2[f] Sin Saltar
		Fin Para
		Escribir ""
		Escribir "Ingresa una letra"
		Leer letra
		error = 1
		
		// Verificar si la letra ingresada está en la palabra oculta
		Para f = 1 Hasta g Con Paso 1 Hacer
			Si letra == vector1[f] Entonces
				Si vector2[f] == "_" Entonces
					vector2[f] = letra
					c = c + 1
					error = 0
				Fin Si
			Fin Si
		Fin Para
		
		// Verificar si el jugador ha ganado
		Si c == g Entonces
			Escribir "Has ganado el juego"
			k = 7
		SiNo
			// Si no ha ganado, verificar si cometió un error
			Si error == 1 Entonces
				k = k + 1
			Fin Si
			
			// Mostrar el estado del ahorcado en función de los errores
			Si k == 1 Entonces
				Escribir "."
				Escribir "."
				Escribir "."
				Escribir "."
				Escribir "solo te quedan 6 intentos"
			Fin Si
			
			Si k == 2 Entonces
				Escribir "......"
				Escribir ".   o "
				Escribir "."
				Escribir "."
				Escribir "solo te quedan 5 intentos"
			Fin Si
			
			Si k == 3 Entonces
				Escribir "......"
				Escribir ".   o "
				Escribir ".  \|/"
				Escribir "."
				Escribir "solo te quedan 4 intentos"
			Fin Si
			
			Si k == 4 Entonces
				Escribir "......"
				Escribir ".   o "
				Escribir ".  \|/"
				Escribir ".   | "
				Escribir "."
				Escribir "solo te quedan 3 intento"
			Fin Si
			
			Si k == 5 Entonces
				Escribir "......."
				Escribir ".   o  "
				Escribir ".  \|/ "
				Escribir ".   |  "
				Escribir ".  /   "
				Escribir "solo te quedan 2 intento"
			Fin Si
			
			Si k == 6 Entonces
				Escribir "......."
				Escribir ".   o  "
				Escribir ".  \|/ "
				Escribir ".   |  "
				Escribir ".  / \  "
				Escribir "solo te quedan 1 intento"
			Fin Si
			
			Si k == 6 Entonces
				Escribir "......."
				Escribir ".   o  "
				Escribir ".  \|/ "
				Escribir ".   |  "
				Escribir ".  / \  "
				Escribir "Estás ahorcado"
			Fin Si
		Fin Si
	Fin Mientras
Fin Algoritmo
```
## Ejercicio en C++
```c++
#include <iostream>
#include <string>

using namespace std;

/**
 * Esta función implementa el juego del ahorcado.
 */
int main() {
    int f, g, k, error, c;
    char letra;
    string secreta, vector1, vector2;
    
    // Solicitar al usuario ingresar la palabra oculta
    cout << "Ingrese la palabra oculta: ";
    cin >> secreta;
    
    k = secreta.length();          // Obtener la longitud de la palabra secreta
    vector1.resize(k);             // Inicializar vector1 con el tamaño de la palabra
    vector2.resize(k, '_');        // Inicializar vector2 con el tamaño de la palabra, llenándolo con '_'
    
    // Copiar la palabra secreta a vector1 y llenar vector2 con '_'
    for (f = 0; f < k; f++) {
        vector1[f] = secreta[f];
    }
    
    // Inicializar variables
    f = 0;                          // Contador de intentos fallidos
    c = 0;                          // Contador de letras correctas
    
    // Comienza el juego
    while (f < 7) {
        // Mostrar las letras adivinadas y espacios
        for (g = 0; g < k; g++) {
            cout << vector2[g];
        }
        cout << endl << endl;
        
        // Solicitar al usuario ingresar una letra
        cout << "Ingresa una letra: ";
        cin >> letra;
        error = 1;   // Inicializar la bandera de error
        
        // Verificar si la letra ingresada está en la palabra secreta
        for (g = 0; g < k; g++) {
            if (letra == vector1[g]) {
                if (vector2[g] == '_') {
                    vector2[g] = letra;
                    c++;
                    error = 0;
                }
            }
        }
        
        // Verificar si se ha adivinado toda la palabra
        if (c == k) {
            cout << "Has ganado el juego" << endl;
            f = 7;  // Terminar el juego si se adivina la palabra
        } else {
            if (error == 1) {
                f++;  // Incrementar el contador de intentos fallidos si se cometió un error
            }
            
            // Mostrar el estado actual del ahorcado
            switch (f) {
                case 1:
                    cout << "." << endl;
                    cout << "." << endl;
                    cout << "." << endl;
                    cout << "." << endl;
                    cout << "solo te quedan 6 intentos" << endl;
                    break;
                case 2:
                    cout << "......" << endl;
                    cout << ".   o " << endl;
                    cout << "." << endl;
                    cout << "." << endl;
                    cout << "solo te quedan 5 intentos" << endl;
                    break;
                case 3:
                    cout << "......" << endl;
                    cout << ".   o " << endl;
                    cout << ".  \|/" << endl;
                    cout << "." << endl;
                    cout << "solo te quedan 4 intentos" << endl;
                    break;
                case 4:
                    cout << "......" << endl;
                    cout << ".   o " << endl;
                    cout << ".  \|/" << endl;
                    cout << ".   | " << endl;
                    cout << "." << endl;
                    cout << "solo te quedan 3 intentos" << endl;
                    break;
                case 5:
                    cout << "......." << endl;
                    cout << ".   o  " << endl;
                    cout << ".  \|/ " << endl;
                    cout << ".   |  " << endl;
                    cout << ".  /   " << endl;
                    cout << "solo te quedan 2 intentos" << endl;
                    break;
                case 6:
                    cout << "......." << endl;
                    cout << ".   o  " << endl;
                    cout << ".  \|/ " << endl;
                    cout << ".   |  " << endl;
                    cout << ".  / \ " << endl;
                    cout << "solo te quedan 1 intento" << endl;
                    break;
                case 7:
                    cout << "......." << endl;
                    cout << ".   o  " << endl;
                    cout << ".  \|/ " << endl;
                    cout << ".   |  " << endl;
                    cout << ".  / \ " << endl;
                    cout << "Estas ahorcado" << endl;
                    break;
            }
        }
    }
    
    return 0;
}
```

## Ejercicio en Python
```py
def main():
    """
    Función principal del juego del ahorcado.
    """
    secreta = input("Ingrese la palabra oculta: ")  # Solicitar al usuario ingresar la palabra secreta
    k = len(secreta)  # Obtener la longitud de la palabra secreta
    vector1 = list(secreta)  # Convertir la palabra en una lista de caracteres
    vector2 = ['_'] * k  # Inicializar vector2 con '_' para ocultar la palabra secreta

    f = 0  # Contador de intentos fallidos
    c = 0  # Contador de letras correctas

    while f < 7:  # Límite de 7 intentos
        print(' '.join(vector2))  # Mostrar las letras adivinadas y espacios
        print()
        letra = input("Ingresa una letra: ")  # Solicitar al usuario ingresar una letra
        error = 1  # Inicializar la bandera de error

        for g in range(k):
            if letra == vector1[g]:
                if vector2[g] == '_':
                    vector2[g] = letra  # Actualizar vector2 con la letra correcta
                    c += 1  # Incrementar el contador de letras correctas
                    error = 0  # Cambiar la bandera de error a falso

        if c == k:
            print("Has ganado el juego")
            f =  7 # Terminar el juego si se adivina la palabra
        else:
            if error == 1:
                f += 1  # Incrementar el contador de intentos fallidos si se cometió un error

            # Mostrar el estado actual del ahorcado
            if f == 1:
                print(".")
                print(".")
                print(".")
                print(".")
                print("solo te quedan 6 intentos")
            elif f == 2:
                print("......")
                print(".   o ")
                print(".")
                print(".")
                print("solo te quedan 5 intentos")
            elif f == 3:
                print("......")
                print(".   o ")
                print(".  \|/")
                print(".")
                print("solo te quedan 4 intentos")
            elif f == 4:
                print("......")
                print(".   o ")
                print(".  \|/")
                print(".   | ")
                print(".")
                print("solo te quedan 3 intentos")
            elif f == 5:
                print(".......")
                print(".   o  ")
                print(".  \|/ ")
                print(".   |  ")
                print(".  /   ")
                print("solo te quedan 2 intentos")
            elif f == 6:
                print(".......")
                print(".   o  ")
                print(".  \|/ ")
                print(".   |  ")
                print(".  / \ ")
                print("solo te quedan 1 intento")
            elif f == 7:
                print(".......")
                print(".   o  ")
                print(".  \|/ ")
                print(".   |  ")
                print(".  / \ ")
                print("Estás ahorcado")

if __name__ == "__main__":
    main()

```

### Video:muestra de funcionamiento y explicacion de los algoritmos

[Video de muestra del algoritmo del juego de ahorcado](https://youtu.be/-K3Q5gV6GDw?si=rER_XJ5etmoKCYWg)
