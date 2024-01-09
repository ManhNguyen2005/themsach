#include <iostream>
#include <fstream>  
#include <stdlib.h> 
#include <string>  
#include <sstream>
#include <iomanip>

using namespace std;

//Ham them sach vao thu vien
void addBook(){
	ifstream xvtk("book.txt");
    string A[100][8], x;

    int run = 0; 
    
    while (getline(xvtk, x)) 
    {
        string isbn = "", title = "", subject = "",
               author = "", publisher = "", date = "", pages = "", copies = "";

        int kt = 0;
        for (size_t i = 0; i < x.size(); ++i)
        {
            if (x[i] == ' ')
            {
                if (kt == 0)
                {
                    kt = 1;
                    continue;
                }
                if (kt == 1)
                {
                    kt = 2;
                    continue;
                }
                if (kt == 2)
                {
                    kt = 3;
                    continue;
                }
                if (kt == 3)
                {
                    kt = 4;
                    continue;
                }
                if (kt == 4)
                {
                    kt = 5;
                    continue;
                }
                if (kt == 5)
                {
                    kt = 6;
                    continue;
                }
                if (kt == 6)
                {
                    kt = 7;
                    continue;
                }
            }

            if (kt == 0)
            {
                isbn += x[i];
            }
            if (kt == 1)
            {
                title += x[i];
            }
            if (kt == 2)
            {
                subject += x[i];
            }
            if (kt == 3)
            {
                author += x[i];
            }
            if (kt == 4)
            {
                publisher += x[i];
            }
            if (kt == 5)
            {
                date += x[i];
            }
            if (kt == 6)
            {
                pages += x[i];
            }
            if (kt == 7)
            {
                copies += x[i];
            }
        }

        A[run][0] = isbn;
        A[run][1] = title;
        A[run][2] = subject;
        A[run][3] = author;
        A[run][4] = publisher;
        A[run][5] = date;
        A[run][6] = pages;
        A[run][7] = copies;
        run++;
    }
    ofstream ofs("test.txt", ios::out | ios::app);  // Open file for writing
	cout<<"Ban muon them bao nhieu sach vao thu vien: ";
	int soluong;
	cin>>soluong;
	for (int i = 1; i <= soluong; i++){
		string isbn, title, subject, author, publisher,date;
		int pages, copies;
		cout<<"Id sach so "<<i<<" : ";
		cin>>A[run][0];
		ofs<<A[run][0]<<" ";
		cout<<"Ten sach: ";
		cin>>A[run][1];
		ofs<<A[run][1]<<" ";
		cout<<"Chu de: ";
		cin>>A[run][2];
		ofs<<A[run][2]<<" ";
		cout<<"Tac gia: ";
		cin>>A[run][3];
		ofs<<A[run][3]<<" ";
		cout<<"Nha xuat ban: ";
		cin>>A[run][4];
		ofs<<A[run][4]<<" ";
		cout<<"Nam xuat ban: ";
		cin>>A[run][5];
		ofs<<A[run][5]<<" ";
		cout<<"So trang: ";
		cin>>A[run][6];
		ofs<<A[run][6]<<" ";
		cout<<"So ban copy: ";
		cin>>A[run][7];
		ofs<<A[run][7]<<" ";
		ofs<<endl;
		cout<<endl;
	}
	ofs.close();
}

int main()
{
	addBook();
	return 0;
}

