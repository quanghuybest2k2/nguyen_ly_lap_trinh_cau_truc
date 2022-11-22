void XuatMenu();
int  ChonMenu(int soMenu);
void XuLyMenu(DaySo a, int menu, int& n);

void XuatMenu() {
	cout << "\t\t\t\t Menu Chuc Nang \n";
	cout << "\t1. Nhap day so \n";
	cout << "\t2. Xuat day so \n";
	cout << "\t3. Tinh tich cac phan tu trong day so \n";
	cout << "\t4. Tinh gia tri lon nhat cua day so \n";
	cout << "\t5. Tim vi tri dau tien cua gia tri lon nhat \n";
	cout << "\t6. Sap xep Khong_GiamDan \n";
}

int ChonMenu(int soMenu) {
	int stt = -1;
	while (stt < 0 || stt > soMenu) {
		system("cls");
		XuatMenu();
		cout << "\nChon chuc nang cua Menu >> ";
		cin >> stt;
	}
	if (stt == 0) {
		cout << "\nOk. Chuong trinh da thoat! Cam on ban..\n";
		exit(0);
	}
	return stt;
}

void XuLyMenu(DaySo a, int menu, int& n) {
	switch (menu) {
	case 1: cout << "Ban da chon chuc nang 1 !";
		NhapMangTD(a, n);
		XuatMang(a, n);
		_getch();
		break;
	case 2: cout << "Ban da chon chuc nang 2 !";
		XuatMang(a, n);
		_getch();
		break;
	case 3: cout << "Ban da chon chuc nang 3 !";
		XuatMang(a, n);
		cout << "Tich cua day so la: " << TinhTich(a, n);
		_getch();
		break;
	case 4: cout << "Ban da chon chuc nang 4 !";
		XuatMang(a, n);
		cout << "Gia tri lon nhat cua day so la: " << TimMax(a, n);
		_getch();
		break;
	case 5: cout << "Ban da chon chuc nang 5 !";
		XuatMang(a, n);
		cout << "Gia tri lon nhat cua day so la: " << TimMax(a, n) << " va vi tri cua Max la: " << ViTriDauTien_Max(a, n);
		_getch();
		break;
	case 6: cout << "Ban da chon chuc nang 6 !";
		XuatMang(a, n);
		Khong_KhacGiam(a, n);
		_getch();
		break;
	}
}