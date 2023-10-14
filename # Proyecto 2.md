# Proyecto 2
### Nombre: Kenly Augusto Fernandez Barbuis
### Carné: 23-6317 
### Sección: C


## Ejercicio en C++
# Documentacion externa en C++ y Python
###### Guía de Uso del Programa de Gestión de Productos
---
###### Este programa te permite gestionar una lista de productos almacenados en un archivo de texto. Puedes elegir entre una versión en C++ o Python para ejecutar el programa, según tu preferencia.

## 1. Ejecución del Programa en C++

##### Asegúrate de tener un entorno de desarrollo C++ o un compilador compatible. Puedes compilar y ejecutar el código siguiendo estos pasos:

###### Abre una terminal o línea de comandos.

###### Navega al directorio donde se encuentra el archivo C++ (por ejemplo, "gestion_productos.cpp") utilizando el comando cd (cambiar directorio).

###### Compila el programa C++, por ejemplo, con g++ gestion_productos.cpp -o gestion_productos (asegúrate de que tengas g++ instalado).

###### Ejecuta el programa con ./gestion_productos.

## 2. Ejecución del Programa en Python

###### Asegúrate de tener Python instalado en tu sistema. Puedes descargar e instalar Python desde python.org si aún no lo tienes instalado.

###### Para ejecutar el programa Python, sigue estos pasos:

###### Guarda el código Python en un archivo con extensión ".py" (por ejemplo, "gestion_productos.py").

###### Abre una terminal o línea de comandos.

###### Navega al directorio donde se encuentra el archivo ".py" utilizando el comando cd (cambiar directorio).

###### Ejecuta el programa con python gestion_productos.py.

## 3. Menú de Opciones (C++ y Python)

###### Una vez que el programa esté en funcionamiento, se mostrará un menú de opciones con las siguientes acciones disponibles:

#### 1: Agregar producto: Permite agregar un nuevo producto a la lista.

#### 2: Buscar producto: Permite buscar productos por código o nombre y muestra la información de los productos coincidentes.

#### 3: Modificar producto: Permite modificar los datos de un producto existente. Debes ingresar el código del producto que deseas modificar y luego actualizar sus detalles.

#### 4: Salir: Termina el programa y guarda automáticamente los cambios en el archivo "productos.txt".

## 4. Agregar un Nuevo Producto (C++ y Python)

###### Cuando seleccionas la opción "Agregar producto" (opción 1), el programa te solicitará ingresar la siguiente información para el nuevo producto:

###### Nombre
###### Código (debe ser único)
###### Precio
###### Proveedor
###### Existencia
###### Estado (Aprobado o Reprobado)
###### Descuento
###### El programa verificará si el código del producto ya existe en la lista antes de agregarlo. Luego, se mostrará un mensaje de éxito o error.

## 5. Buscar Producto (C++ y Python)

###### La opción "Buscar producto" (opción 2) permite buscar productos por código o nombre. Debes ingresar un término de búsqueda y el programa mostrará la información de los productos que coincidan con el código o contengan el término en su nombre.

## 6. Modificar Producto Existente (C++ y Python)

###### Si eliges la opción "Modificar producto" (opción 3), el programa te pedirá ingresar el código del producto que deseas modificar. Luego, puedes actualizar los siguientes detalles del producto:

###### Nombre
###### Precio
###### Proveedor
###### Existencia
###### Estado
###### Descuento
###### Los cambios se guardarán automáticamente en el archivo "productos.txt", y recibirás un mensaje de éxito o error.

## 7. Salir del Programa (C++ y Python)

###### Cuando hayas terminado de gestionar productos, selecciona la opción "Salir" (opción 4) en el menú. El programa guardará automáticamente los cambios en el archivo "productos.txt" y se cerrará.

## 8. Almacenamiento de Datos (C++ y Python)

###### Los productos se almacenan en un archivo de texto llamado "productos.txt" en el mismo directorio donde se encuentra el archivo de programa (C++ o Python). Asegúrate de que el archivo esté en la misma ubicación que el ejecutable del programa (en el caso de C++) o el archivo ".py" (en el caso de Python), o proporciona la ruta correcta al archivo si es necesario.
---
```C++

#include <iostream>
#include <fstream>
#include <vector>
#include <string>

using namespace std;

// Definición de la estructura Producto
struct Producto {
    string nombre;
    string codigo;
    float precio;
    string proveedor;
    int existencia;
    char estado; // Aprobado (A) o Reprobado (R)
    float descuento;
};

// Función para crear un archivo de texto y guardar los productos en él.
void CrearArchivo(const vector<Producto>& productos) {
    ofstream archivo("productos.txt");
    if (archivo.is_open()) {
        for (size_t i = 0; i < productos.size(); ++i) {
            const Producto& producto = productos[i];
            archivo << producto.nombre << ","
                    << producto.codigo << ","
                    << producto.precio << ","
                    << producto.proveedor << ","
                    << producto.existencia << ","
                    << producto.estado << ","
                    << producto.descuento << "\n";
        }
        archivo.close();
    } else {
        cerr << "Error al crear el archivo." << endl;
    }
}

// Función para leer productos desde un archivo de texto.
void LeerArchivo(vector<Producto>& productos) {
    ifstream archivo("productos.txt");
    if (archivo.is_open()) {
        productos.clear();
        string linea;
        while (getline(archivo, linea)) {
            Producto producto;
            sscanf(linea.c_str(), "%[^,],%[^,],%f,%[^,],%d,%c,%f",
                   &producto.nombre[0], &producto.codigo[0], &producto.precio,
                   &producto.proveedor[0], &producto.existencia, &producto.estado, &producto.descuento);
            productos.push_back(producto);
        }
        archivo.close();
    } else {
        cerr << "El archivo no existe, se creará uno nuevo al agregar productos." << endl;
    }
}

// Función para agregar un nuevo producto a la lista.
void AgregarProducto(vector<Producto>& productos) {
    Producto producto;
    cout << "Nombre: ";
    cin >> producto.nombre;
    cout << "Código: ";
    cin >> producto.codigo;

    for (size_t i = 0; i < productos.size(); ++i) {
        if (productos[i].codigo == producto.codigo) {
            cerr << "El código de producto ya existe." << endl;
            return;
        }
    }

    cout << "Precio: ";
    cin >> producto.precio;
    cout << "Proveedor: ";
    cin >> producto.proveedor;
    cout << "Existencia: ";
    cin >> producto.existencia;
    cout << "Estado (A/R): ";
    cin >> producto.estado;
    cout << "Descuento: ";
    cin >> producto.descuento;

    productos.push_back(producto);
    CrearArchivo(productos);
    cout << "Producto agregado con éxito." << endl;
}

// Función para buscar productos por código o nombre.
void BuscarProducto(const vector<Producto>& productos) {
    string busqueda;
    cout << "Buscar por código o nombre: ";
    cin >> busqueda;

    for (size_t i = 0; i < productos.size(); ++i) {
        const Producto& producto = productos[i];
        if (producto.codigo == busqueda || producto.nombre.find(busqueda) != string::npos) {
            cout << "Nombre: " << producto.nombre << endl;
            cout << "Código: " << producto.codigo << endl;
            cout << "Precio: " << producto.precio << endl;
            cout << "Proveedor: " << producto.proveedor << endl;
            cout << "Existencia: " << producto.existencia << endl;
            cout << "Estado: " << producto.estado << endl;
            cout << "Descuento: " << producto.descuento << endl;
        }
    }
}

// Función para modificar los datos de un producto.
void ModificarProducto(vector<Producto>& productos) {
    string codigo;
    cout << "Ingrese el código del producto a modificar: ";
    cin >> codigo;

    for (size_t i = 0; i < productos.size(); ++i) {
        if (productos[i].codigo == codigo) {
            cout << "Nuevo nombre: ";
            cin >> productos[i].nombre;
            cout << "Nuevo precio: ";
            cin >> productos[i].precio;
            cout << "Nuevo proveedor: ";
            cin >> productos[i].proveedor;
            cout << "Nueva existencia: ";
            cin >> productos[i].existencia;
            cout << "Nuevo estado (A/R): ";
            cin >> productos[i].estado;
            cout << "Nuevo descuento: ";
            cin >> productos[i].descuento;
            CrearArchivo(productos);
            cout << "Producto modificado con éxito." << endl;
            return;
        }
    }
    cerr << "Producto no encontrado." << endl;
}

int main() {
    vector<Producto> productos;
    LeerArchivo(productos);

    while (true) {
        cout << "Menú:\n1. Agregar producto\n2. Buscar producto\n3. Modificar producto\n4. Salir\n";
        int opcion;
        cin >> opcion;

        switch (opcion) {
            case 1:
                AgregarProducto(productos);
                break;
            case 2:
                BuscarProducto(productos);
                break;
            case 3:
                ModificarProducto(productos);
                break;
            case 4:
                CrearArchivo(productos);
                return 0;
            default:
                cerr << "Opción inválida." << endl;
        }
    }

    return 0;
}
```

```Py
import os

# Definición de la estructura Producto
class Producto:
    def __init__(self, nombre, codigo, precio, proveedor, existencia, estado, descuento):
        self.nombre = nombre
        self.codigo = codigo
        self.precio = precio
        self.proveedor = proveedor
        self.existencia = existencia
        self.estado = estado
        self.descuento = descuento

# Función para crear un archivo de texto y guardar los productos en él.
def crear_archivo(productos):
    with open("productos.txt", "w") as archivo:
        for producto in productos:
            archivo.write(f"{producto.nombre},{producto.codigo},{producto.precio},{producto.proveedor},{producto.existencia},{producto.estado},{producto.descuento}\n")

# Función para leer productos desde un archivo de texto.
def leer_archivo():
    productos = []
    if os.path.exists("productos.txt"):
        with open("productos.txt", "r") as archivo:
            for linea in archivo:
                datos = linea.strip().split(",")
                if len(datos) == 7:
                    nombre, codigo, precio, proveedor, existencia, estado, descuento = datos
                    producto = Producto(nombre, codigo, float(precio), proveedor, int(existencia), estado, float(descuento))
                    productos.append(producto)
    else:
        print("El archivo no existe, se creará uno nuevo al agregar productos.")
    return productos

# Función para agregar un nuevo producto a la lista.
def agregar_producto(productos):
    nombre = input("Nombre: ")
    codigo = input("Código: ")

    for producto in productos:
        if producto.codigo == codigo:
            print("El código de producto ya existe.")
            return

    precio = float(input("Precio: "))
    proveedor = input("Proveedor: ")
    existencia = int(input("Existencia: "))
    estado = input("Estado (A/R): ")
    descuento = float(input("Descuento: "))

    producto = Producto(nombre, codigo, precio, proveedor, existencia, estado, descuento)
    productos.append(producto)
    crear_archivo(productos)
    print("Producto agregado con éxito.")

# Función para buscar productos por código o nombre.
def buscar_producto(productos):
    busqueda = input("Buscar por código o nombre: ")
    for producto in productos:
        if producto.codigo == busqueda or busqueda in producto.nombre:
            print("Nombre:", producto.nombre)
            print("Código:", producto.codigo)
            print("Precio:", producto.precio)
            print("Proveedor:", producto.proveedor)
            print("Existencia:", producto.existencia)
            print("Estado:", producto.estado)
            print("Descuento:", producto.descuento)

# Función para modificar los datos de un producto.
def modificar_producto(productos):
    codigo = input("Ingrese el código del producto a modificar: ")
    for producto in productos:
        if producto.codigo == codigo:
            producto.nombre = input("Nuevo nombre: ")
            producto.precio = float(input("Nuevo precio: "))
            producto.proveedor = input("Nuevo proveedor: ")
            producto.existencia = int(input("Nueva existencia: "))
            producto.estado = input("Nuevo estado (A/R): ")
            producto.descuento = float(input("Nuevo descuento: "))
            crear_archivo(productos)
            print("Producto modificado con éxito.")
            return
    print("Producto no encontrado.")

def main():
    productos = leer_archivo()
    
    while True:
        print("Menú:\n1. Agregar producto\n2. Buscar producto\n3. Modificar producto\n4. Salir")
        opcion = int(input())
        
        if opcion == 1:
            agregar_producto(productos)
        elif opcion == 2:
            buscar_producto(productos)
        elif opcion == 3:
            modificar_producto(productos)
        elif opcion == 4:
            crear_archivo(productos)
            return
        else:
            print("Opción inválida.")

if __name__ == "__main__":
    main()


```