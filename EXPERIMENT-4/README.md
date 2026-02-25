## Experiment-4a
## Title :Implement Single Inheritance
## Source code:
``` java
class Person {
   String name;
   int age;
   Person(String name,int age) {
     this.name = name;
     this.age = age;
   }
   void displayPersonDetails() {
     System.out.println("Name: "+name);
     System.out.println("Age: "+age);
   }
 }
 class Employee extends Person {
   double annualSalary;
   int yearOfJoining;
   String nationalInsuranceNumber;

   Employee(String name,int age,double annualSalary,int yearOfJoining,String nationalInsuranceNumber) {
     super(name,age);
     this.annualSalary = annualSalary;
     this.yearOfJoining = yearOfJoining;
     this.nationalInsuranceNumber = nationalInsuranceNumber;
   }
   void displayEmployeeDetails() {
     displayPersonDetails();
     System.out.println("AnnualSalary: "+annualSalary);
     System.out.println("YearOfJoining: "+yearOfJoining);
     System.out.println("NationalInsuranceNumber: "+nationalInsuranceNumber);
   }
}
class Main {
   public static void main(String args[]) {
     Employee emp = new Employee("Suvarna",28,55000.0,2026,"NI122345");
     emp.displayEmployeeDetails();
  }
}
```
## Output:
![Exp-4a Output](Exp4a.png)

## Experiment-4b
## Title :Implement Multi-level Inheritance
## Source code:
``` java
class Bicycle {
    void showBicycleInfo() {
      System.out.println("This is a bicycle. ");
    }
  }
  class Motorbike extends Bicycle {
    void showMotorbikeInfo() {
      System.out.println("This is motorbike. ");
    }
  }
  class ElectricBike extends Motorbike {
    void showElectricBikeInfo() {
      System.out.println("This is Electric bike. ");
    }
  }
  public class TestVehicle {
    public static void main(String[] args) {
        ElectricBike ebike=new ElectricBike();
        ebike.showBicycleInfo();
        ebike.showMotorbikeInfo();
        ebike.showElectricBikeInfo();
      }
    }
```
## Output:
![Exp-4b Output](Exp4b.png)

## Experiment-4c
## Title :To construct abstract class to find areas of different shapes
## Source code:
``` java
abstract class Figure {
   double dim1;
   double dim2;
   Figure(double dim1,double dim2) {
     this.dim1 = dim1;
     this.dim2 = dim2;
   }
   abstract double area();
 }
 class Rectangle extends Figure {
    Rectangle (double length,double breadth) {
     super(length,breadth);
    }
    double area() {
      double result = dim1*dim2;
      return result;
    }
 }
 class Triangle extends Figure {
    Triangle(double base,double height) {
     super(base,height);
    }
     double area() {
      double result = 0.5*dim1*dim2;
      return result;
     }
 }
public class TestFigure {
  public static void main(String args[]) {
    Figure f1 = new Rectangle(23.4,14.5);
    Figure f2 = new Triangle(12.3,15.6);
    System.out.println("Area of Rectangle = "+f1.area());
    System.out.println("Area of Triangle = "+f2.area());
  }
}
```
## Output:
![Exp-4c Output](Exp4c.png)
