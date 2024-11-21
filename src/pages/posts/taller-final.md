---
layout: ../../layouts/PostLayout.astro
title: 'TIA 2 - Taller Final: Elaboración de un algoritmo en C++'
pubDate: 2024-11-18
description: 'El objetivo es elaborar un algoritmo que permita a un restaurante evaluar ciertos aspectos de su servicio mediante la calificación de sus clientes.'
author: 'Angie'
image:
  url: 'https://i.pinimg.com/564x/bf/01/62/bf01625ddbe3063bc3e60c72e77e11e7.jpg'
  alt: 'Ilustración de una función en programación'
---

### Enunciado

El dueño de un restaurante entrevista a cinco clientes y les pide calificar del 1 al 10 los siguientes aspectos:

1. Atención de parte de los empleados
2. Calidad de la comida
3. Justicia del precio
4. Ambiente (muebles cómodos, música adecuada, iluminación, decoración, etc.)

El algoritmo debe:

* Pedir las calificaciones para cada uno de estos aspectos
* Almacenar esta información
* Calcular el promedio para cada aspecto
* Imprimir los resultados ordenados del aspecto mejor calificado al peor calificado.

----

## Solución en c++

Aquí está la implementación del algoritmo en c++:

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    double atencionTotal = 0, calidadTotal = 0, precioTotal = 0, ambienteTotal = 0;
    double atencion, calidad, precio, ambiente;
    int clienteCount = 0;
    char continuar;

    cout << "Ingrese calificaciones para cada cliente. Al finalizar cada cliente, se le preguntará si desea continuar.\n";

    do {
        cout << "Cliente " << (clienteCount + 1) << ":\n";

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

        clienteCount++;

        cout << "¿Desea ingresar calificaciones para otro cliente? (s/n): ";
        cin >> continuar;
        cout << endl;

    } while (continuar == 's' || continuar == 'S' && clienteCount <= 5);

    if (clienteCount == 0) {
        cout << "No se ingresaron datos.\n";
        return 0;
    }

    double promedioAtencion = atencionTotal / clienteCount;
    double promedioCalidad = calidadTotal / clienteCount;
    double promedioPrecio = precioTotal / clienteCount;
    double promedioAmbiente = ambienteTotal / clienteCount;

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

----

## Análisis de la solución

1. Estructuras cíclicas:
   El programa utiliza un bucle for para recolectar las calificaciones de los cinco clientes.

2. Estructuras condicionales:
   Se emplean bucles do-while para validar que las calificaciones ingresadas estén dentro del rango permitido (1 a 10).

3. Subprogramas (funcionalidad modular):
   Aunque esta solución no tiene funciones aparte de main, el manejo ordenado de variables y cálculos asegura la
   modularidad en la lógica.

4. Ordenamiento:
   Los promedios se ordenan de forma descendente utilizando un bucle para intercambiar valores y sus etiquetas
   correspondientes con la función swap.

**Resultado esperado**
Después de ejecutar el algoritmo, se mostrará una lista ordenada de los aspectos evaluados, indicando los promedios de
calificación de mejor a peor. Esto ayudará al dueño del restaurante a identificar las áreas que necesita mejorar.
----
