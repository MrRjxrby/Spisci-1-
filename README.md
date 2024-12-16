# Spisci-1-
# Задание 1.1
```
class Student {
    private String name;
    private int age;
    private int course;

    // Конструктор
    public Student() {
        this.name = "";
        this.age = 0;
        this.course = 0;
    }

    public void readAttributes() { // Считывание данных
        Scanner scanner = new Scanner(System.in);
        System.out.print("Введите имя студента: ");
        this.name = scanner.nextLine();
        System.out.print("Введите возраст студента: ");
        this.age = scanner.nextInt();
        System.out.print("Введите курс студента: ");
        this.course = scanner.nextInt();
    }

    public void displayAttributes() { // Вывод данных
        System.out.println("Имя студента: " + this.name);
        System.out.println("Возраст студента: " + this.age);
        System.out.println("Курс студента: " + this.course);
    }
}

public class Main {
    public static void main(String[] args) {
        Student student = new Student();
        student.readAttributes();
        student.displayAttributes();
    }
}
```
# Задание 1.2
```
import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;

class Student {
    private String name;
    private int age;
    private int course;

    public Student(String name, int age, int course) {
        this.name = name;
        this.age = age;
        this.course = course;
    }

    public void displayAttributes() {
        System.out.println("Имя студента: " + name);
        System.out.println("Возраст студента: " + age);
        System.out.println("Курс студента: " + course);
    }
}

class Group {
    private List<Student> students;

    public Group() { // Пустой список
        students = new ArrayList<>();
    }

    // Добавление узла списка
    public void addStudent(Student student) {
        students.add(student);
    }

    // Удаление элемента узла
    public boolean removeStudent(Student student) {
        return students.remove(student);
    }

    // Вывод элементов списка
    public void displayStudents() {
        if (isEmpty()) {
            System.out.println("Список студентов пуст.");
            return;
        }
        for (Student student : students) {
            student.displayAttributes();
            System.out.println("-----------------------");
        }
    }

    // Очистка списка
    public void clear() {
        students.clear();
    }

    // Проверка списка на пустоту
    public boolean isEmpty() {
        return students.isEmpty();
    }
}

public class Main {
    public static void main(String[] args) {
        Group group = new Group();
        Scanner scanner = new Scanner(System.in);

        for (int i = 0; i < 3; i++) {  // Добавление информации о трёх студентах.
            System.out.println("Введите информацию о студенте " + (i + 1) + ":");
            System.out.print("Имя: ");
            String name = scanner.nextLine();

            System.out.print("Возраст: ");
            int age = scanner.nextInt();
            System.out.print("Курс: ");
            int course = scanner.nextInt();
            scanner.nextLine(); 

            group.addStudent(new Student(name, age, course));
        }

        // Вывод списка
        System.out.println("Список студентов:");
        group.displayStudents();
        
        // Очистка списка
        group.clear();
        System.out.println("Список после очистки:");
        System.out.println("Пустой: " + group.isEmpty());
    }
}
```
#Задание 1.3
```
import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;

class Student {
    private String name;
    private int age;
    private int course;

    public Student(String name, int age, int course) {
        this.name = name;
        this.age = age;
        this.course = course;
    }

    public void displayAttributes() {
        System.out.println("Имя студента: " + name);
        System.out.println("Возраст студента: " + age);
        System.out.println("Курс студента: " + course);
    }
}

class Group {
    private List<Student> students;

    public Group() {
        students = new ArrayList<>();
    }

    // Функция добавления узла списка
    public void addStudent(Student student) {
        students.add(student);
    }

    // Удаление элемента из списка
    public boolean removeStudent(Student student) {
        return students.remove(student);
    }

    // Вывод списка студентов
    public void displayStudents() {
        if (isEmpty()) {
            System.out.println("Список студентов пуст.");
            return;
        }
        for (Student student : students) {
            student.displayAttributes();
            System.out.println("-----------------------");
        }
    }

    // Очистка списка
    public void clear() {
        students.clear();
    }

    // ПРоверка списка на пустоту
    public boolean isEmpty() {
        return students.isEmpty();
    }
}

public class Main { // Класс Тестер
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Group group = new Group();
        int x;

        do {
            System.out.println("Меню:");
            System.out.println("1. Добавить студента");
            System.out.println("2. Удалить студента");
            System.out.println("3. Показать студентов");
            System.out.println("4. Очистить список");
            System.out.println("5. Проверить, пуст ли список");
            System.out.println("0. Выход");
            System.out.print("Ваш выбор: ");
            x = scanner.nextInt();
        scanner.nextLine(); 

        switch (x) {
            case 1: 
                System.out.print("Имя студента: ");
                String name = scanner.nextLine();
                System.out.print("Возраст студента: ");
                int age = scanner.nextInt();
                System.out.print("Курс студента: ");
                int course = scanner.nextInt();
                scanner.nextLine(); 
            group.addStudent(new Student(name, age, course));
                System.out.println("Студент добавлен.");
            break;

        case 2:
            System.out.print("Введите имя студента для удаления: ");
            String removeName = scanner.nextLine();
            int removeAge, removeCourse;
            System.out.print("Введите возраст студента для удаления: ");
            removeAge = scanner.nextInt();
            System.out.print("Введите курс студента для удаления: ");
            removeCourse = scanner.nextInt();
            scanner.nextLine();

            Student studentToRemove = new Student(removeName, removeAge, removeCourse);
            if (group.removeStudent(studentToRemove)) {
                System.out.println("Студент удален.");
            } else {
                System.out.println("Студент не найден.");
            }
            break;

        case 3:
            group.displayStudents();
            break;

        case 4:
            group.clear();
            System.out.println("Список очищен.");
            break;

        case 5:
            if (group.isEmpty()) {
                System.out.println("Список пуст.");
            } else {
                System.out.println("Список не пуст.");
            }
            break;

        case 0:
            System.out.println("Выход из программы...");
            break;
        }
    } while (x != 0);

    scanner.close();
    }
}
```
Задание 2(Структура данных - Кольцевой Список)
Файл LinkedList
```
package com.mycompany.list2;

class LinkedList {
    private Student head;

    public LinkedList() {
        this.head = null;
    }

    // Метод добавления студента
    public void addStudent() {
        Student newStudent = new Student();
        newStudent.inputAttributes(); 
        if (head == null) {
            head = newStudent; 
        } else {
            Student current = head;
            while (current.next != null) { 
                current = current.next;
            }
            current.next = newStudent; 
            newStudent.prev = current; 
        }
    }

    public void displayStudents() {
        if (head == null) {
            System.out.println("No students in the list.");
            return;
        }
        Student current = head;
        while (current != null) {
            current.displayAttributes(); 
            current = current.next; 
        }
    }
}
```
файл Student
```
package com.mycompany.list2;

import java.util.Scanner;

class Student {
    String name;
    int age;
    String group;
    String performance;
    Student prev;
    Student next;

    public Student() {
        this.name = null;
        this.age = 0;
        this.group = null;
        this.performance = null;
        this.prev = null;
        this.next = null;
    }

    public void inputAttributes() {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter student's name: ");
        this.name = scanner.nextLine();
        System.out.print("Enter student's age: ");
        this.age = scanner.nextInt();
        scanner.nextLine(); 
        System.out.print("Enter student's group: ");
        this.group = scanner.nextLine();
        System.out.print("Enter performance (Excelent/Good/Bad/Very Bad): ");
        this.performance = scanner.nextLine();
    }

    public void displayAttributes() {
        System.out.println(
            "Name: " + this.name +
            ", Age: " + this.age +
            ", Group: " + this.group +
            ", Performance: " + this.performance
        );
    }
}
```
Основной файл с (main):
```
package com.mycompany.list2;

import java.util.Scanner;

public class List2 {
    public static void main(String[] args) {
        LinkedList studentList = new LinkedList();
        Scanner scanner = new Scanner(System.in);

        while (true) {
            System.out.println("1. Add Student");
            System.out.println("2. Print All Students");
            System.out.println("3. Quit");
            System.out.print("Choose variant of action: ");
            int choice = scanner.nextInt();
            scanner.nextLine(); // Очистка буфера после ввода числа

            switch (choice) {
                case 1 -> {
                    studentList.addStudent(); 
                }
                case 2 -> {
                    studentList.displayStudents(); 
                }
                case 3 -> {
                    System.out.println("Exiting program...");
                    scanner.close();
                    return; // Завершение программы
                }
                default -> System.out.println("Invalid option. Try again.");
            }
        }
    }
}
```
