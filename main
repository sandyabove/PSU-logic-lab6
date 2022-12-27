#include <stdio.h>
#include <windows.h>
#include <time.h>

int flag = -1;

void otozhd(int n, int** G)
{
	int t, p;
	printf("Введите вершину 1 для операции отождествления вершин: ");
	scanf_s("%d", &t);
	printf("Введите вершину 2 для операции отождествления вершин: ");
	scanf_s("%d", &p);
	printf("Итоговая матрица смежности:\n");
	for (int i = 0; i != n; i++)
	{
		if ((G[t][p] == 1) && (G[p][t] == 1))
		{
			flag = t;
		}
		if ((G[i][t] == 1) || (G[i][p] == 1))
		{
			G[i][t] = 1;
			G[t][i] = 1;
		}
	}
	for (int i = 0; i != p; i++) {
		for (int k = 0; k < (n - p - 1); k++) {
			G[i][p + k] = G[i][p + k + 1];
			G[p + k][i] = G[p + k + 1][i];
		}
	}
	for (int i = p; i != n - 1; i++) {
		for (int k = 0; k < (n - p - 1); k++) {
			G[i][p + k] = G[i + 1][p + k + 1];
			G[p + k][i] = G[p + k + 1][i + 1];
		}
	}
	for (int i = 0; i < n - 1; i++)
	{
		for (int j = 0; j < n - 1; j++)
		{
			if (i == j)
			{
				G[i][j] = 0;
			}
			if (flag == t)
			{
				G[t][t] = 1;
			}
			printf("%d\t", G[i][j]);
		}
		printf("\n");
	}
}

void styagivanie(int n, int** G)
{
	int v1, v2;
	printf("\nВведите вершину 1 для операции стягивания ребра: ");
	scanf_s("%d", &v1);
	printf("Введите вершину 2 для операции стягивания ребра: ");
	scanf_s("%d", &v2);
	if (G[v1][v2] != 1) return;
	printf("Итоговая матрица смежности:\n");
	for (int i = 0; i != n; i++)
	{
		if ((G[i][v1] == 1) || (G[i][v2] == 1))
		{
			G[i][v1] = 1;
			G[v1][i] = 1;
		}
	}
	for (int i = 0; i != v2; i++) {
		for (int k = 0; k < (n - v2 - 2); k++) {
			G[i][v2 + k] = G[i][v2 + k + 1];
			G[v2 + k][i] = G[v2 + k + 1][i];
		}
	}
	for (int i = v2; i != n - 2; i++) {
		for (int k = 0; k < (n - v2 - 2); k++) {
			G[i][v2 + k] = G[i + 1][v2 + k + 1];
			G[v2 + k][i] = G[v2 + k + 1][i + 1];
		}
	}
	for (int i = 0; i < n - 2; i++)
	{
		for (int j = 0; j < n - 2; j++)
		{
			if (i == j)
			{
				G[i][j] = 0;
			}
			if ((flag == v1) || (flag == v2))
			{
				G[v1][v1] = 1;
			}
			else if (flag > v2) {
				G[flag - 1][flag - 1] = 1;
			}
			else if ((flag != -1) && (flag != v1) && (flag < v2)) {
				G[flag][flag] = 1;
			}
			printf("%d\t", G[i][j]);
		}
		printf("\n");
	}
}

void rashep(int n, int** G)
{
	int s;
	for (int i = 0; i != n - 2; i++)
	{
		if (G[i][i] == 1) flag = i;
	}
	printf("\nВведите вершину для операции расщепления: ");
	scanf_s("%d", &s);
	printf("Итоговая матрица смежности:\n");
	for (int i = 0; i != s + 1; i++) {
		for (int k = 1; k < (n - s - 2); k++) {
			G[i][n - k - 1] = G[i][n - k - 2];
			G[n - k - 1][i] = G[n - k - 2][i];
		}
	}
	for (int i = s + 2; i != n - 2; i++) {
		for (int k = 1; k < (n - s - 2); k++) {
			G[i][n - k - 1] = G[i - 1][n - k - 2];
			G[n - k - 1][i] = G[n - k - 2][i - 1];
		}
	}

	for (int i = 0; i != n - 1; i++)
	{
		G[i][s + 1] = G[i][s];
		G[s + 1][i] = G[i][s + 1];
	}

	for (int i = 0; i != n - 1; i++)
	{
		if (G[i][s] == 1)
		{
			G[s][s + 1] = 1;
			G[s + 1][s] = 1;
		}
	}

	for (int i = 0; i < n - 1; i++)
	{
		for (int j = 0; j < n - 1; j++)
		{
			if (i == j)
			{
				G[i][j] = 0;
			}
			if ((flag <= s) && (flag != -1))
			{
				G[flag][flag] = 1;
			}
			if (flag > s)
			{
				G[flag + 1][flag + 1] = 1;
			}
			printf("%d\t", G[i][j]);
		}
		printf("\n");
	}
}

int main(void)
{
	SetConsoleOutputCP(1251);
	srand(time(NULL));
	int n, ** G;
	printf("Введите n: ");
	scanf_s("%d", &n);
	G = (int**)malloc(n * sizeof(int*));
	printf("Матрица смежности:\n");
	for (int i = 0; i < n; i++)
	{
		G[i] = (int*)malloc(n * sizeof(int));
	}

	for (int i = 0; i < n; i++)
	{
		for (int j = i; j < n; j++)
		{
			G[i][j] = rand() % 2;
			if (i == j)
			{
				G[i][j] = 0;
			}
			G[j][i] = G[i][j];
		}
	}

	for (int i = 0; i < n; i++)
	{
		for (int j = 0; j < n; j++)
		{
			printf("%d\t", G[i][j]);
		}
		printf("\n");
	}

	printf("\n");
	otozhd(n, G);
	styagivanie(n, G);
	rashep(n, G);
}
