# Colapsed verion of Students list to add, delete, insert students, sort by id in asdending order, display whole list and finally exit(28 rows)
```cpp
#include <iostream>
using namespace std;
int arr[10];
int counter = 0;
void Add_Student(int id) {arr[counter-1] = id;}
void Delete_Student(int index) {for (index; index < counter-1; index++) {arr[index] = arr[index+1];}counter--;cout << "Deleted successefuly";}
void Insert_Student(int id, int pos) {int counter1 = counter;for (counter1; pos <= counter1; counter1--) {arr[counter1] = arr[counter1 - 1];}arr[pos -1 ] = id;}
void Search_Student(int id, int index) {if (id == arr[index]) cout << "Student in " << index + 1 << " position ,  and under " << index << " index";else if (index+1 == counter) cout << "No student with this ID\nYou can add student if choose '1' or '2' options ";else {index++;Search_Student(id, index);}}
void Sort_Students() {for (int i = 0; i < counter - 1; i++) {int minIndex = i;for (int j = i + 1; j < counter; j++) {if (arr[j] < arr[minIndex]) {minIndex = j;}}int temp = arr[i];arr[i] = arr[minIndex];arr[minIndex] = temp;}}
int main() {int choice1, id, position;
	do {int index = 0;cout << "\n\n========Student ID Manager========\n";cout << "1.Add Student\n2.Insert Student\n3.Delete Student\n4.Search Student\n5.Sort by ID\n6.Display All Students\n7.Exit";cout << "\n\nChoose option: ";cin >> choice1;switch (choice1) {
		case 1:
			counter++;if (counter == 11) {cout << "List of students is already full.\nHint: Delete one of students whom you don't like\n";counter--;}else {cout << "Enter student ID(max 10 students): ";cin >> id;if (id == 0) cout << "Incorrect ID, 0 is not allowed, please try again\n";else {Add_Student(id);cout << "Student added successefully";}}break;
		case 2:
			if (counter == 11) {cout << "List of students is already full.\nHint: Delete one of students whom you don't like\n";}else {counter++;cout << "Enter ID: ";cin >> id;cout << "Enter position (1-10): ";cin >> position;Insert_Student(id, position);cout << "Inserted successefuly\n";break;}
		case 3:
			cout << "Enter index to delete: ";cin >> index;if (index > counter - 1)cout << "No Student under this index, please try again.\n";else Delete_Student(index);break;
		case 4:
			cout << "Enter student ID to search: ";cin >> id;Search_Student(id, index);break;
		case 5:
			Sort_Students();cout << "Sorted successefuly";break;
		case 6:
			cout << "List of students with their position(not index): ";for (int i = 0; i < counter; i++) {cout << endl << i + 1 << " Student ID: " << arr[i] << "\t\t|Index: " << i;}break;
		case 7:
			cout << "Program executed! ";break;
		default:
			cout << "Incorrect option! Choose only from 1 to 7";}
	} while (choice1 != 7);return 0;}
```

# More detailed version(122 rows)
```cpp
#include <iostream>
using namespace std;
int arr[10];  // arr[10] gives limit in 10 students . Global locations gives easy access to modify array
int  counter = 0;  // counter maximum value is 10

void Add_Student(int id) {
	arr[counter-1] = id;
}
void Delete_Student(int index) {
	for (index; index < counter-1; index++) {
		arr[index] = arr[index+1];
	}
	counter--;
	cout << "Deleted successefuly";

}
void Insert_Student(int id, int pos) {
	int counter1 = counter;
	for (counter1; pos <= counter1; counter1--) {
		arr[counter1] = arr[counter1 - 1];
	}
	arr[pos -1 ] = id;
}
void Search_Student(int id, int index) {
	if (id == arr[index]) cout << "Student in " << index + 1 << " position ,  and under " << index << " index";
	else if (index+1 == counter) cout << "No student with this ID\nYou can add student if choose '1' or '2' options ";
	else {index++;Search_Student(id, index);}
}
void Sort_Students() {
	for (int i = 0; i < counter - 1; i++) {
		int minIndex = i;
		for (int j = i + 1; j < counter; j++) {
			if (arr[j] < arr[minIndex]) {
				minIndex = j;
			}
		}
		int temp = arr[i];
		arr[i] = arr[minIndex];
		arr[minIndex] = temp;
	}
}




int main() {
	int choice1, id, position;

	do {
		int index = 0;
		cout << "\n\n========Student ID Manager========\n";
		cout << "1.Add Student\n2.Insert Student\n3.Delete Student\n4.Search Student\n5.Sort by ID\n6.Display All Students\n7.Exit";
		cout << "\n\nChoose option: ";
		cin >> choice1;
		switch (choice1) {
		case 1: // Adding student case (maximum 10) (Comlpeted)
			counter ++;
			if (counter == 11) {
				cout << "List of students is already full.\nHint: Delete one of students whom you don't like\n";
				counter--;
			} // this if/else creates maximum of students

			else {
				cout << "Enter student ID(max 10 students): ";
				cin >> id;
				if (id == 0) cout << "Incorrect ID, 0 is not allowed, please try again\n";
				else {
					Add_Student(id);
					cout << "Student added successefully";
				}
			}
			break;

		case 2: // Insert Student by ID (Completed)
			if (counter == 11) {
				cout << "List of students is already full.\nHint: Delete one of students whom you don't like\n";
			}
			else {
				counter++;
				cout << "Enter ID: ";
				cin >> id;
				cout << "Enter position (1-10): "; // Made by position on purpose, because in real life people search with position not by index
				cin >> position;
				Insert_Student(id , position);
				cout << "Inserted successefuly\n";
				break;
			}
		case 3: // Delete student (Completed)
			cout << "Enter index to delete: ";
			cin >> index;
			if (index > counter - 1)cout << "No Student under this index, please try again.\n";
			else Delete_Student(index);
			break;

		case 4: // Search student (Completed)
			cout << "Enter student ID to search: ";
			cin >> id;
			Search_Student(id, index);

			break;
		case 5: // Sort by ID (Completed)
			Sort_Students();
			cout << "Sorted successefuly";
			break;

		case 6:// Display all students by one (Comlpeted)
			cout << "List of students with their position(not index): "; // Shows by position like a real life list of students
			for (int i = 0; i < counter; i++) {
				cout << endl << i + 1<<" Student ID: " << arr[i] << "\t\t|Index: " << i;
			}
			break;

		case 7: // Executes program (Completed)
			cout << "Program executed! ";
			break;
		default:
			cout << "Incorrect option! Choose only from 1 to 7";
		}
	} while (choice1 != 7);
	
	return 0;
}
```
