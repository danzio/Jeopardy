# Jeopardy
A somewhat C++ minicalc for sport-version 'Jeopardy' game.


//Данное консольное приложение создано для более комфортного подсчёта баллов СИ.
//Created by FDelta, 2016


#include <stdafx.h>
#include <stdio.h>
#include <iostream>
#include <locale>
#include <windows.h>
using namespace std;




int _tmain(int argc, _TCHAR* argv[])
{
	setlocale(LC_ALL, "Russian");
	SetConsoleOutputCP(1251);
	SetConsoleCP(1251);
	char ch;
	string an[4], theme[10];
	int a[4], x, r = 1, y, u = 0, u1 = 0, k=0;
	cout << "Количество играющихся тем: ";
	cin >> y;
	cout << "Сегодня играют:\n";
	do
	{
		cout<<(k+1); cout<<". ";
cin >>an[k];
		k++;
	} while (k<= 3);
	cout << "Ваши темы:\n";
	do
	{
cout<<(u+1); cout<<". ";
		cin >> theme[u];
		u++;
	} while (u <= y - 1);

	if (y != 0) do												//задаём условие начала цикла {тема}
	{
		int p = 10;												//задаём начальное значение цены вопроса
		u1 = r - 1;
		cout << "Тема "; cout << r; cout << ": "; cout << theme[u1]; cout << ".\n";
		do														//задаём начало цикла {вопрос}
		{
			cout << "Цена вопроса: "; cout << p; cout << "\n";
			cout << "Отвечает игрок ";							//выбор игрока
			cin >> x;
			if (x>=1 && x<=4)
				{
					cout << "Ответ верный? (Y/N) ";				//проверка правильности
					cin >> ch;
x--;
					if (ch == 'y' || '+')
					{
						//если верно
						a[x] += p;									//прибавляем цену вопроса
						cout << "+"; cout << p; cout << "\n\n";	//выводим совершенное действие
						p += 10;								//переходим к следующему вопросу - увеличиваем цену
					}
					else if ('n' || '-')									//если неверно
					{
						a[x] -= p;									//вычитаем цену вопроса
						cout << "-"; cout << p; cout << "\n\n";	//выводим совершенное действие
					}
					else break;									//откат к выбору игрока
				}
				else
{										//если никто не ответил
				cout << "Ответ не дан\n\n";					//выводим, что нет ответа
				p += 10;										//увеличиваем цену вопроса - переходим к следующему
}
				break;
			}
		} while (p <= 50);											//условие цикла {вопрос} - пока цена вопроса не превысит 50 (тема закончена)
		cout << "После "; cout << r; cout << "-й темы:\n\n";
int n=0;
do
{
cout << an[n]; cout << ": "; cout << a[n]; cout << "\n\n";
n++;
}
while (n<=3);
										//объявляем конец темы и выводим результат после темы
		++r;													//переходим к следующей теме
	} while (r <= y);												//условие цикла {тема} - пока не превысит заданного количества
	system("pause");
	return 0;
}
