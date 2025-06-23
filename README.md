# Evaluacion-n-3
# Sistema de Generación de Turnos Virtuales para Atención de Clientes

## Breve descripcion del sistema
Este sistema de gestión de turnos virtuales permite simular el proceso de atención a clientes mediante la asignación automática de números. A través de una interfaz por consola, los usuarios pueden solicitar un turno, visualizar los turnos pendientes, atender al siguiente cliente, reimprimir un turno ya emitido y consultar el historial completo de atenciones.

El sistema integra patrones de diseño como Prototype, Singleton, Adapter e Iterator para estructurar el código de forma limpia y eficiente.

# Patrones de diseño aplicados al sistema.

## Clase Turno patron aplicado Prototype (creacional)

### ¿por que se uso?
todos los turnos tienen una estructura base común: número, nombre del cliente y hora. En lugar de crear manualmente un nuevo objeto desde cero cada vez, se clona una plantilla de turno, y luego se personaliza con los datos del cliente.
### ¿Como se uso en el sistema?
La clase Turno implementa Cloneable y sobrescribe el método clone()
Dentro de GestorTurnos, se crea una plantilla con new Turno("", 0, "")
Luego se clona con Turno nuevo = plantilla.clone(); y se personaliza.

![Image](https://github.com/user-attachments/assets/0c0e4e8f-c6bc-4df6-ba1b-767733c69cbc)

## Clase GestorTurnos (creacional)
### ¿Por que se uso?
En este sistema de turnos, solo debe haber un único gestor que administre todos los turnos pendientes e históricos.

Si existieran múltiples instancias de GestorTurnos, se podrían generar inconsistencias.
como por ejemplo.
Dos turnos con el mismo número.

Pérdida del orden en la cola de espera.

Historiales divididos entre instancias.

### ¿Como se uso?
Constructor privado evita que otros puedan crear instancias desde fuera
getInstancia() asegura que solo se crea una instancia, la primera vez que se llama
A partir de ahí, siempre se reutiliza la misma instancia

![Image](https://github.com/user-attachments/assets/cfdda639-bd3b-4e8e-8ff2-9102cb1c9a59)

### ¿Donde se usa?
se accede desde cualquier parte desde, GestorTurnos gestor = GestorTurnos.getInstancia();

## Clase TurnoIterator Patron aplicado Iterator (comportamiento )

### ¿Por que se uso?
El sistema maneja una cola de turnos pendientes, y es necesario recorrerla para visualizar cada uno sin alterar el orden de atención ni modificar la colección original.

### ¿Como se uso?
Se creó la clase TurnoIterator que implementa  Iterator<Turno>

![Image](https://github.com/user-attachments/assets/73c8a3fe-a5f6-4133-a790-bebd840b0445)

### ¿Donde se uso?
se uso en metodo mostrarPendientes, permite mostrar todos los turnos en espera uno por uno , sin saber cómo están almacenados internamente.

![Image](https://github.com/user-attachments/assets/27860af7-f1ca-4452-9df4-413af6543ae1)




























