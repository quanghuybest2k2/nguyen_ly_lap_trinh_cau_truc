void XuatMenu()
{
	cout << "\n\n\t\t\t\tMENU CHUC NANG\n";
	cout << "\t\t0. Thoat khoi chuong trinh\n";
	cout << "\t\t1. Tao bang diem hoc vien\n";
	cout << "\t\t2. Xem danh sach hoc vien\n";
	cout << "\t\t3. Xuat danh sach cac hoc vien trong bang diem cao nhat\n";
	cout << "\t\t4. Xoa cac hoc vien co nam sinh cho truoc ra khoi bang diem mon hoc\n";
	cout << "\t\t5. Sap bang diem mon hoc tang dan theo ho va ten hoc vien\n";
}
int ChonMenu(int soMenu)
{

	int stt; 
	for (;;)
	{
		system("cls");
		XuatMenu();
		cout << "\nNhap 1 tuy chon menu >> ";
		cin >> stt;
		if (0 <= stt && stt <= soMenu)
		{
			break;
		}
	}
	return stt;
}
void XuLyMenu(int stt, HOCVIEN a[MAX], int& n)
{
	char* f;
	int check;
	int namXoa;
	system("cls");
	switch (stt)
	{
	case 0:
		cout << "\nOK. CHUONG TRINH DA THOAT !\n";
		exit(0);
		break;
	case 1:
		cout << "\n1. Tao bang diem hoc vien\n";
		f = new char[MAX];
		do
		{
			cout << "\nNhap file : ";
			cin >> f;
			check = TaoBangDiem(a, n, f);
		} while (!check);
		cout << "\nMo tep thanh cong!\n";
		delete[] f;
		break;
	case 2:
		cout << "\n2. Xem danh sach hoc vien\n";
		Xuat_DS_HV(a, n);
		break;
	case 3:
		cout << "\n3. Xuat danh sach cac hoc vien trong bang diem cao nhat\n";
	
		Xuat_DS_Theo_Diem(a, n);
		break;
	case 4:
		cout << "\n4. Xoa cac hoc vien co nam sinh cho truoc ra khoi bang diem mon hoc\n";
		cout << "\nDanh sach hien hanh : ";
		Xuat_DS_HV(a, n);
		cout << "\nNhap vao nam can xoa : ";
		cin >> namXoa;
		Xoa_HV(a, n, namXoa);
		cout << "\nDanh sach sau khi xoa :\n";
		Xuat_DS_HV(a, n);
		break;
	case 5:
		cout << "\n5. Sap bang diem mon hoc tang dan theo ho va ten hoc vien\n";
		cout << "\nDanh sach hien hanh :\n";
		Xuat_DS_HV(a, n);
		_getch();
		cout << "\nNhan phim bat ki de hien ds da sx >>";
		system("cls");
		Sap_Xep(a, n);
		cout << "\nDanh sach sau sap xep :\n";
		Xuat_DS_HV(a, n);
		break;
	}
	cout << "\nNhan mot phim bat ki de tiep tuc chuong trinh!";
	_getch();
}