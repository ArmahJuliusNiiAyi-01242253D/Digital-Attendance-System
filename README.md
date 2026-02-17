#include <iostream>
#include <vector>
#include <string>

class Student {
public:
    std::string indexNumber;
    std::string name;

    Student(std::string idx, std::string n) : indexNumber(idx), name(n) {}

    void display() {
        std::cout << "Index: " << indexNumber << ", Name: " << name << "\n";
    }
};

std::vector<Student> students;

void addStudent() {
    std::string idx, name;
    std::cout << "Enter Index Number: ";
    std::cin >> idx;
    std::cin.ignore(); // ignore leftover newline
    std::cout << "Enter Name: ";
    std::getline(std::cin, name);

    if (idx.empty() || name.empty()) {
        std::cout << "Invalid input. Please try again.\n";
        return;
    }

    students.emplace_back(idx, name);
    std::cout << "Student added successfully!\n";
}

void viewStudents() {
    if (students.empty()) {
        std::cout << "No students registered yet.\n";
        return;
    }
    for (auto& s : students)
        s.display();
}

int main() {
    int choice;
    do {
        std::cout << "\n--- Digital Attendance System ---\n";
        std::cout << "1. Add Student\n2. View Students\n3. Exit\n";
        std::cout << "Enter choice: ";
        std::cin >> choice;

        switch (choice) {
            case 1: addStudent(); break;
            case 2: viewStudents(); break;
            case 3: std::cout << "Exiting...\n"; break;
            default: std::cout << "Invalid choice. Please try again.\n";
        }
    } while (choice != 3);

    return 0;
}
