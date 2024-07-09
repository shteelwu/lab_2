```c
#include <stdio.h>
#include <locale.h>

int ab(int a, int b) {
    while (b != 0) {
        int temp = b;
        b = a % b;
        a = temp;
    }
    return a;
}

int qb(int a, int b) {
    return (a * b) / ab(a, b);
}

int main() {
    setlocale(LC_ALL, "Ukr");

    int p;
    printf("Enter count of numbers: ");
    scanf("%d", &p);

    if (p < 2 || p > 20) {
        printf("Count of numbers must be between 2 and 20\n");
        return 1;
    }

    int numbers[20];
    printf("Enter numbers: ");
    for (int i = 0; i < p; i++) {
        scanf("%d", &numbers[i]);
    }

    int result = numbers[0];
    for (int i = 1; i < p; i++) {
        result = qb(result, numbers[i]);
    }

    printf("NSD: %d\n", result);
    return 0;
}
