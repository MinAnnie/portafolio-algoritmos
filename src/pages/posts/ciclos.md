---
layout: ../../layouts/PostLayout.astro
title: 'Utilización de estructuras repetitivas "Ciclos" y subprogramas'
pubDate: 2024-11-16
description: 'Exploración de ciclos y subprogramas en programación con ejemplos en C++'
author: 'Angie'
image:
  url: 'https://img.freepik.com/foto-gratis/vista-superior-flechas-concentricas-rompiendo-circulo_23-2148490520.jpg?t=st=1731944575~exp=1731948175~hmac=fb1506553e0d70b989a6dc83040e5cbcf5801f2d808a0c546bd448814ce8b808&w=1380'
  alt: 'Ilustración de un bucle infinito'
---

Las **estructuras repetitivas**, comúnmente conocidas como "ciclos", y los **subprogramas** son herramientas
fundamentales en la programación que permiten automatizar procesos, simplificar código y mejorar su reutilización. En
este blog veremos cómo implementarlos en **C++**.

### ¿Qué son los ciclos?

Un ciclo es una estructura de control que repite un bloque de instrucciones mientras se cumpla una condición. En C++
existen tres tipos principales de ciclos:

1. **Ciclo `for`:** Se utiliza cuando sabemos cuántas veces queremos repetir una acción.

```cpp
#include <iostream>
   using namespace std;

   int main() {
       for (int i = 0; i < 10; i++) {
           cout << "Iteración: " << i << endl;
       }
       return 0;
   }
```

2. **Ciclo `while`:** Se ejecuta mientras una condición sea verdadera.

```cpp
#include <iostream>
using namespace std;

int main() {
    int i = 0;
    while (i < 10) {
        cout << "Iteración: " << i << endl;
        i++;
    }
    return 0;
}
```

3. **Ciclo `do-while`:** Es similar al `while`, pero este se ejecuta al menos una vez.

```cpp
#include <iostream>
using namespace std;

int main() {
    int i = 0;
    while (i < 10) {
        cout << "Iteración: " << i << endl;
        i++;
    }
    return 0;
}
```

### ¿Que son los subprogramas?

Los subprogramas son bloques de código independientes que realizan una tarea específica y pueden ser llamados desde
cualquier parte del programa. En C++ se dividen en:

* Funciones: Devuelven un valor al programa principal.

```cpp
#include <iostream>
using namespace std;

int suma(int a, int b) {
    return a + b;
}

int main() {
    int resultado = suma(5, 3);
    cout << "La suma es: " << resultado << endl;
    return 0;
}

```

* Procedimientos: No devuelven un valor, solo ejecutan una serie de instrucciones.

```cpp
#include <iostream>
using namespace std;

void imprimirMensaje() {
    cout << "¡Hola, mundo!" << endl;
}

int main() {
    imprimirMensaje();
    return 0;
}
```

### Ventajas de usar ciclos y subprogramas

* Eficiencia: Reducen la cantidad de código duplicado.
* Reutilización: Los subprogramas pueden ser llamados varias veces en diferentes contextos.
* Legibilidad: Dividen el código en bloques más pequeños y manejables.
* Escalabilidad: Facilitan la modificación y el mantenimiento del código.
  Las **estructuras repetitivas**, comúnmente conocidas como "ciclos", y los **subprogramas** son herramientas fundamentales en la programación que permiten automatizar procesos, simplificar código y mejorar su reutilización. En este blog veremos cómo implementarlos en **C++**.

---

### Aplicaciones con estructuras repetitivas

En la unidad 2 del curso de programación, se exploraron diversas aplicaciones prácticas de las estructuras repetitivas, destacando su utilidad en tareas como:

**Cálculo de sumatorias:** Uso de ciclos `for` para calcular la suma de una serie de números, como en el cálculo de promedios o factoriales.
   ```cpp
   #include <iostream>
   using namespace std;

   int main() {
       int suma = 0;
       for (int i = 1; i <= 10; i++) {
           suma += i;
       }
       cout << "La suma de los primeros 10 números es: " << suma << endl;
       return 0;
   }
   ```

### Ejemplo: Calificaciones de un restaurante

Un caso práctico interesante es el de un restaurante que entrevista a sus clientes para calificar aspectos importantes como la atención, la calidad de la comida, la justicia del precio y el ambiente. El objetivo es obtener un promedio de cada aspecto y ordenarlos de mejor a peor calificación.

El siguiente algoritmo utiliza un **centinela** para manejar los datos de múltiples clientes y calcular los resultados:

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    double atencionTotal = 0, calidadTotal = 0, precioTotal = 0, ambienteTotal = 0;

    double atencion, calidad, precio, ambiente;

    for (int i = 1; i <= 5; i++) {
        cout << "Cliente " << i << ":\n";

        do {
            cout << "Califique Atención de los empleados (1-10): ";
            cin >> atencion;
        } while (atencion < 1 || atencion > 10);
        atencionTotal += atencion;

        do {
            cout << "Califique Calidad de la comida (1-10): ";
            cin >> calidad;
        } while (calidad < 1 || calidad > 10);
        calidadTotal += calidad;

        do {
            cout << "Califique Justicia del precio (1-10): ";
            cin >> precio;
        } while (precio < 1 || precio > 10);
        precioTotal += precio;

        do {
            cout << "Califique Ambiente (1-10): ";
            cin >> ambiente;
        } while (ambiente < 1 || ambiente > 10);
        ambienteTotal += ambiente;

        cout << endl;
    }

    double promedioAtencion = atencionTotal / 5;
    double promedioCalidad = calidadTotal / 5;
    double promedioPrecio = precioTotal / 5;
    double promedioAmbiente = ambienteTotal / 5;

    string aspecto1 = "Atención de los empleados";
    string aspecto2 = "Calidad de la comida";
    string aspecto3 = "Justicia del precio";
    string aspecto4 = "Ambiente";

    double promedio1 = promedioAtencion;
    double promedio2 = promedioCalidad;
    double promedio3 = promedioPrecio;
    double promedio4 = promedioAmbiente;

    for (int i = 0; i < 3; i++) {
        if (promedio1 < promedio2) { swap(promedio1, promedio2); swap(aspecto1, aspecto2); }
        if (promedio2 < promedio3) { swap(promedio2, promedio3); swap(aspecto2, aspecto3); }
        if (promedio3 < promedio4) { swap(promedio3, promedio4); swap(aspecto3, aspecto4); }
    }

    cout << "Promedio de calificaciones para cada aspecto, de mejor a peor:\n";
    cout << aspecto1 << ": " << promedio1 << endl;
    cout << aspecto2 << ": " << promedio2 << endl;
    cout << aspecto3 << ": " << promedio3 << endl;
    cout << aspecto4 << ": " << promedio4 << endl;

    return 0;
}
```

### Ejemplo 2: Cálculo de pago a empleados

Este ejemplo utiliza **subprogramas** y **estructuras repetitivas** para calcular cuánto se le paga a un empleado considerando:

- Su salario base.
- Un subsidio adicional por cada hijo.
- Una retención del 10% sobre el total.

El siguiente programa realiza estos cálculos:
```cpp
#include <iostream>
using namespace std;

// Función para calcular el pago total de un empleado
double calcularPago(double salarioBase, int numeroHijos) {
    double subsidioPorHijo = 5000; // Subsidio fijo por hijo
    double retencion = 0.10; // 10% de retención
    double total = salarioBase + (numeroHijos * subsidioPorHijo);
    double totalConRetencion = total - (total * retencion);
    return totalConRetencion;
}

int main() {
    int numeroEmpleados;
    cout << "Ingrese el número de empleados: ";
    cin >> numeroEmpleados;

    for (int i = 0; i < numeroEmpleados; i++) {
        double salarioBase;
        int numeroHijos;

        cout << "\nEmpleado " << i + 1 << ":" << endl;
        cout << "Ingrese el salario base: ";
        cin >> salarioBase;
        cout << "Ingrese el número de hijos: ";
        cin >> numeroHijos;

        double pagoFinal = calcularPago(salarioBase, numeroHijos);
        cout << "El pago total para el empleado es: $" << pagoFinal << endl;
    }

    return 0;
}
```


Estas aplicaciones demuestran cómo las estructuras repetitivas simplifican tareas comunes y las hacen más eficientes.

---

### Conclusión

Las estructuras repetitivas son esenciales en la resolución de problemas en programación, ya que permiten manejar datos de manera estructurada y realizar cálculos de manera eficiente.

### Bibliografía

- Deitel, P., & Deitel, H. (2021). *C++ Cómo programar*. Pearson Educación.
- Stroustrup, B. (2013). *The C++ Programming Language*. Addison-Wesley.
- Material del curso: Unidad 2 - Estructuras de control repetitivas.