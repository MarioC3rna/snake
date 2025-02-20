🐍 Snake Game: Array vs Cola (Queue)
Este repositorio contiene dos implementaciones del clásico juego de la serpiente (Snake Game) en JavaScript. Una versión utiliza un array para manejar la serpiente, mientras que la otra utiliza una cola (Queue). A continuación, se describen las diferencias clave entre ambas implementaciones.

🎯 Diferencias principales
1. Estructura de datos
Característica	Array	Cola (Queue)
Representación	Array de objetos {x, y}.	Cola implementada con una clase.
Manipulación	Métodos nativos (pop(), unshift()).	Métodos personalizados (enqueue(), dequeue()).
Encapsulación	No encapsula la lógica.	Encapsula la lógica en una clase.
Acceso a los datos	Directo (índices del array).	A través de métodos (getItems()).
2. Funcionamiento
Array:

La serpiente se maneja como un array.

Se elimina el último segmento con pop() y se añade la nueva cabeza con unshift().

La detección de colisiones se realiza directamente sobre el array.

Cola (Queue):

La serpiente se maneja como una cola.

Se elimina el primer segmento con dequeue() y se añade la nueva cabeza con enqueue().

La detección de colisiones se realiza sobre una copia del array interno.
