#include <iostream>
#include <limits>
#include <cmath>

using namespace std;

// Функція для отримання коректного введення цілого числа > 0
int getValidatedPositiveInt(const string& prompt) {
    int number;
    while (true) {
        cout << prompt;
        cin >> number;
        
        if (cin.fail() || number <= 0) {
            cin.clear();
            cin.ignore(numeric_limits<streamsize>::max(), '\n');
            cout << "Помилка: введено некоректне значення. Введіть ціле число більше за 0." << endl;
        } else {
            return number;
        }
    }
}

// Функція для отримання коректного введення дійсного числа > 0
double getValidatedPositiveDouble(const string& prompt) {
    double number;
    while (true) {
        cout << prompt;
        cin >> number;
        
        if (cin.fail() || number <= 0) {
            cin.clear();
            cin.ignore(numeric_limits<streamsize>::max(), '\n');
            cout << "Помилка: введено некоректне значення. Введіть дійсне число більше за 0." << endl;
        } else {
            return number;
        }
    }
}

// Функція для обчислення суми ряду
double calculateSum(int N, double epsilon) {
    double sum = 0.0;
    for (int i = 1; i <= N; ++i) {
        double term = 1.0 / (i * i);
        if (term < epsilon) {
            break;
        }
        sum += term;
    }
    return sum;
}

int main() {
    // Запускаємо програму для трьох наборів даних
    for (int i = 0; i < 3; ++i) {
        int N = getValidatedPositiveInt("Введіть ціле число N (> 0): ");
        double epsilon = getValidatedPositiveDouble("Введіть дійсне число ε (> 0): ");
        
        double result = calculateSum(N, epsilon);
        cout << "Наближене значення суми ряду: " << result << endl;
        cout << "-----------------------------" << endl;
    }
    
    return 0;
}
