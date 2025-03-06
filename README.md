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
