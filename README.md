# Домашнее задание к работе 16
Кирилл Донцов, бИЦ-251
## Условие задачи 
Массив d,каждый элемент которого определяется по правилу d=max (a,b,c), в случае исчерпания элементов в одном из массивов , опять используются его элементы , начиная с 0.
## 1. Реализация программы 
# Код программы 
```c
#include <stdio.h>
#include <stdlib.h>
#include <time.h>

// Функция для создания массива со случайными числами
double* generate_array(int size) {
    double* arr = (double*)malloc(size * sizeof(double));
    for (int i = 0; i < size; i++) {
        arr[i] = (rand() % 200 - 100) / 10.0; // числа от -10.0 до 10.0
    }
    return arr;
}

// Функция для вывода массива
void print_array(double* arr, int size, char name) {
    printf("Массив %c[%d]: ", name, size);
    for (int i = 0; i < size; i++) {
        printf("%.1f ", arr[i]);
    }
    printf("\n");
}

// Функция для задания 6
double* create_array_d(double* a, int size_a, double* b, int size_b, double* c, int size_c, int* size_d) {
    int max_size = (size_a > size_b) ? ((size_a > size_c) ? size_a : size_c) : ((size_b > size_c) ? size_b : size_c);
    *size_d = max_size;
    
    double* d = (double*)malloc(max_size * sizeof(double));
    
    for (int i = 0; i < max_size; i++) {
        double a_val = a[i % size_a];
        double b_val = b[i % size_b];
        double c_val = c[i % size_c];
        
        // Находим максимальное значение
        double max_val = a_val;
        if (b_val > max_val) max_val = b_val;
        if (c_val > max_val) max_val = c_val;
        
        d[i] = max_val;
    }
    
    return d;
}

int main() {
    srand(time(NULL));
    
    // Генерируем случайные размеры массивов от 10 до 50
    int size_a = rand() % 41 + 10;
    int size_b = rand() % 41 + 10;
    int size_c = rand() % 41 + 10;
    
    // Создаем массивы
    double* a = generate_array(size_a);
    double* b = generate_array(size_b);
    double* c = generate_array(size_c);
    
    // Выводим исходные массивы
    printf("Исходные массивы:\n");
    print_array(a, size_a, 'a');
    print_array(b, size_b, 'b');
    print_array(c, size_c, 'c');
    
    // Создаем массив d по правилу задания 6
    int size_d;
    double* d = create_array_d(a, size_a, b, size_b, c, size_c, &size_d);
    
    // Выводим результирующий массив
    printf("\nРезультирующий массив d (максимумы a[i], b[i], c[i]):\n");
    print_array(d, size_d, 'd');
    
    // Освобождаем память
    free(a);
    free(b);
    free(c);
    free(d);
    
    return 0;
}
#include <stdio.h>
#include <stdlib.h>
#include <time.h>

// Функция для создания массива со случайными числами
double* generate_array(int size) {
    double* arr = (double*)malloc(size * sizeof(double));
    for (int i = 0; i < size; i++) {
        arr[i] = (rand() % 200 - 100) / 10.0; // числа от -10.0 до 10.0
    }
    return arr;
}

// Функция для вывода массива
void print_array(double* arr, int size, char name) {
    printf("Массив %c[%d]: ", name, size);
    for (int i = 0; i < size; i++) {
        printf("%.1f ", arr[i]);
    }
    printf("\n");
}

// Функция для задания 6
double* create_array_d(double* a, int size_a, double* b, int size_b, double* c, int size_c, int* size_d) {
    int max_size = (size_a > size_b) ? ((size_a > size_c) ? size_a : size_c) : ((size_b > size_c) ? size_b : size_c);
    *size_d = max_size;
    
    double* d = (double*)malloc(max_size * sizeof(double));
    
    for (int i = 0; i < max_size; i++) {
        double a_val = a[i % size_a];
        double b_val = b[i % size_b];
        double c_val = c[i % size_c];
        
        // Находим максимальное значение
        double max_val = a_val;
        if (b_val > max_val) max_val = b_val;
        if (c_val > max_val) max_val = c_val;
        
        d[i] = max_val;
    }
    
    return d;
}

int main() {
    srand(time(NULL));
    
    // Генерируем случайные размеры массивов от 10 до 50
    int size_a = rand() % 41 + 10;
    int size_b = rand() % 41 + 10;
    int size_c = rand() % 41 + 10;
    
    // Создаем массивы
    double* a = generate_array(size_a);
    double* b = generate_array(size_b);
    double* c = generate_array(size_c);
    
    // Выводим исходные массивы
    printf("Исходные массивы:\n");
    print_array(a, size_a, 'a');
    print_array(b, size_b, 'b');
    print_array(c, size_c, 'c');
    
    // Создаем массив d по правилу задания 6
    int size_d;
    double* d = create_array_d(a, size_a, b, size_b, c, size_c, &size_d);
    
    // Выводим результирующий массив
    printf("\nРезультирующий массив d (максимумы a[i], b[i], c[i]):\n");
    print_array(d, size_d, 'd');
    
    // Освобождаем память
    free(a);
    free(b);
    free(c);
    free(d);
    
    return 0;
}


