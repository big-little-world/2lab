# 2lab

#include "stdafx.h"
#include <iostream>
using namespace std;
int first, last, n;
/** function Функция "вычисление"*/
void quicksort(int *mas, int first, int last)
{
	int mid, count;
	int f = first, l = last;
	mid = mas[(f + l) / 2]; //вычисление опорного элемента
	do
	{
		while (mas[f]<mid) f++;
		while (mas[l]>mid) l--;
		if (f <= l) //перестановка элементов
		{
			count = mas[f];
			mas[f] = mas[l];
			mas[l] = count;
			f++;
			l--;
		}
	} while (f<l);
	if (first<l) quicksort(mas, first, l);
	if (f<last) quicksort(mas, f, last);
}
//главная функция
/** @function главная функция */
void main()
{
	setlocale(LC_ALL, "Rus");
	cout << "Количество элементов массива\n";
	cin >> n;
	int *A = new int[n];
	for (int i = 0; i<n; i++)
		cin >> A[i];
	cout << "Массив: " << '\n';
	for (int i = 0; i < n; i++)
		cout << A[i] << "\t";

	first = 0; last = n - 1;
	quicksort(A, first, last);
	cout << endl << "массив после преобразования:\n ";
	for (int i = 0; i<n; i++) cout << A[i] << "\t ";
	delete[]A;
	system("pause");
}
