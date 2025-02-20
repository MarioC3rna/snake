# 🐍 Snake Game: Array vs Cola (Queue)

Este repositorio contiene dos implementaciones del clásico juego de la serpiente (Snake Game) en JavaScript.
Una versión utiliza un **array** para manejar la serpiente, mientras que la otra utiliza una **cola (Queue)**.  
A continuación, se describen las diferencias clave entre ambas implementaciones.

---

## 🎯 Diferencias principales

### 1. 📌 Estructura de datos

| Característica   | Array                        | Cola (Queue)                      |
|-----------------|-----------------------------|-----------------------------------|
| **Representación** | Array de objetos `{x, y}`.  | Cola implementada con una clase. |
| **Manipulación** | Métodos nativos (`pop()`, `unshift()`). | Métodos personalizados (`enqueue()`, `dequeue()`). |
| **Encapsulación** | No encapsula la lógica. | Encapsula la lógica en una clase. |
| **Acceso a los datos** | Directo (índices del array). | A través de métodos (`getItems()`). |

---

### 2. ⚙️ Funcionamiento

#### 🟢 **Array**
- La serpiente se maneja como un **array**.
- Se elimina el último segmento con `pop()` y se añade la nueva cabeza con `unshift()`.
- La detección de colisiones se realiza directamente sobre el array.

---

#### 🔵 **Cola (Queue)**
- La serpiente se maneja como una **cola**.
- Se elimina el primer segmento con `dequeue()` y se añade la nueva cabeza con `enqueue()`.
- La detección de colisiones se realiza sobre una copia del array interno.

---

## 📌 Comparación de eficiencia

| Funcionamiento     | Array | Cola (Queue) |
|--------------------|-----------------------------|---------------------------------|
| **Movimiento** | `unshift(newHead)` para agregar la nueva cabeza y `pop()` para eliminar la cola. | `enqueue(newHead)` para agregar la nueva cabeza y `dequeue()` para eliminar la cola. |
| **Acceso a los elementos** | Se accede a los segmentos de la serpiente con índices (`snake[i]`). | Se accede a los segmentos con `getItems()`. |
| **Encapsulación** | La serpiente es un simple array, con toda la lógica en la misma función. | La serpiente es una instancia de `Queue`, encapsulando su lógica. |
| **Eficiencia** | `unshift()` es menos eficiente porque reordena el array. | `enqueue()` y `dequeue()` son más eficientes en una estructura de cola. |

---

## 🎯 **Conclusión**
- La implementación con **array** es más simple y directa, pero menos eficiente.
- La implementación con **cola (Queue)** encapsula mejor la estructura de datos y separa responsabilidades, haciendo el código más organizado y escalable.
- Si se quiere mejorar la eficiencia y la mantenibilidad del código, la implementación con `Queue` es la mejor opción. 🚀

