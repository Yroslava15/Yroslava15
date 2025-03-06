
#include <iostream>
#include <limits> // Для перевірки правильності введених даних

using namespace std;

// Функція для отримання коректного цілого числа
int getValidatedInput(const string& prompt) {
    int num;
    while (true) {
        cout << prompt;
        cin >> num;

        if (cin.fail()) {
            cin.clear(); // Очистити флаг помилки
            cin.ignore(numeric_limits<streamsize>::max(), '\n'); // Очистити вхідний буфер
            cout << "Помилка! Будь ласка, введіть ціле число.\n";
        } else {
            return num;
        }
    }
}

// Функція для виведення всіх парних чисел в діапазоні, що діляться на 3
void printEvenNumbersDivisibleBy3(int N1, int N2) {
    cout << "Парні числа в діапазоні [" << N1 << ", " << N2 << "] що діляться на 3:\n";
    
    bool found = false;
    for (int i = N1; i <= N2; i++) {
        if (i % 2 == 0 && i % 3 == 0) {
            cout << i << " ";
            found = true;
        }
    }

    if (!found) {
        cout << "Немає таких чисел.";
    }
    cout << endl;
}

int main() {
    cout << "Програма знаходження парних чисел у діапазоні, що діляться на 3.\n";

    // Отримуємо два числа від користувача
    int N1 = getValidatedInput("Введіть початок діапазону (N1): ");
    int N2 = getValidatedInput("Введіть кінець діапазону (N2): ");

    // Переконуємось, що N1 <= N2 (міняємо місцями, якщо потрібно)
    if (N1 > N2) {
        swap(N1, N2);
    }

    // Викликаємо функцію для обчислення та виводу результату
    printEvenNumbersDivisibleBy3(N1, N2);

    return 0;
}

СИНОК, [06.03.2025 12:20]
#include <iostream>
#include <limits>  // Для перевірки правильності введених даних
#include <cmath>   // Для математичних обчислень

using namespace std;

// Функція для отримання коректного цілого числа N (> 0)
int getValidatedPositiveInt(const string& prompt) {
    int num;
    while (true) {
        cout << prompt;
        cin >> num;

        if (cin.fail() || num <= 0) {
            cin.clear();  // Очистити флаг помилки
            cin.ignore(numeric_limits<streamsize>::max(), '\n');  // Очистити вхідний буфер
            cout << "Помилка! Будь ласка, введіть ціле число більше 0.\n";
        } else {
            return num;
        }
    }
}

// Функція для отримання коректного дійсного числа ε (> 0)
double getValidatedPositiveDouble(const string& prompt) {
    double num;
    while (true) {
        cout << prompt;
        cin >> num;

        if (cin.fail() || num <= 0) {
            cin.clear();
            cin.ignore(numeric_limits<streamsize>::max(), '\n');
            cout << "Помилка! Будь ласка, введіть дійсне число більше 0.\n";
        } else {
            return num;
        }
    }
}

// Функція для обчислення суми ряду з точністю ε
double calculateSeriesSum(int N, double epsilon) {
    double sum = 0.0;
    double term;  // Поточний член ряду

    for (int i = 1; i <= N; i++) {
        term = 1.0 / (i * i);  // Обчислення поточного члена ряду

        if (term < epsilon) {  // Якщо член ряду менший за ε – зупиняємо обчислення
            break;
        }

        sum += term;  // Додаємо член до суми
    }

    return sum;
}

int main() {
    cout << "Програма для обчислення суми ряду 1 + 1/2^2 + ... + 1/N^2 з точністю ε.\n";

    // Отримуємо вхідні дані від користувача
    int N = getValidatedPositiveInt("Введіть ціле число N (> 0): ");
    double epsilon = getValidatedPositiveDouble("Введіть дійсне число ε (> 0): ");

    // Обчислюємо суму ряду
    double result = calculateSeriesSum(N, epsilon);

    // Виводимо результат
    cout << "Наближене значення суми ряду: " << result << endl;

    return 0;
}
