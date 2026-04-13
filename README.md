#include <stdio.h>

#define MAX 100

// Structure to store employee details
struct Employee {
    int id;
    char name[50];
    float basic, hra, da, deduction, netSalary;
};

struct Employee emp[MAX];
int count = 0;

// Function to add employee
void addEmployee() {
    printf("\nEnter Employee ID: ");
    scanf("%d", &emp[count].id);

    printf("Enter Name: ");
    scanf("%s", emp[count].name);

    printf("Enter Basic Salary: ");
    scanf("%f", &emp[count].basic);

    printf("Enter HRA: ");
    scanf("%f", &emp[count].hra);

    printf("Enter DA: ");
    scanf("%f", &emp[count].da);

    printf("Enter Deductions: ");
    scanf("%f", &emp[count].deduction);

    // Calculate Net Salary
    emp[count].netSalary = emp[count].basic + emp[count].hra + emp[count].da - emp[count].deduction;

    count++;
    printf("\nEmployee Added Successfully!\n");
}

// Function to display employees
void displayEmployee() {
    if (count == 0) {
        printf("\nNo Employee Records Found!\n");
        return;
    }

    printf("\nEmployee Details:\n");
    for (int i = 0; i < count; i++) {
        printf("\nID: %d", emp[i].id);
        printf("\nName: %s", emp[i].name);
        printf("\nBasic Salary: %.2f", emp[i].basic);
        printf("\nHRA: %.2f", emp[i].hra);
        printf("\nDA: %.2f", emp[i].da);
        printf("\nDeductions: %.2f", emp[i].deduction);
        printf("\nNet Salary: %.2f\n", emp[i].netSalary);
    }
}

// Function to search employee by ID
void searchEmployee() {
    int id, found = 0;
    printf("\nEnter Employee ID to search: ");
    scanf("%d", &id);

    for (int i = 0; i < count; i++) {
        if (emp[i].id == id) {
            printf("\nEmployee Found:\n");
            printf("Name: %s\n", emp[i].name);
            printf("Net Salary: %.2f\n", emp[i].netSalary);
            found = 1;
            break;
        }
    }

    if (!found) {
        printf("\nEmployee Not Found!\n");
    }
}

// Main function
int main() {
    int choice;

    while (1) {
        printf("\n--- Employee Salary Management System ---\n");
        printf("1. Add Employee\n");
        printf("2. Display Employees\n");
        printf("3. Search Employee\n");
        printf("4. Exit\n");

        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1:
                addEmployee();
                break;
            case 2:
                displayEmployee();
                break;
            case 3:
                searchEmployee();
                break;
            case 4:
                printf("\nExiting Program...\n");
                return 0;
            default:
                printf("\nInvalid Choice!\n");
        }
    }

    return 0;
}
