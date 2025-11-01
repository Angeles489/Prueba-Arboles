# 🌳 Binary Search Tree (BST) - Implementación en C++

Este proyecto implementa desde cero una estructura de datos **Árbol Binario de Búsqueda (Binary Search Tree - BST)** en **C++**, aplicando los conceptos fundamentales de estructuras dinámicas enlazadas, recursividad y operaciones CRUD.

---

## 🧠 Objetivo

El objetivo del proyecto es diseñar, implementar y probar un **BST** utilizando **programación orientada a objetos (OOP)** y **nodos enlazados dinámicamente**, cumpliendo con los siguientes requisitos:

### 🧩 Características solicitadas

### Clase `Node`
Atributos:
- `int key`
- `Node* left`
- `Node* right`

Constructor:
- Inicializa la clave y los punteros en `nullptr`.

### Clase `BinarySearchTree`
Debe incluir los siguientes métodos:
| Método | Descripción |
|---------|--------------|
| `BinarySearchTree()` | Constructor: inicializa el árbol vacío (`root = nullptr`). |
| `bool insert(int key)` | Inserta una nueva clave respetando la propiedad del BST. |
| `bool search(int key)` | Busca una clave y devuelve si existe o no. |
| `void removeNode(int key)` | Elimina una clave del árbol (considerando los 3 casos: hoja, un hijo o dos hijos). |
| `void inorder()` | Recorre el árbol en orden (izquierda → raíz → derecha). |
| `void preorder()` | Recorre el árbol en preorden (raíz → izquierda → derecha). |
| `void postorder()` | Recorre el árbol en postorden (izquierda → derecha → raíz). |
| `void display()` | Muestra visualmente (de forma simple) la estructura del árbol. |

---

## 🏗️ Estructura del Proyecto

---

## ⚙️ Descripción de los Métodos Principales

### 🔹 `insert(int value)`
Inserta un nuevo nodo en el árbol de forma ordenada:
- Si el árbol está vacío, el nodo se convierte en la raíz.
- Si el valor ya existe, no se inserta (evita duplicados).
- Inserta recursivamente en el subárbol izquierdo o derecho según corresponda.

### 🔹 `search(int value)`
Busca un valor de manera recursiva:
- Retorna `true` si encuentra el valor.
- Retorna `false` si no existe en el árbol.

### 🔹 `removeNode(int value)`
Elimina un nodo del árbol, manejando los tres casos clásicos:
1. **Nodo hoja:** se elimina directamente.  
2. **Nodo con un hijo:** se reemplaza por su hijo.  
3. **Nodo con dos hijos:** se sustituye por el valor mínimo del subárbol derecho (sucesor inorder).

### 🔹 `inorder()`, `preorder()`, `postorder()`
Recorridos recursivos del árbol:
- **Inorder:** imprime los valores ordenados de menor a mayor.
- **Preorder:** imprime primero la raíz, luego los subárboles.
- **Postorder:** imprime primero los hijos, luego la raíz.

### 🔹 `display()`
Muestra visualmente la estructura jerárquica del árbol en consola, con un formato amigable como:



---

## 💻 Ejemplo de uso (`main.cpp`)

```cpp
#include <iostream>
#include "../include/BinarySearchTree.h"
using namespace std;

int main() {
    BinarySearchTree* bst = new BinarySearchTree();

    // Inserción
    bst->insert(8);
    bst->insert(3);
    bst->insert(10);
    bst->insert(1);
    bst->insert(6);
    bst->insert(14);
    bst->insert(4);
    bst->insert(7);
    bst->insert(13);

    cout << "\n=== DISPLAY DEL ÁRBOL ===\n";
    bst->display();

    cout << "\n=== RECORRIDOS ===\n";
    cout << "Inorder: "; bst->inorder(); cout << endl;
    cout << "Preorder: "; bst->preorder(); cout << endl;
    cout << "Postorder: "; bst->postorder(); cout << endl;

    cout << "\n=== BUSQUEDA ===\n";
    cout << "Buscar 6: " << (bst->search(6) ? "Encontrado" : "No encontrado") << endl;
    cout << "Buscar 15: " << (bst->search(15) ? "Encontrado" : "No encontrado") << endl;

    cout << "\n=== ELIMINACIONES ===\n";
    bst->removeNode(1);   // hoja
    bst->removeNode(6);   // dos hijos
    bst->removeNode(10);  // un hijo

    cout << "\nÁrbol después de eliminar 1, 6 y 10:\n";
    bst->display();

    delete bst;
    return 0;
}

=== DISPLAY DEL ÁRBOL ===
└──8
    ├──3
    │   ├──1
    │   └──6
    │       ├──4
    │       └──7
    └──10
        └──14
            └──13

=== RECORRIDOS ===
Inorder: 1 3 4 6 7 8 10 13 14
Preorder: 8 3 1 6 4 7 10 14 13
Postorder: 1 4 7 6 3 13 14 10 8

=== BUSQUEDA ===
Buscar 6: Encontrado
Buscar 15: No encontrado

=== ELIMINACIONES ===
Árbol después de eliminar 1, 6 y 10:
└──8
    ├──3
    │   └──4
    └──14
        └──13




