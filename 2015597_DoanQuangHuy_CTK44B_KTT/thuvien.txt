#define MAX 100
typedef unsigned short int Byte;

struct NGAYTHANGNAMSINH
{
	Byte ngay;
	Byte thang;
	unsigned int nam;
};

struct HOCVIEN
{
	char MaHV[8];
	char hoTen[21];
	NGAYTHANGNAMSINH date;
	char queQuan[16];
	double diem;
};

int TaoBangDiem(HOCVIEN a[], int& n, char* tentep)
{
	fstream Nhap(tentep);
	if (!Nhap)
	{
		return 0;
	}
	n = 0;
	while (!Nhap.eof())
	{
		Nhap >> a[n].MaHV;
		Nhap >> a[n].hoTen;
		Nhap >> a[n].date.ngay;
		Nhap >> a[n].date.thang;	
		Nhap >> a[n].date.nam;
		Nhap >> a[n].queQuan;
		Nhap >> a[n].diem;
		n++;
	}
	Nhap.close();
	return 1;
}
void Ke_Ngang(char kyTu)
{
	cout << setiosflags(ios::left) << '|';
	for (int i = 0; i < 86; i++)
	{
		cout << kyTu;
	}
	cout << '|';
}
void Tieu_De()
{
	Ke_Ngang('=');
	cout << '\n' << setiosflags(ios::left) << '|'
		<< setw(8) << "Ma so" << '|'
		<< setw(21) << "Ho ten" << '|'
		<< setw(10) << "Ngay sinh" << '|'
		<< setw(10) << "Thang sinh" << '|'
		<< setw(10) << "Nam sinh" << '|'
		<< setw(16) << "Que quan" << '|'
		<< setw(5) << "Diem" << '|'
		<< '\n';
	Ke_Ngang('=');
}
void Xuat_1_HV(HOCVIEN a)
{
	cout << '\n' << setiosflags(ios::left) << '|'
		<< setw(8) << a.MaHV << '|'
		<< setw(21) << a.hoTen << '|'
		<< setw(10) << a.date.ngay << '|'
		<< setw(10) << a.date.thang << '|'
		<< setw(10) << a.date.nam << '|'
		<< setw(16) << a.queQuan << '|'
		<< setw(5) << a.diem << '|'
		<< '\n';
	Ke_Ngang('_');
}
void Thong_Bao(int tong)
{
	cout << '\n' << setiosflags(ios::left) << '|'
		<< setw(50) << "TONG SO HOC VIEN TRONG DANH SACH LA : " << setw(36) << tong << '|' << '\n';
	Ke_Ngang('=');
}
void Xuat_DS_HV(HOCVIEN a[], int n)
{
	Tieu_De();
	for (int i = 0; i < n; i++)
	{
		Xuat_1_HV(a[i]);
	}
	Thong_Bao(n);
}
int Tim_Max(HOCVIEN a[], int n)
{
	double max = a[0].diem;
	for (int i = 1; i < n; i++)
	{
		if (max < a[i].diem)
		{
			max = a[i].diem;
		}
	}
	return max;
}
void Xuat_DS_Theo_Diem(HOCVIEN a[], int n)
{
	double max = Tim_Max(a, n);
	int VT[MAX];
	int x = 0;
	for (int i = 0; i < n; i++)
	{
		if (max == a[i].diem)
		{
			VT[x++] = i;
		}
	}
	if (x != 0)
	{
		Tieu_De();
		for (int i = 0; i < x; i++)
		{
			Xuat_1_HV(a[VT[i]]);
		}
		Thong_Bao(x);
	}
}
void Xoa_HV(HOCVIEN a[MAX], int& n, int namXoa)
{
	int m = 0;
	for (int i = 0; i < n; i++)
	{
		if (a[i].date.nam != namXoa)
		{
			a[m] = a[i];
			m++;
		}
	}
	n = m;
}

void HoanVi(HOCVIEN& x, HOCVIEN& y)
{
	HOCVIEN z = x;
	x = y;
	y = z;
}

void Sap_Xep(HOCVIEN a[MAX], int n)
{
	for (int i = 0; i < n; i++)
	{
		for (int j = i + 1; j < n; j++)
		{
			if (_strcmpi(a[i].hoTen, a[j].hoTen) > 0)
			{
				HoanVi(a[i], a[j]);
			}
		}

	}
}