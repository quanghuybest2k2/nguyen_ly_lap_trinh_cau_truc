#include <iostream>
#include <conio.h>
#include <iomanip>
#include <fstream>
#include <string.h>

using namespace std;

#include "thuvien.h"
#include "menu.h"

void ChayChuongTrinh();

int main()
{
	ChayChuongTrinh();
	return 0;
}
void ChayChuongTrinh()
{
	int stt;
	int n = 0;
	int soMenu = 5;
	HOCVIEN a[MAX];
	do
	{
		stt = ChonMenu(soMenu);
		XuLyMenu(stt, a, n);
	} while (stt > 0);
}