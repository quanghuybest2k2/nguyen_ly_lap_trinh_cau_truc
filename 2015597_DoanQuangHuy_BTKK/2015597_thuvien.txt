// Khai báo hằng:
#define COT 7
#define HANG 6
#define NGANGDON '_'

// Định nghĩa KDL mới:
typedef int MaTran[HANG][COT];

// Khai báo nguyên mẫu hàm:
void XuatKeNgang();
void XuatThuTrongTuan();
int ThuTrongTuan(int thang, int nam);
int SoNgayTrongThang(int thang, int nam);
bool KiemTraNamNhuan(int nam);
void TaoLich(MaTran& lich, int thang, int nam);
void XuatLich(MaTran lich);

// Functions:
void XuatKeNgang()
{
	cout << "\n";
	for (int i = 1; i <= 39; i++)
		cout << NGANGDON;
}
void XuatThuTrongTuan()
{
	XuatKeNgang();
	cout << '\n';
	cout << setiosflags(ios::left)
		<< setw(6) << "Sun "
		<< setw(6) << "Mon "
		<< setw(6) << "Tue "
		<< setw(6) << "Wed "
		<< setw(6) << "Thu "
		<< setw(6) << "Fri "
		<< setw(6) << "Sat ";
	XuatKeNgang();
}
int ThuTrongTuan(int thang, int nam)
{
	int t, x, k,
		thu;
	t = nam - (14 - thang) / 12;
	x = t + t / 4 - t / 100 + t / 400;
	k = thang + 12 * ((14 - thang) / 12) - 2;
	thu = (1 + x + (31 * k) / 12) % 7;
	return thu;
}
bool KiemTraNamNhuan(int nam)
{
	bool check = false;
	if ((nam % 4 == 0 && nam % 100 != 0) || nam % 400 == 0)
	{
		check = true;
	}
	return check;
}
int SoNgayTrongThang(int thang, int nam)
{
	int soNgay;
	switch (thang)
	{
	case 1:
	case 3:
	case 5:
	case 7:
	case 8:
	case 10:
	case 12:
		soNgay = 31;
		break;
	case 4:
	case 6:
	case 9:
	case 11:
		soNgay = 30;
		break;
	default:
		if (KiemTraNamNhuan(nam))
			soNgay = 29;
		else
			soNgay = 28;
		break;
	}
	return soNgay;
}
void TaoLich(MaTran& lich, int thang, int nam)
{
	int thu = ThuTrongTuan(thang, nam); 
	int soNgay = SoNgayTrongThang(thang, nam);

	for (int i = 0; i < HANG; i++)
	{
		for (int j = 0; j < COT; j++)
		{
			lich[i][j] = 0;
		}
	}

	int dem = 1;
	for (int j = thu; j < COT; j++, dem++)
	{
		lich[0][j] = dem;
	}
	for (int i = 1; i < HANG; i++)
	{
		for (int j = 0; j < COT; j++, dem++)
		{
			if (dem > soNgay)
				break;
			lich[i][j] = dem;
		}
	}
}
void XuatLich(MaTran lich)
{
	int dem = 1;
	XuatThuTrongTuan();
	for (int i = 0; i < HANG; i++)
	{
		cout << "\n";
		for (int j = 0; j < COT; j++)
		{
			if (lich[i][j] == 0)
				cout << setiosflags(ios::left) << setw(6) << " ";
			else
			{
				cout << setiosflags(ios::left) << setw(6) << lich[i][j];
			}
			dem++;
		}
	}
}