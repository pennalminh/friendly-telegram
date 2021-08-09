# friendly-telegram
#include<string.h>
#include<iostream>
#include <fstream>
#include<iomanip>
#include<conio.h>
using namespace std;

//Class cau thu
class CauThu
{
private:
	int Cmnd =0;
	string Ten;
	string QuocTich;
	string NgaySinh;
	int ChieuCao=0;
	int CanNang=0;
	string ViTri;
public:
	~CauThu() {}
	friend void XuatCauThu(CauThu a[], int s);
	friend void NhapCauThu(CauThu &a);
	friend void NhapCauThu1(CauThu a[], int s);
	friend void SuaCauThu(CauThu a[], int s);
	friend void XoaCauThu(CauThu a[], int s);
	friend int DocFileCauThu(CauThu a[]);
	friend void GhiFileCauThu(CauThu a[], int s);
	friend void CauThuNs(CauThu a[], int s);
	friend void CauThuVt(CauThu a[], int s);
};

//Ham nhap cau thu
void NhapCauThu(CauThu &a){
	cout<<"Nhap so chung minh nhan dan: ";
	cin>>a.Cmnd;
	cout<<"Nhap ho va ten: ";
	cin.ignore();
	getline(cin,a.Ten);
	cout<<"Nhap quoc tich: ";
	getline(cin,a.QuocTich);
	cout<<"Nhap ngay sinh: ";
	getline(cin,a.NgaySinh);
	cout<<"Nhap chieu cao (cm): ";
	cin>>a.ChieuCao;
	cout<<"Nhap can nang(kg): ";
	cin>>a.CanNang;
	cin.ignore();
	cout<<"Nhap vi tri thi dau: ";
	getline(cin,a.ViTri);
}

//Ham nhap cau thu vao danh sach
void NhapCauThu1(CauThu a[], int s){
		cout<<"Nhap cau thu thu "<<s+1<<":"<<endl;
		NhapCauThu(a[s]);
}

//Ham xuat cau thu
void XuatCauThu(CauThu a[], int s){
		int c;
		int count=0;
		cout<<"Nhap so cmnd cua cau thu: ";
		cin>>c;
		for(int i=0; i<s ; i++){
			if(a[i].Cmnd==c){
				cout<<"________________________________________________________________________________________________________________"<<endl;
				cout<<"So cmnd\t\tHo ten\t\t\tQuoc tich\tNgay sinh\tChieu cao\tCan nang\tVi tri"<<endl;
				cout<<a[i].Cmnd<<"\t\t"<<a[i].Ten<<"\t"<<a[i].QuocTich<<"\t"<<a[i].NgaySinh<<"\t"<<a[i].ChieuCao<<"\t\t"<<a[i].CanNang<<"\t\t"<<a[i].ViTri<<endl;
				cout<<"________________________________________________________________________________________________________________"<<endl;
				count++;
			}
		}
		if(count==0){
			cout<<"Khong co cau thu nao co so cmnd nay! Moi nhap lai.";
		}
}

//Ham sua thong tin cau thu
void SuaCauThu(CauThu a[], int s){
	int c;
	int count=0;
	cout<<"Nhap so cmnd cua cau thu: ";
	cin>>c;
	for(int i=0;i<s;i++){
		if(c==a[i].Cmnd){
		count++;
		NhapCauThu(a[i]);
		}
	}
	if(count == 0){
		cout<<"Nhap sai so cmnd! Moi nhap lai";
	}
}

//Ham xoa cau thu
void XoaCauThu(CauThu a[], int s){
	int c;
	int count=0;
	cout<<"Nhap so cmnd cua cau thu: ";
	cin>>c;
	for(int i=0;i<s;i++){
		if (c==a[i].Cmnd)
		{
			count++;
			for (int j = i; j < s; j++) {
                a[j] = a[j+1];
            }
		}
	}
	if(count==0){
		cout<<"Nhap sai! Moi nhap lai.";
	}
}

//Ham liet ke cau thu theo nam sinh
void CauThuNs(CauThu a[], int s){
	string b;
	string temp;
	int count=0;
	cout<<"Nhap nam sinh: ";
	cin.ignore();
	cin>>b;
	cout<<"________________________________________________________________________________________________________________"<<endl;
	for(int i=0;i<s;i++){
		temp=a[i].NgaySinh.substr(6);	
		if(b==temp){
			cout<<"So cmnd\t\tHo ten\t\t\tQuoc tich\tNgay sinh\tChieu cao\tCan nang\tVi tri"<<endl;
			cout<<a[i].Cmnd<<"\t\t"<<a[i].Ten<<"\t\t"<<a[i].QuocTich<<"\t"<<a[i].NgaySinh<<"\t"<<a[i].ChieuCao<<"\t\t"<<a[i].CanNang<<"\t\t"<<a[i].ViTri<<endl;
			count++;
		}
	}
	if(count==0){
		cout<<"Khong co cau thu nao co nam sinh nay! Moi nhap lai.";
	}
	cout<<"________________________________________________________________________________________________________________"<<endl;
}

//Ham liet ke cau thu theo vi tri
void CauThuVt(CauThu a[], int s){
	string b;
	int count=0;
	cout<<"Nhap vi tri: ";
	cin.ignore();
	cin>>b;
	cout<<"________________________________________________________________________________________________________________"<<endl;
	for(int i=0;i<s;i++){
		if(a[i].ViTri==b){
		cout<<"So cmnd\t\tHo ten\t\t\tQuoc tich\tNgay sinh\tChieu cao\tCan nang\tVi tri"<<endl;
		cout<<a[i].Cmnd<<"\t\t"<<a[i].Ten<<"\t\t"<<a[i].QuocTich<<"\t"<<a[i].NgaySinh<<"\t"<<a[i].ChieuCao<<"\t\t"<<a[i].CanNang<<"\t\t"<<a[i].ViTri<<endl;
		count++;
		}
	}
	if(count==0){
		cout<<"Nhap sai! Moi nhap lai.";
	}
	cout<<"________________________________________________________________________________________________________________"<<endl;
}
//Ham ghi file cau thu
void GhiFileCauThu(CauThu a[], int s){
	ofstream outfile;
	outfile.open("CauThu.txt", ios_base::out);
	for(int i =0;i<s;i++){
		outfile<<a[i].Cmnd<<"\t\t"<<a[i].Ten<<"\t\t"<<a[i].QuocTich<<"\t\t"<<a[i].NgaySinh<<"\t\t"<<a[i].ChieuCao<<"\t\t"<<a[i].CanNang<<"\t\t"<<a[i].ViTri<<endl;
	}
	outfile.close();
}

//Ham doc file cau thu
int DocFileCauThu(CauThu a[]){
	ifstream infile;
	int i=0;
	infile.open("CauThu.txt", ios_base::in);
	while (!infile.eof())
	{
		infile>>a[i].Cmnd>>a[i].Ten>>a[i].QuocTich>>a[i].NgaySinh>>a[i].ChieuCao>>a[i].CanNang>>a[i].ViTri;
		if(infile.eof()) {
       		break; 
    	}
		i++;
	}
	infile.close();
	return i;
}


//Class doi bong
class DoiBong
{
private:
	string TenDoi;
	string DiaPhuong;
	string Hlv;
	int n=5;
	string *Ds = new string[n];
public:
	~DoiBong() {}
	friend void NhapDoiBong(DoiBong &a);
	friend void NhapDoiBong1(DoiBong a[], int s);
	friend void XuatDoiBong(DoiBong a[], int s);
	friend void HienThiDs(DoiBong a[], int s);
	friend void SuaDoiBong(DoiBong a[], int s);
	friend void XoaDoiBong(DoiBong a[], int s);
	friend int DocFileDoiBong(DoiBong a[]);
	friend void GhiFileDoiBong(DoiBong a[], int s);	
};

//Ham nhap doi bong
void NhapDoiBong(DoiBong &a){
	cin.ignore();
	cout<<"Nhap ten doi bong: ";
	getline(cin,a.TenDoi);
	cout<<"Nhap dia phuong cua doi bong: ";
	getline(cin,a.DiaPhuong);
	cout<<"Nhap ten huan luyen vien: ";
	getline(cin,a.Hlv);
	cin.ignore();
	for(int i=0;i<a.n;i++){
		cout<<"Nhap ten cau thu "<<i+1<<": ";
		getline(cin,a.Ds[i]);
	}
}

//Ham nhap doi bong vao danh sach
void NhapDoiBong1(DoiBong a[], int s){
		cout<<"Nhap doi bong thu "<<s<<":"<<endl;
		NhapDoiBong(a[s]); 
}

//Ham xuat doi bong theo ten doi
void XuatDoiBong(DoiBong a[], int s){
	string d;
	int count = 0;
	cout<<"Nhap ten doi bong: ";
	getline(cin,d);
	cin>>d;
	for(int i=0; i<s; i++){
		if(d==a[i].TenDoi){
			count++;
			cout<<"________________________________________________________________________________________________________________"<<endl;
			cout<<"Ten doi bong\tDiaPhuong\tTen HLV"<<endl;
			cout<<a[i].TenDoi<<"\t\t"<<a[i].DiaPhuong<<"\t\t"<<a[i].Hlv<<endl;
			cout<<"________________________________________________________________________________________________________________"<<endl;
		}
	}
	if(count == 0){
		cout<<"Nhap sai ten doi bong! Moi nhap lai.";
	}
}

//Ham sua thong tin doi bong
void SuaDoiBong(DoiBong a[], int s){
	string d;
	int count = 0;
	cout<<"Nhap ten doi bong: ";
	cin.ignore();
	getline(cin,d);
	cin>>d;
	for(int i=0; i<s; i++){
		if(d==a[i].TenDoi){
			count++;
			NhapDoiBong(a[i]);
		}
	}
	if(count==0){
		cout<<"Nhap sai ten doi! Moi nhap lai.";
	}
}

//Ham xoa doi bong
void XoaDoiBong(DoiBong a[], int s){
	string d;
	int count = 0;
	cout<<"Nhap ten doi bong: ";
	cin.ignore();
	getline(cin,d);
	cin>>d;
	for(int i=0;i<s;i++){
		if(d==a[i].TenDoi){
			count++;
			for (int j = i; j < s; j++) {
                a[j] = a[j+1];
		}
	}
}
	if(count==0){
		cout<<"Nhap sai! Moi nhap lai.";
	}
}

//Ham hien thi danh sach cau thu
void HienThiDs(DoiBong a[], int s){
	string d;
	int count = 0;
	cout<<"Nhap ten doi bong: ";
	cin.ignore();
	getline(cin,d);
	for (int i = 0; i < s; i++)
	{
		if(d==a[i].TenDoi){
			cout<<"____________________________________"<<endl;
			cout<<"Danh sach cau thu: "<<endl;
			for(int j = 0; j < a[i].n; j++){
				cout<<a[i].Ds[j]<<endl;
			}
			cout<<"____________________________________"<<endl;
			count++;
		}
	}
	if(count == 0){
		cout<<"Nhap sai ten doi bong! Moi nhap lai.";
	}
}

//Ham ghi file doi bong
void GhiFileDoiBong(DoiBong a[], int s){
	ofstream outfile;
	outfile.open("DoiBong.txt", ios_base::out);
	for(int i =0;i<s;i++){
		outfile<<a[i].TenDoi<<"\t\t"<<a[i].DiaPhuong<<"\t\t"<<a[i].Hlv<<"\t"<<a[i].Ds[0]<<endl;
		for (int j = 1; j <a[i].n; j++)
			{
				outfile<<"\t\t\t\t\t\t\t\t\t\t\t"<<a[i].Ds[j]<<endl;
			}
	}
	outfile.close();
}

//Ham doc file doi bong
int DocFileDoiBong(DoiBong a[]){
	ifstream infile;
	int i=0;
	infile.open("DoiBong.txt", ios_base::in);
	while (!infile.eof())
	{
		infile>>a[i].TenDoi>>a[i].DiaPhuong>>a[i].Hlv>>a[i].Ds[0];
		for (int j = 1; j <a[i].n; j++)
			{
				infile>>a[i].Ds[j];
			}
			i++;
		if(infile.eof()) {
       		break; 
    	}
	}
	infile.close();
	return i;
}



//Class tran dau
class TranDau
{
private:
	string NgayThiDau;
	string SanThiDau;
	string TenHaiDoi;
	string TySo;
public:
	 ~TranDau() {}
	  friend void NhapTranDau(TranDau &a);
	  friend void NhapTranDau1(TranDau a[], int s);
	  friend void XuatTranDau(TranDau a[], int s);
	  friend void SuaTranDau(TranDau a[], int s);
	  friend void XoaTranDau(TranDau a[], int s);
	  friend void LietKeTranDau1n(TranDau a[], int s);
	  friend void LietKeTranDau1t(TranDau a[], int s);
	  friend void LietKeTranDau(TranDau a[], int s);
	  friend int DocFileTranDau(TranDau a[]);
	  friend int GhiFileTranDau(TranDau a[], int s);
};


//Ham nhap tran dau
	void NhapTranDau(TranDau &a){
		cin.ignore();
		cout<<"Nhap ngay thi dau: ";
		getline(cin,a.NgayThiDau);
		cout<<"Nhap san thi dau: ";
		getline(cin,a.SanThiDau);
		cout<<"Nhap ten hai doi: ";
		getline(cin,a.TenHaiDoi);
		cout<<"Nhap ty so: ";
		getline(cin,a.TySo);
	}

//Ham nhap tran dau vao danh sach
void NhapTranDau1(TranDau a[], int s){
		cout<<"Nhap tran dau thu "<<s+1<<":"<<endl;
		NhapTranDau(a[s]);
}

//Ham xuat tran dau
void XuatTranDau(TranDau a[], int s){
	string t;
	int count=0;
	cout<<"Nhap ten hai doi: ";
	cin.ignore();
	getline(cin,t);
	for (int i = 0; i < s; i++)
	{
		if(t==a[i].TenHaiDoi){
			count++;
			cout<<"________________________________________________________________________________________________________________"<<endl;
			cout<<"Ngay thi dau\t\tSan thi dau\t\tTen hai doi\t\t\tTy so"<<endl;
			cout<<a[i].NgayThiDau<<"\t\t"<<a[i].SanThiDau<<"\t\t\t"<<a[i].TenHaiDoi<<"\t\t\t"<<a[i].TySo<<endl;
			cout<<"________________________________________________________________________________________________________________"<<endl;
		}
	}
}

//Ham sua tran dau
void SuaTranDau(TranDau a[], int s){
	string t;
	int count=0;
	cout<<"Nhap ten hai doi: ";
	cin.ignore();
	getline(cin,t);
	for(int i=0;i<s;i++){
		if(t==a[i].TenHaiDoi){
			count++;
			NhapTranDau(a[i]);
		}
	}
	if(count==0){
		cout<<"Nhap sai!Moi nhap lai.";
	}
}

//Ham xoa tran dau
void XoaTranDau(TranDau a[], int s){
		string t;
		int count=0;
		cout<<"Nhap ten hai doi: ";
		cin.ignore();
		getline(cin,t);
		for(int i=0;i<s;i++){
			if(t==a[i].TenHaiDoi){
				count++;
				for (int j = i; j < s; j++) {
                a[j] = a[j+1];
			}
			break;
		}
	}
	if(count==0){
		cout<<"Nhap sai! Moi nhap lai.";
	}
}

//Ham liet ke tran dau trong 1 ngay
void LietKeTranDau1n(TranDau a[], int s){
	string b;
	string temp;
	int count=0;
	cout<<"Nhap ngay: ";
	cin.ignore();
	getline(cin,b);
	for(int i=0;i<s;i++){
		temp=a[i].NgayThiDau;
		if(temp==b){
			count++;
			cout<<"________________________________________________________________________________________________________________"<<endl;
			cout<<"Ngay thi dau\t\tSan thi dau\t\tTen hai doi\t\t\tTy so"<<endl;
			cout<<a[i].NgayThiDau<<"\t\t"<<a[i].SanThiDau<<"\t\t\t"<<a[i].TenHaiDoi<<"\t\t\t"<<a[i].TySo<<endl;
			cout<<"________________________________________________________________________________________________________________"<<endl;
		}
	}
	if(count==0){
		cout<<"Nhap sai! Moi nhap lai.";
	}
}

//Ham liet ke tran dau trong 1 thang.
void LietKeTranDau1t(TranDau a[], int s){
	string b;
	string temp;
	int count=0;
	cout<<"Nhap thang va nam: ";
	cin.ignore();
	getline(cin,b);
	for(int i=0;i<s;i++){
		temp=a[i].NgayThiDau.substr(3);
		if(temp==b){
			count++;
			cout<<"________________________________________________________________________________________________________________"<<endl;
			cout<<"Ngay thi dau\t\tSan thi dau\t\tTen hai doi\t\t\tTy so"<<endl;
			cout<<a[i].NgayThiDau<<"\t\t"<<a[i].SanThiDau<<"\t\t\t"<<a[i].TenHaiDoi<<"\t\t\t"<<a[i].TySo<<endl;
			cout<<"________________________________________________________________________________________________________________"<<endl;
		}
	}
	if(count==0){
		cout<<"Nhap sai! Moi nhap lai.";
	}
}

//Ham liet ke tran dau trong toan giai
void LietKeTranDau(TranDau a[], int s){
	cout<<"________________________________________________________________________________________________________________"<<endl;
	for (int i = 0; i < s; i++)
	{
		cout<<"Ngay thi dau\t\tSan thi dau\t\tTen hai doi\t\t\tTy so"<<endl;
		cout<<a[i].NgayThiDau<<"\t\t"<<a[i].SanThiDau<<"\t\t\t"<<a[i].TenHaiDoi<<"\t\t\t"<<a[i].TySo<<endl;
	}
		cout<<"________________________________________________________________________________________________________________"<<endl;
}

//Ham ghi file tran dau
int GhiFileTranDau(TranDau a[], int s){
	ofstream outfile;
	outfile.open("TranDau.txt", ios_base::out);
	for(int i =0;i<s;i++){
		outfile<<a[i].NgayThiDau<<"\t\t"<<a[i].SanThiDau<<"\t\t\t"<<a[i].TenHaiDoi<<"\t\t\t"<<a[i].TySo<<endl;
	}
	outfile.close();
}

//Ham doc file tran dau
int DocFileTranDau(TranDau a[]){
	ifstream infile;
	int i=0;
	infile.open("TranDau.txt", ios_base::in);
	
	while (!infile.eof())
	{
		infile>>a[i].NgayThiDau>>a[i].SanThiDau>>a[i].TenHaiDoi>>a[i].TySo;
		if(infile.eof()) {
       		break; 
    	}
		i++;
	}
	infile.close();
	return i;
}

//Ham main
int main(){
	int key;
	int slCauThu = 0;
	int slDoiBong = 0;
	int slTranDau = 0;
	CauThu  aCauThu [100];
	DoiBong aDoiBong[100];
	TranDau aTranDau[100];
	slCauThu = DocFileCauThu(aCauThu);
	slTranDau = DocFileTranDau(aTranDau);
	slDoiBong = DocFileDoiBong(aDoiBong);
	while (true)
	{
		system("cls");
		cout<<"_____________________*MENU*____________________"<<endl;
		cout<<"|                                             |"<<endl;
		cout<<"|  1. Them thong tin.                         |"<<endl;
		cout<<"|  2. Sua thong tin.                          |"<<endl;
		cout<<"|  3. Xoa thong tin.                          |"<<endl;
		cout<<"|  4. Hien thi thong tin.                     |"<<endl;
		cout<<"|  5. Liet ke ket qua tran dau.               |"<<endl;
		cout<<"|  6. Liet ke cau thu.                        |"<<endl;
		cout<<"|  8. Luu thong tin.                          |"<<endl;
		cout<<"|  0. Thoat chuong trinh.                     |"<<endl;
		cout<<"|_____________________________________________|"<<endl<<endl;
		cout<<"Nhap tuy chon: ";
		cin>>key;
		switch (key)
		{
		case 1:
			cout<<endl<<"Them thong tin"<<endl;
			cout<<"____________________________"<<endl;
			cout<<"|                           |"<<endl;
			cout<<"| 1. Them cau thu.          |"<<endl;
			cout<<"| 2. Them doi bong.         |"<<endl;
			cout<<"| 3. Them tran dau          |"<<endl;
			cout<<"| 4. Thoat.                 |"<<endl;
			cout<<"|___________________________|"<<endl;
			cin>>key;
			switch (key)
			{
			case 1:
				NhapCauThu1(aCauThu, slCauThu);
				slCauThu++;
				getch();
				break;
			case 2:
				NhapDoiBong1(aDoiBong, slDoiBong);
				slDoiBong++;
				getch();
				break;
			case 3:
				NhapTranDau1(aTranDau, slTranDau);
				slTranDau++;
				getch();
				break;
			case 4:
				getch();
				break;
			default:
				cout<<"Nhap sai chuc nang! Moi nhap lai.";
				getch();
				break;
			}
			break;
		case 2:
			cout<<"Sua thong tin"<<endl;
			cout<<"____________________________"<<endl;
			cout<<"|                           |"<<endl;
			cout<<"| 1. Sua cau thu.           |"<<endl;
			cout<<"| 2. Sua doi bong.          |"<<endl;
			cout<<"| 3. Sua tran dau           |"<<endl;
			cout<<"| 4. Thoat				   |"<<endl;
			cout<<"|___________________________|"<<endl;
			cin>>key;
			switch (key)
			{
			case 1:
				SuaCauThu(aCauThu, slCauThu);
				cout<<"Sua thanh cong!";
				getch();
				break;
			case 2:
				SuaDoiBong(aDoiBong, slDoiBong);
				cout<<"Sua thanh cong!";
				getch();
				break;
			case 3:
				SuaTranDau(aTranDau, slTranDau);
				cout<<"Sua thanh cong!";
				getch();
				break;
			case 4:
				getch();
				break;
			default:
				cout<<"Nhap sai chuc nang! Moi nhap lai.";
				getch();
				break;
			}
			break;
			case 3:
				cout<<"Xoa thong tin"<<endl;
				cout<<"____________________________"<<endl;
				cout<<"|                           |"<<endl;
				cout<<"| 1. Xoa cau thu.           |"<<endl;
				cout<<"| 2. Xoa doi bong.          |"<<endl;
				cout<<"| 3. Xoa tran dau           |"<<endl;
				cout<<"| 4. Thoat				   |"<<endl;
				cout<<"|___________________________|"<<endl;
				cin>>key;
				switch (key)
				{
				case 1:
					XoaCauThu(aCauThu, slCauThu);
					slCauThu--;
					cout<<"Xoa thanh cong!";
					getch();
					break;
				case 2:
					XoaDoiBong(aDoiBong, slDoiBong);
					slDoiBong--;
					cout<<"Xoa thanh cong!";
					getch();
					break;
				case 3:
					XoaTranDau(aTranDau, slTranDau);
					slTranDau--;
					cout<<"Xoa thanh cong!";
					getch();
					break;
				case 4:
					getch();
					break;
				default:
					cout<<"Nhap sai chuc nang! Moi nhap lai.";
					getch();
					break;
				}
				break;
				case 4:
					cout<<"Hien thi thong tin"<<endl;
					cout<<"__________________________________"<<endl;
					cout<<"|                                |"<<endl;
					cout<<"| 1. Hien thi 1 cau thu.         |"<<endl;
					cout<<"| 2. Hien thi 1 doi bong.        |"<<endl;
					cout<<"| 3. Hien thi 1 tran dau.        |"<<endl;
					cout<<"| 4. Hien thi danh sach cau thu. |"<<endl;
					cout<<"| 5. Thoat.				        |"<<endl;
					cout<<"|________________________________|"<<endl;
					cin>>key;
					switch (key)
					{
					case 1:
						XuatCauThu(aCauThu, slCauThu);
						getch();
						break;
					case 2:
						XuatDoiBong(aDoiBong, slDoiBong);
						getch();
						break;
					case 3:
						XuatTranDau(aTranDau, slTranDau);
						getch();
						break;
					case 4:
						HienThiDs(aDoiBong, slDoiBong);
						getch();
						break;
					case 5:
						getch();
						break;
					default:
						cout<<"Nhap sai chuc nang! Moi nhap lai.";
						getch();
						break;
					}
					break;
				case 5:
					cout<<"Liet ke ket qua tran dau"<<endl;
					cout<<"__________________________________"<<endl;
					cout<<"|                                |"<<endl;
					cout<<"| 1. Trong 1 ngay.               |"<<endl;
					cout<<"| 2. Trong 1 thang.              |"<<endl;
					cout<<"| 3. Trong toan giai.            |"<<endl;
					cout<<"| 4. Thoat.				        |"<<endl;
					cout<<"|________________________________|"<<endl;
					cin>>key;
					switch (key)
					{
					case 1:
						LietKeTranDau1n(aTranDau, slTranDau);
						getch();
						break;
					case 2:
						LietKeTranDau1t(aTranDau, slTranDau);
						getch();
						break;
					case 3:
						LietKeTranDau(aTranDau, slTranDau);
						getch();
						break;
					case 4:
						getch();
						break;
					default:
						cout<<"Nhap sai chuc nang! Moi nhap lai.";
						getch();
						break;
					}
					break;
				case 6:
					cout<<"Liet ke cau thu"<<endl;
					cout<<"__________________________________"<<endl;
					cout<<"|                                |"<<endl;
					cout<<"| 1. Theo nam sinh.              |"<<endl;
					cout<<"| 2. Theo vi tri.                |"<<endl;
					cout<<"| 3. Thoat.				        |"<<endl;
					cout<<"|________________________________|"<<endl;
					cin>>key;
					switch (key){
						case 1:
							CauThuNs(aCauThu, slCauThu);
							getch();
							break;
						case 2:
							CauThuVt(aCauThu, slCauThu);
							getch();
							break;
						case 3:
							getch();
							break;
						default:
							cout<<"Nhap sai chuc nang! Moi nhap lai.";
							getch();
							break;
						}
					break;
				case 7:
					break;
				case 8:
					cout<<"Luu thong tin"<<endl;
					cout<<"__________________________________"<<endl;
					cout<<"|                                |"<<endl;
					cout<<"| 1. Luu cau thu.                |"<<endl;
					cout<<"| 2. Luu doi bong.               |"<<endl;
					cout<<"| 3. Luu tran dau.               |"<<endl;
					cout<<"| 4. Thoat.                      |"<<endl;
					cout<<"|________________________________|"<<endl;
					cin>>key;
					switch(key){
						case 1:
							GhiFileCauThu(aCauThu, slCauThu);
							cout<<"Luu thong tin thanh cong!";
							getch();
							break;
						case 2:
							GhiFileDoiBong(aDoiBong, slDoiBong);
							cout<<"Luu thong tin thanh cong!";
							getch();
							break;
						case 3:
							GhiFileTranDau(aTranDau, slTranDau);
							cout<<"Luu thong tin thanh cong!";
							getch();
							break;
						case 4:
							getch();
							break;
						default:
							cout<<"Nhap sai chuc nang! Moi nhap lai.";
							getch();
							break;
						}
					break;
				case 0:
					return 0;
					break;
				default:
					cout<<"Nhap sai chuc nang! Moi nhap lai.";
					getch();
					break;
		}
	}
	return 0;
}
