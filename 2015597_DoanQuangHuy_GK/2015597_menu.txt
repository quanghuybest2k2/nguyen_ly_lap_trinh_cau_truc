void XuatMenu();
int ChonMenu(int soMenu);
void XuLyMenu(int menu, MaTran a, int& n);

void XuatMenu()
{
	cout << "\t\t\t\tMenu Chuc Nang\n";
	cout << "\t0. Thoat chuong trinh!\n";
	cout << "\t1. Nhap ma tran tu dong a cap n cac so nguyen trong khoang [-3,3]\n";
	cout << "\t2. Xem ma tran\n";
	cout << "\t3. Tinh tinh tong cac phan tu cua hang i\n";
	cout << "\t4. Tinh tich cac phan tu cua cot j\n";
	cout << "\t5. Xuat ra man hinh cac phan tu theo yeu cau\n";
}
int ChonMenu(int soMenu)
{
	int stt;
	for (;;)
	{
		system("CLS");
		XuatMenu();
		cout << "\n Ban hay nhap Menu tuy chon, STT >> ";
		cin >> stt;
		if (0 <= stt && stt <= soMenu)
		{
			break;
		}
	}
	return stt;
}
void XuLyMenu(int menu, MaTran a, int& n)
{
	int i, j;
	switch (menu)
	{
	case 0:
		system("CLS");
		cout << "\nOk. Chuong trinh da thoat!\n";
		break;
	case 1:
		system("CLS");
		cout << "1. Nhap ma tran tu dong a cap n cac so nguyen trong khoang [-3,3]\n";
		NhapMaTran_TD(a, n);
		XuatMaTran(a, n);
		break;
	case 2:
		system("CLS");
		cout << "\n2. Xem ma tran\n";
		XuatMaTran(a, n);
		break;
	case 3: 
		system("CLS");
		cout << "\n3. Tinh tinh tong cac phan tu cua hang i\n";
		XuatMaTran(a, n);
		cout << "\nBan hay nhap hang muon tinh tong, i = ";
		cin >> i;
		cout << "Tong cac phan tu cua hang " << i << " la: " << TinhTongHang(a, n, i);
		break;
	case 4: 
		system("CLS");
		cout << "\n4. Tinh tich cac phan tu cua cot j\n";
		XuatMaTran(a, n);
		cout << "\nBan hay nhap cot muon tinh tich, j = ";
		cin >> j;
		cout << "Tich cac phan tu cua cot " << j << " la: " << TinhTichCot(a, n, j);
		break;
	case 5: 
		system("CLS");
		cout << "\n5. Xuat ra man hinh cac phan tu theo yeu cau\n";
		XuatMaTran(a, n);
		Tim_MaxHang_MinCot(a, n);
		break;
	}
	_getch();
}