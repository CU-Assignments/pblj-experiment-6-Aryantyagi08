[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/pAwhWXY5)
import java.util.ArrayList;
import java.util.Collections;
import java.util.Comparator;
import java.util.Scanner;

class Employee {
    int id;
    String name;
    double salary;

    // Constructor
    public Employee(int id, String name, double salary) {
        this.id = id;
        this.name = name;
        this.salary = salary;
    }

    // Display Employee details
    public void displayEmployee() {
        System.out.println("ID: " + id + ", Name: " + name + ", Salary: " + salary);
    }

    // Getters for Employee attributes
    public int getId() {
        return id;
    }

    public String getName() {
        return name;
    }
}

public class EmployeeList {
    // List to store employees
    static ArrayList<Employee> employees = new ArrayList<>();

    // Method to add an employee to the list
    public static void addEmployee(int id, String name, double salary) {
        Employee employee = new Employee(id, name, salary);
        employees.add(employee);
    }

    // Method to display all employees
    public static void displayEmployees() {
        if (employees.isEmpty()) {
            System.out.println("No employees found.");
        } else {
            System.out.println("\nEmployee List:");
            for (Employee emp : employees) {
                emp.displayEmployee();
            }
        }
    }

    // Method to sort employees by ID
    public static void sortEmployeesById() {
        Collections.sort(employees, Comparator.comparingInt(Employee::getId));
    }

    // Method to search for an employee by name
    public static void searchEmployeeByName(String name) {
        boolean found = false;
        for (Employee emp : employees) {
            if (emp.getName().equalsIgnoreCase(name)) {
                emp.displayEmployee();
                found = true;
                break;
            }
        }
        if (!found) {
            System.out.println("Employee not found.");
        }
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int choice;

        do {
            // Displaying menu
            System.out.println("\nEmployee Management System");
            System.out.println("1. Add Employee");
            System.out.println("2. Display Employees");
            System.out.println("3. Sort Employees by ID");
            System.out.println("4. Search Employee by Name");
            System.out.println("5. Exit");
            System.out.print("Enter your choice: ");
            choice = scanner.nextInt();

            switch (choice) {
                case 1: // Add Employee
                    System.out.print("Enter Employee ID: ");
                    int id = scanner.nextInt();
                    scanner.nextLine();  // Consume newline
                    System.out.print("Enter Employee Name: ");
                    String name = scanner.nextLine();
                    System.out.print("Enter Employee Salary: ");
                    double salary = scanner.nextDouble();
                    addEmployee(id, name, salary);
                    System.out.println("Employee added successfully!");
                    break;

                case 2: // Display Employees
                    displayEmployees();
                    break;

                case 3: // Sort Employees by ID
                    sortEmployeesById();
                    System.out.println("Employees sorted by ID.");
                    break;

                case 4: // Search Employee by Name
                    scanner.nextLine(); // Consume newline
                    System.out.print("Enter Employee Name to search: ");
                    String searchName = scanner.nextLine();
                    searchEmployeeByName(searchName);
                    break;

                case 5: // Exit
                    System.out.println("Exiting the program.");
                    break;

                default:
                    System.out.println("Invalid choice. Please try again.");
            }

        } while (choice != 5);

        scanner.close();
    }
}
