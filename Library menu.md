# Collapsed version of Library management menu(20 rows)
```cpp
#include <iostream>
#include <string>
using namespace std;
int main() {int option, n, level=0, index;string checker;cout << "Enter number of books: ";cin >> n;string* Book_tittles = new string[n];string* Authors = new string[n];char* Status = new char[n];int* Year = new int[n];
	do {
		cout << "\n\n====== LIBRARY MANAGEMENT MENU ======\n";cout << "1. Add Book\n2. Display all Records\n3. Delete Book\n4. Search Book by Authors\n5. Exit\nChoose an option(1-5): ";cin >> option;
		switch (option){
		case 1:
			if (level == n) {cout << "Storage is full, free it with deleting a book";}else if (level >= 0) {cout << "Enter book tittle: ";getline(cin >> ws, Book_tittles[level]);cout << "Enter author: ";getline(cin >> ws, Authors[level]);cout << "Enter publishing year: ";cin >> Year[level];cout << "Enter avaibility status(Y/N): ";cin >> Status[level];++level;if (Status[level-1] != 'N') {if (Status[level - 1] != 'Y') {cout << "Invalid data ,only 'Y' and 'N' are avaible. try again";--level;Book_tittles[level] = "";Authors[level] = "";Year[level] = 0;Status[level] = 0;}else cout << "Book was added successefully!";}else   cout << "Book was added successefully!";}else {cout << "Invalid data, try again!";}break;
		case 2:
			cout << "\n==== ALL BOOK RECORDS ====\n";for (int i = 0; i < level; i++) {cout << "Index: " << i << "\nTittle: " << Book_tittles[i] << "\nAuthor: " << Authors[i] << "\nPublication Year: " << Year[i] << "\nStatus: " << Status[i] << endl;cout << "------------\n";}break;
		case 3:
			cout << "Enter index to delete: ";cin >> index;if (index >= level) cout << "Invalid data, no item with this index ,try again";else {int count = index;for (index; index < level-1; index++) {Book_tittles[index] = Book_tittles[index + 1];}index = count;for (index; index < level-1; index++) {Authors[index] = Authors[index + 1];}index = count;for (index; index < level-1; index++) {Year[index] = Year[index + 1];}index = count;for (index; index < level-1; index++) {Status[index] = Status[index + 1];}index = count;level--;cout << "Deleted successefuly";}break;
		case 4:
			cout << "Enter author name to search: ";cin >> checker;cout << "Search result:\n";for (int i = 0; i < level; ++i) {
				if (Authors[i] == checker) {cout << "Index: " << i << "\nTittle: " << Book_tittles[i] << "\nAuthor: " << Authors[i] << "\nPublication Year: " << Year[i] << "\nStatus: " << Status[i] << endl;}else cout << "No book found";}break;
		case 5:
			cout << "Thank you, programme ended";delete[] Status;delete[] Book_tittles;delete[] Year;delete[] Authors;break;
		default:
			cout << "Incorrect input , try again!";break;}} while (option != 5);return 0;}
```
# Full version of code (107 rows)
```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
	int option, n, level=0, index;
	string checker;
	cout << "Enter number of books: ";
	cin >> n;
	string* Book_tittles = new string[n];
	string* Authors = new string[n];
	char* Status = new char[n];
	int* Year = new int[n];


	do {
		cout << "\n\n====== LIBRARY MANAGEMENT MENU ======\n";
		cout << "1. Add Book\n2. Display all Records\n3. Delete Book\n4. Search Book by Authors\n5. Exit\nChoose an option(1-5): ";
		cin >> option;
		switch (option){
		case 1:
			if (level == n) {
				cout << "Storage is full, free it with deleting a book";
			}
			else if (level >= 0) {
				cout << "Enter book tittle: ";
				getline(cin >> ws, Book_tittles[level]);
				cout << "Enter author: ";
				getline(cin >> ws, Authors[level]);
				cout << "Enter publishing year: ";
				cin >> Year[level];
				cout << "Enter avaibility status(Y/N): ";
				cin >> Status[level];
				++level;
				if (Status[level-1] != 'N') {
					if (Status[level - 1] != 'Y') {
						cout << "Invalid data ,only 'Y' and 'N' are avaible. try again";
						--level;
						Book_tittles[level] = "";
						Authors[level] = "";
						Year[level] = 0;
						Status[level] = 0;
					}
					else cout << "Book was added successefully!";
				}
				else   cout << "Book was added successefully!";
			}
			else {
				cout << "Invalid data, try again!";
			}
			break;

		case 2:
			cout << "\n==== ALL BOOK RECORDS ====\n";
			for (int i = 0; i < level; i++) {
				cout << "Index: " << i << "\nTittle: " << Book_tittles[i] << "\nAuthor: " << Authors[i] << "\nPublication Year: " << Year[i] << "\nStatus: " << Status[i] << endl;
				cout << "------------\n";
			}
			break;

		case 3:
			cout << "Enter index to delete: ";
			cin >> index;
			if (index >= level) cout << "Invalid data, no item with this index ,try again";
			else {
				int count = index;
				for (index; index < level-1; index++) {
					Book_tittles[index] = Book_tittles[index + 1];
				}
				index = count;
				for (index; index < level-1; index++) {
					Authors[index] = Authors[index + 1];
				}
				index = count;
				for (index; index < level-1; index++) {
					Year[index] = Year[index + 1];
				}
				index = count;
				for (index; index < level-1; index++) {
					Status[index] = Status[index + 1];
				}
				index = count;
				level--;
				cout << "Deleted successefuly";
			}
			break;

		case 4:
			cout << "Enter author name to search: ";
			cin >> checker;
			cout << "Search result:\n";
			for (int i = 0; i < level;++i) {
				if (Authors[i] == checker) {
					cout << "Index: " << i << "\nTittle: " << Book_tittles[i] << "\nAuthor: " << Authors[i] << "\nPublication Year: " << Year[i] << "\nStatus: " << Status[i] << endl;
				}
				else cout << "No book found";
			}
			break;

		case 5:
			cout << "Thank you, programme ended";
			delete[] Status;
			delete[] Book_tittles;
			delete[] Year;
			delete[] Authors;
			break;

		default:
			cout << "Incorrect input , try again!";
			break;
		}
	} while (option != 5);
	return 0;}
```
