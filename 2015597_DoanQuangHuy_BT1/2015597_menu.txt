void XuatMenu();
int  ChonMenu(int soMenu);
void XuLyMenu(int menu, int n);

void XuatMenu() {
	cout << "\n\t\t\t\tMenu Chuc Nang\n";
	cout << "\t0. Thoat khoi chuong trinh\n";
	cout << "\t1. Xuat ra man hinh cac so nguyen duong chan khong lon hon n\n";
	cout << "\t2. Xuat n so nguyen duong dau tien chia het cho 4, nhung khong chia het cho 6\n";
	cout << "\t3. Xuat ra man hinh cac chu so n, 2 chu so cach nhau 1 tab\n";
	cout << "\t4. Tinh tong cac chu so trong n\n";
}

int ChonMenu(int soMenu) {
	int stt = -1;
	while (stt < 0 || stt > soMenu) {
		system("cls");
		XuatMenu();
		cout << "\n Chon chuc nang cua Menu >> ";
		cin >> stt;
	}
	if (stt == 0) {
		cout << "Ok. Chuong trinh da thoat! Cam on ban..";
		exit(0);
	}
	return stt;
}

void XuLyMenu(int menu, int n) {
	int ketQua;
	switch (menu) {
	case 1: 
		cout << "Ban da chon chuc nang 1!\n";
		XuatNDChan(n);
		break;
	case 2:
		cout << "Ban da chon chuc nang 2!\n";
		ChiaHet(n);
		break;
	case 3:
		cout << "Ban da chon chuc nang 3!\n";
		XuatCacChuSo(n);
		break;
	case 4:
		cout << "Ban da chon chuc nang 4!\n";
		TinhTong(n);
		break;
	}
	_getch();
}
