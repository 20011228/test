#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>     
#include <string.h>    
#include <stdlib.h>    
#include <Windows.h>    
#include<iostream>

void gotoxy(int x, int y)
{
	COORD pos; pos.X = x - 1; pos.Y = y - 1;
	SetConsoleCursorPosition(GetStdHandle(STD_OUTPUT_HANDLE), pos);
}

int main(int argc, char*argv[])
{
	system("mode con cols=400 lins=120");
	system("color f0");
	system("D:\\字符动画\\音乐\\audio.mp4");
	Sleep(1000);
	long i;
	char FileName[100];
	char str[10000];
	signed char hi;
	FILE*in;

	int x = 0;
	for (i = 1; i <=3501; i++)
	{
		x = 0;
		sprintf_s(FileName, "D:\\字符动画\\字符5\\ASCII-第五人格 (%ld).txt", i);
		in = fopen(FileName, "r");
		while (fread(&hi, sizeof(char), 1, in) != 0)
		{
			str[x++] = hi;
		}
		str[x++] = '\0';
		printf("%s\n", str);
		gotoxy(0, 0);
		Sleep(30);
		fclose(in);
	}

	printf("谢谢观看\n");
	system("pause");

}
