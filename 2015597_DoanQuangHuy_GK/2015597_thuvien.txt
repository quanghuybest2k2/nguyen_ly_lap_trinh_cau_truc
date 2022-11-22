#define SIZE 100
#define TAB '\t'

typedef int MaTran[SIZE][SIZE];

void NhapMaTran_TD(MaTran a, int n);
void XuatMaTran(MaTran a, int n);
int TinhTongHang(MaTran a, int n, int i);
int TinhTichCot(MaTran a, int n, int j);
int TimMaxHangi(MaTran a, int n, int i);
int TimMinCotj(MaTran a, int n, int j);
void Tim_MaxHang_MinCot(MaTran a, int n);

void NhapMaTran_TD(MaTran a, int n)
{
	srand(time(0));
	for (int i = 0; i < n; i++)
	{
		for (int j = 0; j < n; j++)
		{
			a[i][j] = rand() % (3 - -3 + 1) + -3;
		}
	}
}
void XuatMaTran(MaTran a, int n)
{
	cout << "Ma tran vuong cua ban la: \n";
	for (int i = 0; i < n; i++)
	{
		for (int j = 0; j < n; j++)
		{
			cout << a[i][j] << TAB;
		}
		cout << '\n';
	}
}
int TinhTongHang(MaTran a, int n, int i)
{
	int sum = 0;
	for (int j = 0; j < n; j++)
	{
		sum += a[i][j];
	}
	return sum;
}
int TinhTichCot(MaTran a, int n, int j)
{
	int tich = 1;
	for (int i = 0; i < n; i++)
	{
		tich *= a[i][j];
	}
	return tich;
}
int TimMaxHangi(MaTran a, int n, int i)
{
	int max;
	max = a[i][0];
	for (int j = 1; j < n; j++)
	{
		if (max < a[i][j])
		{
			max = a[i][j];
		}
	}
	return max;
}

int TimMinCotj(MaTran a, int n, int j)
{
	int min;
	min = a[0][j];
	for (int i = 1; i < n; i++)
	{
		if (min > a[i][j])
		{
			min = a[i][j];
		}
	}
	return min;
}

void Tim_MaxHang_MinCot(MaTran a, int n)
{
	int dau = 0;
	for (int i = 0; i < n; i++)
	{
		for (int j = 0; j < n; j++)
		{
			if (a[i][j] == TimMaxHangi(a, n, i) && a[i][j] == TimMinCotj(a, n, j))
			{
				dau = 1;
				break;
			}
		}
	}
	if (!dau)
	{
		cout << "\nKhong co phan tu nao thoa man dieu kien bai toan!!!!";
	}
	else
	{
		for (int i = 0; i < n; i++)
		{
			for (int j = 0; j < n; j++)
			{
				if (a[i][j] == TimMaxHangi(a, n, i) && a[i][j] == TimMinCotj(a, n, j))
				{
					cout << "\Gia tri thoa man la: "
						<< " a[" << i << "][" << j << "] = " << a[i][j]
						<< " : Max hang " << i << " va Min cot " << j;
				}
			}
		}
	}
}