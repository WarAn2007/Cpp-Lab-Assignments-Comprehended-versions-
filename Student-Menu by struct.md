# Full version (184 rows)
```cpp
#include <iostream>
#include <string>
using namespace std;

struct Student{ //Structure to contain fata of students
	int id;
	string name,faculty,contact;
	double gpa;
};
void AddStudent(Student student[], int &Count){ // adding student function
	Count ++;
	if(Count <= 10){
		cout << "----Add Student----\nEnter full name: ";
		getline(cin >> ws, student[Count-1].name);
		cout << "Enter ID: ";
		cin >> student[Count-1].id;
		cout << "Enter faculty: ";
		getline(cin >> ws, student[Count-1].faculty);
		cout << "Enter gpa(0.0-4.0): ";
		cin >> student[Count-1].gpa;
		while(student[Count-1].gpa < 0.0 || student[Count-1].gpa > 4.0){
			cout << "Inalid data, try again!\nEnter gpa(0.0-4.0): ";
			cin.clear();cin.ignore();
			cin >> student[Count-1].gpa;
		}
		cout << "Enter contact(number, email): ";
		cin >> student[Count-1].contact;
		cout << "Student added successefuly!\n";
	}
	else {cout << "Too many students(max = 10), free some space to enter another student!\n"; Count--;}
}
void Display(const Student student[], int Count){ //display all records of students
	if(Count < 1)cout << "No students to display, enter them first\n";
	else {
		cout << "------ Students Records ------\n";
		cout << "ID\tName\t\tFaculty\t\tGPA\tContact";
		for(int i = 0; i < Count; i++){
			cout << endl<< student[i].id << "\t" << student[i].name << "\t\t" << student[i].faculty << "\t\t" << student[i].gpa << "\t" << student[i].contact;
		}
	}
}
void FoundS(const Student student[], int i){ // displays students found in Search func
	cout << "---------\n";
	cout << "Founded: \nID: "<< student[i].id << "\nName: "<< student[i].name << "\nFaculty: " << student[i].faculty << "\nGPA: " << student[i].gpa << "\nContact: " << student[i].contact;
	cout << "\n---------\n";
}
void Search(const Student student[], int Count){ 
	int option,idsearch;
	string namesearch;
	bool found = false;// Search function by ID or Name
	if (Count == 0) cout << "No students entered to search, enter data first\n";
			else{
				cout << "---- Search Operation ----\n1. Search by ID\n2. Search by Name\nEnter an option: ";
				cin >> option;
				switch(option){
					case 1:
						cout << "Enter ID to Search: ";
						cin >> idsearch;
						for(int i = 0; i < Count; i++){
							if(student[i].id == idsearch){
								found = true;
								FoundS(student, i);
						break;
							}
						}
						if(found == false) cout << "No students were found with this ID";
						break;
					case 2:
						cout << "Enter Name to Search: ";
						cin >> namesearch;
						for(int i = 0; i < Count; i++){
						if(student[i].name == namesearch){
							found = true;
							FoundS(student,i);
							break;
						}
						}
						if(found == false) cout << "No students were found with this Name";
						break;
					default:
						cout << "Invalid Option! Please try again!\n";
						break;
				}
			}
}
void UpdateS(Student student[], int Count){ // Update information of Student
	int id,option,position;
	bool found = false;
	cout << "---- Update Data ----\nEnter ID to search student: ";
	cin >> id;
	for(int i = 0; i < Count; i++){
		if(student[i].id == id){
			found = true;
			FoundS(student, i);
			cout << "\nWhich you want to change: \n1. Name\n2. Faculty\n3. GPA\n4. Contact\n5. Finish Updating\nOption: ";
			cin >> option;
			switch (option){
			case 1:
				cout << "Enter Name to change: ";
				getline(cin >> ws, student[i].name);
				break;
			case 2:
				cout << "Enter Faculty to change: ";
				getline(cin >> ws, student[i].faculty);
				break;
			case 3:
				cout << "Enter gpa(0.0-4.0): ";
				cin >> student[i].gpa;
				while(student[Count].gpa < 0.0 || student[Count].gpa > 4.0){
					cout << "Inalid data, try again!\nEnter gpa(0.0-4.0): ";
					cin.clear();cin.ignore();
					cin >> student[Count].gpa;
				}
				break;
			case 4:
				cout << "Enter contact(number, email): ";
				cin >> student[Count].contact;
				break;
			case 5:
				break;
			default:
				cout << "Invalid option, try again!\n";
				break;
			} // end of switch statement
			if(option <=5 && option>0) cout << "Student Updated successefuly!\n";
				break; // stops checking other students when find one
			}
	}
	if(found == false) cout << "Student not Found\n";
}
void DeleteS(Student student[], int &Count){ // Delete Student by ID
	int id;
	bool found = false;
	cout << "Enter Student's ID to delete: ";
	cin >> id;
	for(int i = 0; i <= Count; i++){
		if(id == student[i].id){
			found = true;
			for (int j = i; j < Count-1; j++) {
				student[j].id = student[j+1].id;
				student[j].name = student[j+1].name;
				student[j].faculty = student[j+1].faculty;
				student[j].gpa = student[j+1].gpa;
				student[j].contact = student[j+1].contact;
			}
			Count --;
			cout << "Student Deleted Successefuly\n";
			break;
		}
	}
	if(found == false) cout << "Student not Found\n";
}
int main() {
	int option, countdown = 0;
	Student freshmen[10]; // Declaring that 10 students are limit of data base. Also 
	do{
		cout << "\n===================\n\tDATA BASE MENU\n===================\n";
		cout << "1. Add Student\n2. Dispay All\n3. Search for a Student\n4. Update Student Info\n5. Delete Student\n6. Exit";
		cout << "\n-------------------\nEnter option: ";
		cin >> option;
		switch (option){
		case 1: //Adding Student to data (completed)
			AddStudent(freshmen, countdown);
			break;
		case 2: // Displaying all Students  (completed)
			Display(freshmen, countdown);
			break;
		case 3: // Searching for exact student by ID or Name (completed)
			Search(freshmen,countdown);
			break;
		case 4: // Update information about student (completed)
			UpdateS(freshmen,countdown);
			break;
		case 5: // Execute student 💀(completed)
			DeleteS(freshmen, countdown);
			break;
		case 6: // Executing programm (completed)
			cout << "Goodbye, leave a tip for worker XXXX XXXX XXXX XXXX";
			break;
		default: // Invalid Input Reaction (completed)
			cout << "Invalid Option! Please try again!\n";
			break;
		}
	}while(option !=6);
	return 0;
}
```
