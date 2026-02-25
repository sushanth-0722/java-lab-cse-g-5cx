## EXPERIMENT-5
## Title:To implement interface.
## SourceCode:
``` java
interface sortable {
  public abstract void sort(int[] arr);
}
class BubbleSort implements sortable {
  public void sort(int[] arr) {
    int size = arr.length;
    int temp = 0;
    for(int i=0; i<size-1; i++) {
      for(int j=0; j<size-i-1; j++) {
        if(arr[j] >arr[j+1]) {
          temp = arr[j+1];
          arr[j+1] = arr[j];
          arr[j] = temp;
        }
      }
    }
  }
}
class SelectionSort implements sortable {
  public void sort(int[] arr) {
    int size = arr.length;
    int minIndex = 0;
    int min;
    for(int i=0; i<size; i++) {
      min = arr[i];
      for(int j=i+1; j<size; j++) {
        if(min > arr[j]) {
          min = arr[j];
          minIndex = j;
        }
      }
      for(int j=minIndex; j>i; j--) {

        arr[j] = arr[j-1];
      }
      arr[i] = min;
    }
  }
}
class TestSort {
  static void display(int arr[]) {
    for(int ele : arr) {
      System.out.print(ele +", ");
    }
    System.out.println("\b\b.");
  }
  public static void main(String args[]) {
    int[] arr = {9, 7, 4, 3, 6, 8};
    int[] bar = {8, 6, 3, 4, 7, 9};
    sortable s;
    s = new BubbleSort();
    s.sort(arr);
    System.out.println("after BubbleSort: ");
    display(arr);
    s = new SelectionSort();
    s.sort(bar);
    System.out.println("after selectionsort: ");
    display(bar);
  }
}
```
## Output:
![EXP-5a output](exp5a.png)

## experiment-5b
## Title:To implement Runtime polymorphism.
## SourceCode:
``` java
class Vehicle
{
    void run()
    {
        System.out.println("vehicle is running");
    }
}

class Bike extends Vehicle
{
    void run()
    {
        System.out.println("Bike is running");
    }
}

class Car extends Vehicle
{
    void run()
    {
        System.out.println("car is running");
    }
}

class TestVehicle
{
    public static void main(String args[])
    {
        Vehicle v;

        v = new Car();
        v.run();

        v = new Bike();
        v.run();

        v = new Vehicle();
        v.run();
    }
}
```
## Output:
![EXP-5b output](exp5b.png)

## experiment-5c
## Title:To implement stringbuffer to delete,remove character.
## SourceCode:
``` java
class DeleteChar
{
    public static void main(String args[])
    {
        StringBuffer sb = new StringBuffer("java program");

        System.out.println(sb);

        sb.deleteCharAt(4);
        System.out.println(sb);

        sb.delete(0, 4);
        System.out.println(sb);
    }
}
```
## Output:
![EXP-5c output](exp5c.png)
