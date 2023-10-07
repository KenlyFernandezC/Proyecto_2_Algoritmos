# Tarea_4
### Nombre: Kenly Augusto Fernandez Barbuis
### Carné: 23-6317 
### Sección: C

## Ejercicio 1 en C++ y Python 
###### Ejercicio 1: escriba una aplicación para resolver el siguiente enunciado. El gobierno ha implementado como parte de su programa social, un subsidio familiar bajo la siguiente reglamentación: Las familias que tienen hasta 2 hijos, reciben Q. 70.00, las que tienen hasta 3 y 5 reciben Q. 90.00 y las que tienen 6 o más reciben Q. 120 mensual. Por cada hijo en edad escolar reciben Q. 10.00 adicionales. Se considera la edad escolar entre 6 y 18 años. Si la madre de familia fuera viuda, la familia recibe Q. 20.00 adicionales. Determinar el monto mensual que recibirá una familia de acuerdo a su realidad familiar a través de una función llamada calcularSubsidio
## C++
```C++

#include <iostream>

using namespace std;

// Función para calcular el subsidio familiar
double calcularSubsidio(int numHijos, int edadEscolar, bool esViuda) {
    double subsidioBase;

    // Determinar el subsidio base según el número de hijos
    if (numHijos <= 2) {
        subsidioBase = 70.00;
    } else if (numHijos >= 3 && numHijos <= 5) {
        subsidioBase = 90.00;
    } else {
        subsidioBase = 120.00;
    }

    // Calcular el monto adicional por hijos en edad escolar
    double montoAdicional = 10.00 * edadEscolar;

    // Calcular el monto adicional si la madre es viuda
    double montoViuda = esViuda ? 20.00 : 0.00;

    // Calcular el subsidio total
    double subsidioTotal = subsidioBase + montoAdicional + montoViuda;

    return subsidioTotal;
}

int main() {
    int numHijos, edadEscolar;
    bool esViuda;

    // Solicitar información de la familia al usuario
    cout << "Numero de hijos: ";
    cin >> numHijos;
    cout << "Edad escolar de los hijos (entre 6 y 18 años): ";
    cin >> edadEscolar;
    cout << "¿La madre es viuda? (1 para si, 0 para no): ";
    cin >> esViuda;

    // Calcular el subsidio familiar
    double subsidio = calcularSubsidio(numHijos, edadEscolar, esViuda);

    // Mostrar el resultado
    cout << "El monto mensual del subsidio familiar es: Q. " << subsidio << endl;

    return 0;
}
```
## Ejercicio 1 en Python

```py
# Función para calcular el subsidio familiar
def calcularSubsidio(numHijos, edadEscolar, esViuda):
    subsidioBase = 0.0

    # Determinar el subsidio base según el número de hijos
    if numHijos <= 2:
        subsidioBase = 70.00
    elif 3 <= numHijos <= 5:
        subsidioBase = 90.00
    else:
        subsidioBase = 120.00

    # Calcular el monto adicional por hijos en edad escolar
    montoAdicional = 10.00 * edadEscolar

    # Calcular el monto adicional si la madre es viuda
    montoViuda = 20.00 if esViuda else 0.00

    # Calcular el subsidio total
    subsidioTotal = subsidioBase + montoAdicional + montoViuda

    return subsidioTotal

# Función principal
def main():
    numHijos = int(input("Número de hijos: "))
    edadEscolar = int(input("Edad escolar de los hijos (entre 6 y 18 años): "))
    esViuda = bool(int(input("¿La madre es viuda? (1 para sí, 0 para no): ")))

    # Calcular el subsidio familiar
    subsidio = calcularSubsidio(numHijos, edadEscolar, esViuda)

    # Mostrar el resultado
    print(f"El monto mensual del subsidio familiar es: Q. {subsidio:.2f}")

if __name__ == "__main__":
    main()

```
## Ejercicio 2 en C++ y Python 
###### Ejercicio 2: escribir una aplicación que solicite al usuario un número que será la longitud de dos vectores que se deben llenar aleatoriamente, sume los valores e indique si ocurre cualquiera de los siguientes escenarios. a) Son iguales, b) vector A es menor a B, c) vector B es menor a A
## Ejercicio 2 en C++

```C++
#include <iostream>
#include <cstdlib> // Para rand() y srand()

using namespace std;

int main() {
    // Solicitar al usuario la longitud de los vectores
    int longitud;
    cout << "Ingrese la longitud de los vectores: ";
    cin >> longitud;

    // Declarar dos arreglos en lugar de vectores
    int vectorA[longitud];
    int vectorB[longitud];

    // Llenar los arreglos aleatoriamente
    for (int i = 0; i < longitud; i++) {
        vectorA[i] = rand() % 100;  // Rellenar con números aleatorios entre 0 y 99
        vectorB[i] = rand() % 100;
    }

    // Sumar los valores de los arreglos
    int sumaA = 0, sumaB = 0;
    for (int i = 0; i < longitud; i++) {
        sumaA += vectorA[i];
        sumaB += vectorB[i];
    }

    // Comprobar los escenarios
    if (sumaA == sumaB) {
        cout << "Los arreglos son iguales." << endl;
    } else if (sumaA < sumaB) {
        cout << "El arreglo A es menor que el arreglo B." << endl;
    } else {
        cout << "El arreglo B es menor que el arreglo A." << endl;
    }

    return 0;
}
```

## Ejercicio 2 en Python
```PY
# Llenar las listas con números aleatorios entre 0 y 99
for _ in range(longitud):
    listaA.append(random.randint(0, 99))
    listaB.append(random.randint(0, 99))

# Sumar los valores de las listas
sumaA = sum(listaA)
sumaB = sum(listaB)

# Comprobar los escenarios
if sumaA == sumaB:
    print("Las listas son iguales.")
elif sumaA < sumaB:
    print("La lista A es menor que la lista B.")
else:
    print("La lista B es menor que la lista A.") 
    
```
## Ejercicio 3 en C++ y Python 
###### Ejercicio 3: en estadística descriptiva, se define el rango de un conjunto de datos reales como la diferencia entre el mayor y el menor de los datos.Escriba un programa que: 
###### a) Pregunte al usuario cuántos datos serán ingresados, 
###### b) Pida al usuario ingresar los datos uno por uno, y entregue como resultado el rango de los datos
## Ejercicio 3 en C++
```C++
#include <iostream>

using namespace std;

int main() {
    int n;
    
    // Preguntar al usuario cuántos datos serán ingresados
    cout << "Ingrese la cantidad de datos: ";
    cin >> n;

    // Verificar que n sea mayor que 1 para calcular el rango
    if (n < 2) {
        cout << "Debe ingresar al menos dos datos para calcular el rango." << endl;
        return 1;
    }

    // Declarar un array estático para almacenar los datos
    double datos[n];
    
    // Solicitar al usuario ingresar los datos uno por uno
    for (int i = 0; i < n; i++) {
        cout << "Ingrese el dato " << i + 1 << ": ";
        cin >> datos[i];
    }

    // Encontrar el valor máximo y mínimo en el array de datos
    double maximo = datos[0];
    double minimo = datos[0];
    
    for (int i = 1; i < n; i++) {
        if (datos[i] > maximo) {
            maximo = datos[i];
        }
        if (datos[i] < minimo) {
            minimo = datos[i];
        }
    }

    // Calcular y mostrar el rango
    double rango = maximo - minimo;
    cout << "El rango de los datos es: " << rango << endl;

    return 0;
}
```
## Ejercicio 3 en Python

```Py
# Preguntar al usuario cuántos datos serán ingresados
n = int(input("Ingrese la cantidad de datos: "))

# Verificar que n sea mayor que 1 para calcular el rango
if n < 2:
    print("Debe ingresar al menos dos datos para calcular el rango.")
else:
    # Declarar una lista para almacenar los datos
    datos = []

    # Solicitar al usuario ingresar los datos uno por uno
    for i in range(n):
        dato = float(input(f"Ingrese el dato {i + 1}: "))
        datos.append(dato)

    # Encontrar el valor máximo y mínimo en la lista de datos
    maximo = datos[0]
    minimo = datos[0]

    for dato in datos[1:]:
        if dato > maximo:
            maximo = dato
        if dato < minimo:
            minimo = dato

    # Calcular y mostrar el rango
    rango = maximo - minimo
    print(f"El rango de los datos es: {rango}")
```
## Ejercicio 4 en C++ y Python 
###### Ejercicio 4: solicite al usuario ingresar un número que será el lado de un cuadrado y escriba un programa que dibuje dicho cuadrado.

## Ejercicio 4 en C++

```C++
#include <iostream>

using namespace std;

int main() {
    int lado;

    // Solicitar al usuario ingresar el lado del cuadrado
    cout << "Ingrese el lado del cuadrado: ";
    cin >> lado;

    // Verificar que el lado sea al menos 2 para dibujar un cuadrado
    if (lado < 2) {
        cout << "El lado debe ser al menos 2 para dibujar un cuadrado." << endl;
        return 1;
    }

    // Dibujar el cuadrado
    for (int i = 0; i < lado; i++) {
        for (int j = 0; j < lado; j++) {
            // Si estamos en el borde o en las esquinas, imprimir "*"
            if (i == 0 || i == lado - 1 || j == 0 || j == lado - 1) {
                cout << "* ";
            } else {
                // De lo contrario, imprimir un espacio en blanco
                cout << "  ";
            }
        }
        cout << endl;
    }

    return 0;
}
```
## Ejercicio 4 en Python
```Py
# Solicitar al usuario ingresar el lado del cuadrado
lado = int(input("Ingrese el lado del cuadrado: "))

# Verificar que el lado sea al menos 2 para dibujar un cuadrado
if lado < 2:
    print("El lado debe ser al menos 2 para dibujar un cuadrado.")
else:
    # Dibujar el cuadrado
    for i in range(lado):
        for j in range(lado):
            # Si estamos en el borde o en las esquinas, imprimir "*"
            if i == 0 or i == lado - 1 or j == 0 or j == lado - 1:
                print("*", end=" ")
            else:
                # De lo contrario, imprimir un espacio en blanco
                print(" ", end=" ")
        print()

```
###### Muestra de ejercicios C++

![Ejercicios](https://i.ibb.co/ZThxWgz/2-ejercicio-C.png) 

![Ejercicios](https://i.ibb.co/s1vn7SZ/3-ejercicio-C.png)

![Ejercicios](https://i.ibb.co/NF4x4jL/4-ejercicio-C.png)

###### Muestra de ejercicios Python

![Ejercicios](https://i.ibb.co/fQ4XcXD/py-1.png) 

![Ejercicios](https://i.ibb.co/vsDg3wJ/py-2.png) 

![Ejercicios](https://i.ibb.co/PspZWzW/py-3.png) 

![Ejercicios](https://i.ibb.co/D8t1ZTR/py-4.png) 