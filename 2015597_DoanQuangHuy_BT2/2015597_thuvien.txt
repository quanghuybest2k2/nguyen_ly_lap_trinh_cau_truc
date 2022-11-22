#define TAB '\t'
#define SIZE 100

typedef int DaySo[SIZE];

void NhapMangTD(DaySo a, int& n);
void XuatMang(DaySo a, int n);
int TinhTich(DaySo a, int n);
int TimMax(DaySo a, int n);
int ViTriDauTien_Max(DaySo a, int n);
int TimXTrongDoan(DaySo a, int x, int l, int r);
void Khong_KhacGiam(DaySo a, int n);

void NhapMangTD(DaySo a, int& n) {
	do {
		cout << "\nNhap vao so phan tu cua mang: ";
		cin >> n;
	} while (0 > n);
	srand((unsigned)time(0));

	for (int i = 0; i < n; i++) {
		a[i] = rand() % (4 - -4 + 1) + -4; // Giới hạn sinh số ngẫu nhiên trong phạm vi: CT rand() % (max - min + 1) + min
	}
}
void XuatMang(DaySo a, int n) {
	cout << "\nDay so cua ban la: \n";
	for (int i = 0; i < n; i++) {
		cout << a[i] << TAB;
	}
	cout << '\n';
}
int TinhTich(DaySo a, int n) {
	int tich = 1;
	for (int i = 0; i < n; i++)
	{
		tich *= a[i];
	}
	return tich;
}
int TimMax(DaySo a, int n) {
	int max = a[0];
	for (int i = 1; i < n; i++) {
		if (max < a[i]) {
			max = a[i];
		}
	}
	return max;
}
int ViTriDauTien_Max(DaySo a, int n) {

	int max = TimMax(a, n);
	for (int i = 0; i < n; i++) {
		if (max == a[i]) {
			return i;
		}
	}
	return -1;
}
int TimXTrongDoan(DaySo a, int x, int l, int r) {
	int kq = 0;
	for (int i = l; i <= r; i++) {
		if (a[i] == x) {
			kq = 1;
			break;
		}
	}
	return kq;
}

void Khong_KhacGiam(DaySo a, int n) {
	cout << "\nDay so sau khi sap xep la : ";
	int dk, tg;
	for (int i = 0; i < n; i++) {
		for (int j = i + 1; j < n; j++) {
			dk = (a[i] < 0 && a[j] < 0 && a[i] < a[j]
				|| a[i] < 0 && a[j] == 0
				|| a[i] < 0 && a[j]>0
				|| a[i]>0 && a[j] == 0
				|| a[i]>0 && a[j]>0 && a[i] < a[j]);
			if (dk) {
				tg = a[i];
				a[i] = a[j];
				a[j] = tg;
			}
		}
	}
	// Loại bỏ các số bị trùng:
	for (int i = 0; i < n; i++) {
		if (TimXTrongDoan(a, a[i], 0, i - 1) == 0) {
			cout << a[i] << TAB;
		}
	}
}