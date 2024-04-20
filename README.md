#include <iostream>

// Función para ordenar el arreglo en orden ascendente
void insertionSortAsc(int arr[], int n) {
    int i, key, j;
    for (i = 1; i < n; i++) {
        key = arr[i];
        j = i - 1;

        /* Mueve los elementos de arr[0..i-1], que son mayores que la llave,
           a una posición adelante de su posición actual */
        while (j >= 0 && arr[j] > key) {
            arr[j + 1] = arr[j];
            j = j - 1;
        }
        arr[j + 1] = key;
    }
}

// Función para ordenar el arreglo en orden descendente
void insertionSortDesc(int arr[], int n) {
    int i, key, j;
    for (i = 1; i < n; i++) {
        key = arr[i];
        j = i - 1;

        /* Mueve los elementos de arr[0..i-1], que son menores que la llave,
           a una posición adelante de su posición actual */
        while (j >= 0 && arr[j] < key) {
            arr[j + 1] = arr[j];
            j = j - 1;
        }
        arr[j + 1] = key;
    }
}

// Función para imprimir el arreglo
void printArray(int arr[], int size) {
    for (int i = 0; i < size; i++)
        std::cout << arr[i] << " ";
    std::cout << std::endl;
}

int main() {
    int arr[10];
    int n = sizeof(arr) / sizeof(arr[0]);

    std::cout << "Ingrese 10 valores enteros separados por espacio: ";
    for (int i = 0; i < n; i++) {
        std::cin >> arr[i];
    }

    char order;
    std::cout << "¿Ordenar en orden ascendente (A) o descendente (D)? ";
    std::cin >> order;

    if (order == 'A' || order == 'a') {
        insertionSortAsc(arr, n);
        std::cout << "Arreglo ordenado en orden ascendente: ";
    } else if (order == 'D' || order == 'd') {
        insertionSortDesc(arr, n);
        std::cout << "Arreglo ordenado en orden descendente: ";
    } else {
        std::cout << "Opción no válida." << std::endl;
        return 1;
    }

    printArray(arr, n);

    return 0;
}
