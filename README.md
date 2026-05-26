# cpp-vector-lesson
#include <iostream>
#include <vector>
#include <string>

using namespace std;

struct Question {
    string text;
    vector<string> options;
    char correctAnswer;
};

int main() {
    // Налаштування кодування для української мови в консолі
    setlocale(LC_ALL, "Ukrainian");

    vector<Question> quiz = {
        {
            "1. Яке початкове значення місткості (capacity) встановлюється в конструкторі класу Vector?",
            {"А) 0", "Б) 1", "В) 2", "Г) 10"},
            'В'
        },
        {
            "2. Що відбувається з виділеною пам'яттю, коли викликається метод pop_back()?",
            {"А) Пам'ять під останній елемент одразу звільняється через delete", 
             "Б) Зменшується лише значення length, фізично пам'ять не змінюється", 
             "В) Місткість масиву автоматично зменшується вдвічі", 
             "Г) Відбувається повне очищення масиву"},
            'Б'
        },
        {
            "3. За якої умови всередині методу push_back() викликається метод resize()?",
            {"А) Коли масив порожній (length == 0)", 
             "Б) Коли кількість елементів досягла місткості (length >= capacity)", 
             "В) Після кожного третього виклику push_back()", 
             "Г) Коли індекс перевищує максимальне значення"},
            'Б'
        }
    };

    int score = 0;
    char userAnswer;

    cout << "=== ІНТЕРАКТИВНИЙ ТЕСТ: CLASS VECTOR ===" << endl << endl;

    for (size_t i = 0; i < quiz.size(); i++) {
        cout << quiz[i].text << endl;
        for (const string& option : quiz[i].options) {
            cout << "  " << option << endl;
        }
        
        cout << "Ваша відповідь (введіть велику літеру А, Б, В або Г): ";
        cin >> userAnswer;
        
        // Проста валідація введення літери в іншому регістрі
        if (userAnswer == 'в') userAnswer = 'В';
        if (userAnswer == 'б') userAnswer = 'Б';
        if (userAnswer == 'а') userAnswer = 'А';
        if (userAnswer == 'г') userAnswer = 'Г';

        if (userAnswer == quiz[i].correctAnswer) {
            cout << "🟢 Правильно!" << endl << endl;
            score++;
        } else {
            cout << "🔴 Неправильно. Правильна відповідь: " << quiz[i].correctAnswer << endl << endl;
        }
    }

    cout << "========================================" << endl;
    cout << "Тест завершено! Ваш результат: " << score << " з " << quiz.size() << " балів." << endl;

    return 0;
}
