# Prueba-Arboles
# 🌳 Binary Search Tree (BST) Implementation in C++

Este proyecto implementa desde cero una estructura de datos **Árbol Binario de Búsqueda (Binary Search Tree)** en C++, aplicando los principios de:
- Nodos enlazados dinámicamente
- Inserción y búsqueda ordenada
- Recorridos del árbol (inorden, preorden, postorden)
- Operaciones CRUD: Crear, Leer, Actualizar (mediante reemplazo de nodo), y Eliminar
- Visualización del árbol en consola

---

## 🧠 Descripción General

Un **árbol binario de búsqueda (BST)** es una estructura de datos jerárquica donde:
- Cada nodo tiene **un valor** y **dos hijos** (izquierdo y derecho).
- Los valores del **subárbol izquierdo** son **menores** que la raíz.
- Los valores del **subárbol derecho** son **mayores** que la raíz.

Esto permite realizar operaciones de búsqueda, inserción y eliminación en tiempo promedio **O(log n)**.

---

## 🏗️ Estructura del Proyecto


---

## ⚙️ Implementación

### 🔹 Clase `BinarySearchTree`
Contiene toda la lógica del árbol binario, incluyendo un `struct Node` interno.

#### **Atributos principales**
| Atributo | Descripción |
|-----------|--------------|
| `Node* root` | Puntero al nodo raíz del árbol |

#### **Métodos públicos**
| Método | Descripción |
|---------|--------------|
| `BinarySearchTree()` | Constructor: inicializa el árbol vacío |
| `bool insert(int value)` | Inserta un nuevo valor en el árbol |
| `bool search(int value)` | Busca un valor y devuelve `true` o `false` |
| `bool remove(int value)` | Elimina un nodo según su valor |
| `void display()` | Muestra la estructura del árbol en consola |

#### **Métodos privados auxiliares**
| Método | Descripción |
|---------|--------------|
| `Node* remove(Node* current, int value)` | Implementa la eliminación recursiva (3 casos) |
| `Node* findMin(Node* node)` | Encuentra el nodo con el menor valor (sucesor inorder) |
| `void display(Node* node, int space)` | Imprime el árbol en formato visual sideways |

---

## 🔍 Casos de eliminación manejados

1. **Nodo hoja (sin hijos):** se elimina directamente.  
2. **Nodo con un hijo:** se conecta el padre con el hijo, “saltando” el nodo.  
3. **Nodo con dos hijos:** se reemplaza por el **sucesor inorder** (menor del subárbol derecho).

---

## 💻 Ejemplo de uso (`main.cpp`)

```cpp
#include "include/BinarySearchTree.h"
#include <iostream>
using namespace std;

int main() {
    BinarySearchTree bst;

    // Inserción
    bst.insert(50);
    bst.insert(30);
    bst.insert(70);
    bst.insert(20);
    bst.insert(40);
    bst.insert(60);
    bst.insert(80);

    cout << "Árbol inicial:\n";
    bst.display();

    // Eliminación de diferentes casos
    cout << "\nEliminar nodo hoja (20):\n";
    bst.remove(20);
    bst.display();

    cout << "\nEliminar nodo con un hijo (30):\n";
    bst.remove(30);
    bst.display();

    cout << "\nEliminar nodo con dos hijos (50):\n";
    bst.remove(50);
    bst.display();

    return 0;
}

Árbol inicial:
          80
     70
          60
50
          40
     30
          20

Eliminar nodo hoja (20):
          80
     70
          60
50
          40
     30

Eliminar nodo con un hijo (30):
          80
     70
          60
50
          40

Eliminar nodo con dos hijos (50):
          80
     70
          60
40

