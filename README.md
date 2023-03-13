# Java
## OOP 
Object Oriented Programming is a paradigm (way of programming) that allows us to model real world objects as software objects. This is done by using classes and objects. **Classes are the blueprint** for the object. **Objects are the instances of the class**. A class can be defined as a collection of objects. It is a logical entity that has some specific **attributes** and **methods**. For example, a dog is an object. Dog is an instance of the class Animal. A class Animal can have attributes like color, breed, legs etc. and methods like walk, eat, bark etc.

- Abstraction: Hiding the internal details and showing only functionality.
- Encapsulation: Binding the data and the functions that manipulate them.
- Inheritance: A way to form new classes using classes that have already been defined.
- Polymorphism: The process of using an operator or function in different ways for different data input.

## Class
A class is a user-defined blueprint or prototype from which objects are created. It represents the set of properties or methods that are common to all objects of one type.

## Object
An object is a unique instance of a data structure that's defined by its class. An object comprises both data members (class variables and instance variables) and methods. Instance is the representation of the object of a class. An object obj that belongs to a class Circle, for example, is an instance of the class Circle.

## Constructor
A constructor is a special type of method (function) which is used to initialize the instance members of the class. It is called when an object of a class is created. It can be used to set initial values for object attributes.

## Method
A method is a function that is associated with an object. In Python, a method is not unique to class instances. Any object type can have methods.

## Encapsulation
Encapsulation is the process of wrapping code and data together into a single unit. In encapsulation, the variables or data of a class is hidden from any other class and can be accessed only through any member function of own class in which they are declared. To achieve encapsulation in Java − Declare the variables of a class as private. to make them accessible only within the class. Provide public `setter` and `getter` methods to modify and view the variables values.

## Methods (Behaviors)

-`constructor` : This is a special method, which is called class constructor or initialization method that Python calls when you create a new instance of this class.

## this
The `this` keyword is a reference to the current instance of the class, and is used to access variables that belong to the class.

## Null pointer exception
A null pointer exception is an exception that occurs when an application attempts to use an object reference that has the value null. A null reference is a reference that does not refer to any object. It is a common error in Java programming.

```java
// Account.java
public class Account {
    private User user; // reference to User object is null
    private String password;
}
```

```java
// User.java
public class User {
    private String name;
    private String email;
    private String phone;
}
```

```java
// Main.java
public class Main {
    public static void main(String[] args) {
        Account account = new Account();
        account.user.name = "Annie"; // NullPointerException
    }
}
```

### How to fix it?
```java
// Account.java
public class Account {
    private User user;
    private String password;

    public Account() {
        user = new User(); // initialize user
    }
}
```
## Constructor
A constructor is a special method that is used to initialize objects. The constructor is called when an object of a class is created. It can be used to set initial values for object attributes.

```java
public class Car {
    private String make;
    private String model;
    private int year;

    public Car(String make, String model, int year) {
        this.make = make;
        this.model = model;
        this.year = year;
    }
}
```
The constructor above is a parameterized constructor because it takes parameters. If a class does not have a constructor, then Java compiler creates a default constructor for that class. The default constructor does not have any parameters. If you create your own constructor, then the default constructor is not created. You can have as many constructors as you want in a class by method overloading. The only requirement is that the constructor name must be the same as the class name. The constructor can also be overloaded by the number and type of parameters. The constructor can also be overloaded by the access modifier. The constructor can also be overloaded by the type of exception thrown. The constructor forces the programmer to initialize the object by passing the required parameters. It is a good practice to initialize the object using constructor.

## Static
Static is a keyword in Java which is used for memory management mainly. We can apply Java static keyword with variables, methods, blocks and nested class. The static keyword belongs to the class than an instance of the class. **A static member belongs to the class as a whole rather than to a specific object**. It makes no sense to talk about non-static variables here because non-static variables are instance variables and instance variables are always associated with an object.

### Static variable
A static variable is a variable which is declared as static. It can be accessed without instantiating its class. A static variable is shared by all the instances of the class. Memory allocation for static variable happens only once when the class is loaded in the memory.

### Static method
A static method belongs to the class rather than object of a class. A static method can be invoked without the need for creating an instance of a class. A static method can access static data member and can change the value of it.

### Static block
A static block is used for initializing the static data member. It is executed before the main method at the time of classloading.

```java
public class StaticBlock {
    private static int count;
    private static int num;
    private static String mystr;
    // static block
    static {
        count = 0;
        num = 97;
        mystr = "Static keyword in Java";
    }

    public static int getCount() {
        return StaticBlock.count;
    }
    // main method
    public static void main(String args[]) {
        System.out.println("Value of num: "+num);
        System.out.println("Value of mystr: "+mystr);
    }
}
```

## Inheritance
Inheritance is a mechanism in which one object acquires all the properties and behaviors of a parent object. It is an important part of OOPs (Object Oriented programming system). It provides code reusability. It is used to achieve runtime polymorphism.
```java
class A {
    private int age;
    public void getAge() {
        return age;
    }
}

class B extends A {
    public String describe() {
        return "Class' B objects is " + super.getAge() + " years old.";
    }
}
```

## Polymorphism
Polymorphism means "many forms", and it occurs when we have many classes that are related to each other by inheritance. Like we specified in the previous chapter; Inheritance lets us inherit attributes and methods from another class. Polymorphism uses those methods to perform different tasks. This allows us to perform a single action in different ways.

```java
class Animal {
    public void animalSound() {
        System.out.println("The animal makes a sound");
    }
}

```

```java
// BankAccount.java
public class BankAccount {
    private String accountNumber;
    private double balance;

    public BankAccount(String accountNumber, double balance) {
        this.accountNumber = accountNumber;
        this.balance = balance;
    }

    public void deposit(double amount) {
        this.balance += amount;
    }

    public void withdraw(double amount) {
        if (amount <= getBalance()) {
            this.balance -= amount;
        }
    }

    public double getBalance() {
        return balance;
    }
}
```

```java
// SavingsAccount.java
public class SavingsAccount extends BankAccount {
    private double interestRate;

    public SavingsAccount(String accountNumber, double balance, double interestRate) {
        super(accountNumber, balance);
        this.interestRate = interestRate;
    }

    public void addInterest() {
        double interest = getBalance() * interestRate / 100;
        deposit(interest);
    }

    @Override // override withdraw method
    public void withdraw(double amount) {
        double fee = 0.01;
        super.withdraw(amount + fee);
    }
}
```

```java
// CheckingAccount.java
public class CheckingAccount extends BankAccount {
    private double fee;

    public CheckingAccount(String accountNumber, double balance, double fee) {
        super(accountNumber, balance);
        this.fee = fee;
    }

    public void deductFee() {
        withdraw(fee);
    }
}
```
## Abstract class
An abstract class is a restricted class that cannot be used to create objects (to access it, it must be inherited from another class). To access an abstract class, it must be inherited from another class, providing the body of the abstract methods in the child class. Abstract classes are often used to provide a common template for subclasses. Abstract classes can have abstract methods and non-abstract methods. Abstract methods are methods that do not have a body. They are declared using the abstract keyword and can only be used in an abstract class. Abstract classes are declared with the abstract keyword.

```java
// Staff.java
public abstract class Staff {
    private String name;
    private String address;
    private String phone;

    public Staff(String name, String address, String phone) {
        this.name = name;
        this.address = address;
        this.phone = phone;
    }

    public abstract double calculatePay();
}
```

```java
// HourlyStaff.java
public class HourlyStaff extends Staff {
    private double hourlyRate;
    private double hoursWorked;

    public HourlyStaff(String name, String address, String phone, double hourlyRate, double hoursWorked) {
        super(name, address, phone);
        this.hourlyRate = hourlyRate;
        this.hoursWorked = hoursWorked;
    }

    @Override
    public double calculatePay() {
        return hourlyRate * hoursWorked;
    }
}
```

```java
// SalariedStaff.java
public class SalariedStaff extends Staff {
    private double monthlySalary;

    public SalariedStaff(String name, String address, String phone, double monthlySalary) {
        super(name, address, phone);
        this.monthlySalary = monthlySalary;
    }

    @Override
    public double calculatePay() {
        return monthlySalary;
    }
}
```

```java
// Main.java

public class Main {
    public static void main(String[] args) {
        Staff[] staffs = new Staff[3];
        staffs[0] = new HourlyStaff("John", "123 Main St", "123-456-7890", 10, 40);
        staffs[1] = new HourlyStaff("Mary", "456 Main St", "123-456-7890", 15, 40);
        staffs[2] = new SalariedStaff("Bob", "789 Main St", "123-456-7890", 1000);

        for (Staff staff : staffs) {
            System.out.println(staff.calculatePay());
        }
    }
}
```

## Interface
An interface is a completely "abstract class" that is used to group related methods with empty bodies. To access the interface methods, the interface must be "implemented" (kinda like inherited) by another class with the **implements** keyword (instead of extends). The body of the interface method is provided by the "implement" class. On implementation of an interface, you must override all of its methods. Interface methods do not have a body - the body is provided by the "implement" class. On implementation of an interface, you must override all of its methods. Interface methods are by default abstract and public. Interface attributes are by default public, static and final. An interface cannot contain a constructor (as it cannot be used to create objects). Java does not support "multiple inheritance" (a class can only inherit from one superclass). However, it can be achieved with interfaces, because the class can implement multiple interfaces. Note: To implement multiple interfaces, separate them with a comma (see example below).


```java
// Authenticatable.java
public interface Authenticatable {
    public boolean authenticate(String username, String password);
}
```

```java
// User.java
public class User implements Authenticatable {
    private String username;
    private String password;

    public User(String username, String password) {
        this.username = username;
        this.password = password;
    }

    @Override
    public boolean authenticate(String username, String password) {
        return this.username.equals(username) && this.password.equals(password);
    }
}
```

```java
// Manager.java
public class Manager extends Staff implements Authenticatable {
    private String username;
    private String password;

    public Manager(String name, String address, String phone, double monthlySalary, String username, String password) {
        super(name, address, phone, monthlySalary);
        this.username = username;
        this.password = password;
    }

    @Override
    public boolean authenticate(String username, String password) {
        return this.username.equals(username) && this.password.equals(password);
    }
}
```

```java
// InternalSystem.java
public class InternalSystem {
    private Authenticatable[] users;

    public InternalSystem(Authenticatable[] users) {
        this.users = users;
    }

    public void login(String username, String password) {
        for (Authenticatable user : users) {
            if (user.authenticate(username, password)) {
                System.out.println("Login successful");
                return;
            }
        }
        System.out.println("Login failed");
    }
}
```

```java
// Main.java


```

**Hight cohesion and low coupling** are the two most important principles of OOPs. High cohesion means that the methods in a class are related to each other. Low coupling means that the classes are loosely coupled. In other words, the classes are independent of each other.

## Interface vs Abstract class
An interface is a completely "abstract class" that is used to group related methods with empty bodies. To access the interface methods, the interface must be "implemented" (kinda like inherited) by another class with the **implements** keyword (instead of extends). The body of the interface method is provided by the "implement" class. On implementation of an interface, you must override all of its methods. Interface methods do not have a body - the body is provided by the "implement" class. On implementation of an interface, you must override all of its methods. Interface methods are by default abstract and public. Interface attributes are by default public, static and final. An interface cannot contain a constructor (as it cannot be used to create objects). Java does not support "multiple inheritance" (a class can only inherit from one superclass). However, it can be achieved with interfaces, because the class can implement multiple interfaces. Note: To implement multiple interfaces, separate them with a comma (see example below).