void XuatNDChan(int n);
void ChiaHet(int n);
void XuatCacChuSo(int n);
void TinhTong(int n);

void XuatNDChan(int n) {
	cout << "Xuat ra man hinh cac so nguyen duong chan khong lon hon " << n << " la :\n ";
	int dong = 0;
	for (int i = 1; i < n; i++)
	{
		if (i % 2 == 0) {
			cout << i << "\t";
			dong += 1;
			if (dong % 6 == 0) {
				cout << endl;
			}
		}
	}
}

void ChiaHet(int n) {
	int count = 0;
	cout << "Xuat " << n << " so nguyen duong dau tien chia het cho 4, nhung khong chia het cho 6 la :\n";
	for (int i = 1; ; i++)
	{
		if (i % 4 == 0 && i % 6 != 0) {
			cout << i << "\t";
			count++;
		}
		if (count == n)
		{
			break;
		}
	}
}

void XuatCacChuSo(int n) {
	cout << "Xuat ra man hinh cac chu so " << n << ", 2 chu so cach nhau 1 tab la :\n";
	/*int tmp = 0;
	int res = 0;
	int dem = 0;
	for (int i = 0; i <= n; i++)
	{
		tmp = n % 10;
		dem++;
		cout << tmp;
		if (dem % 2 == 0) {
			cout << "\t";
		}
		n /= 10;
	}*/
	int soTemp = 0;
	int sum = 0, dem = 0;
	while (n != 0)
	{
		soTemp = (soTemp * 10) + (n % 10);
		n /= 10;
	}
	while (soTemp != 0)
	{
		dem++;
		sum = soTemp % 10;
		cout << sum;
		if (dem % 2 == 0) {
			cout << "\t";
		}
		soTemp /= 10;
	}
}

void TinhTong(int n) {
	cout << "Tong cua cac chu so trong " << n << " la :";
	int sum = 0;
	int kq = 0;
	for (; n != 0;)
	{
		kq = n % 10;
		sum += kq;
		n /= 10;
	}
	cout << sum;
}
