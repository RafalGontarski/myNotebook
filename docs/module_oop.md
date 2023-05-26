# OOP

#### Define a constructor?
>A constructor in Java is a special method that is called when an object of a class is created. It is used to initialize the object's fields and can also perform any other initialization required by the object.

**Here's an example of a constructor in Java:**


    public class Person {
        private String name;
        private int age;
    
        public Person(String name, int age) {
            this.name = name;
            this.age = age;
        }
        
        public void setName(String name) {
            this.name = name;
        }
        
        public String getName() {
            return name;
        }
        
        public void setAge(int age) {
            this.age = age;
        }
        
        public int getAge() {
            return age;
        }
    }

>In this example, we have defined a class **Person** with two private fields **name** and **age**. The constructor of the **Person** class takes two arguments, **name** and **age**, and initializes the corresponding fields of the object using the **this** keyword. The **this** keyword refers to the current instance of the object being created.

>We have also defined getter and setter methods for the **name** and **age** fields. These methods can be used to get and set the values of the fields for an object of the **Person** class. 

**Here's an example of how to create an object of the Person class using the constructor:**

    Person person = new Person("John", 25);

>In this example, we create a new **Person** object called **person** and pass the arguments "John" and 25 to the constructor. The constructor initializes the **name** and **age** fields of the object to "John" and 25 respectively.


#### Difference between overloading and overriding?

>Overloading and overriding are two concepts in object-oriented programming that are used to create methods with different behavior.

>Overloading refers to defining multiple methods in a class with the same name but different parameters. These methods can have different signatures, such as different types or numbers of arguments. When a method is called, the appropriate method is selected based on the number and types of arguments passed to it.

Here's an example of method overloading in Java:


    public class Calculator {
        public int add(int x, int y) {
        return x + y;
        }
    
        public double add(double x, double y) {
            return x + y;
        }
    
        public int add(int x, int y, int z) {
            return x + y + z;
        }
    }

>In this example, we have defined three methods with the same name add, but different parameter lists. The appropriate method is selected based on the number and types of arguments passed to it.

>Overriding, on the other hand, refers to defining a method in a subclass that has the same name and signature as a method in the superclass. The subclass method overrides the superclass method, providing a new implementation for it. When a method is called on an object of the subclass, the overridden method in the subclass is called instead of the method in the superclass.

Here's an example of method overriding in Java:


    public class Animal {
        public void makeSound() {
        System.out.println("The animal makes a sound");
        }
    }

    public class Cat extends Animal {
        @Override
        public void makeSound() {
        System.out.println("The cat meows");
        }
    }

>In this example, we have defined a class Animal with a method makeSound, and a subclass Cat that overrides the makeSound method. When the makeSound method is called on a Cat object, the overridden method in the Cat class is called, which prints "The cat meows" to the console.

>In summary, overloading is used to define multiple methods with the same name but different parameters, while overriding is used to provide a new implementation for a method in a subclass that has the same name and signature as a method in the superclass.

#### Do we require parameters for constructors?
#### Explain the “Single Responsibility” principle!
#### How do you prevent developers from changing the value of a variable?
#### How do you prevent developers from inheriting a class?
#### How do you prevent developers from overriding a method in a child class?
#### How do you prevent developers from overriding a method in a subclass?
#### How do you prevent developers from subclassing a class?
#### What are access modifiers?
#### What are base class, subclass and superclass?
#### What are different types of arguments? (context: pass by value / pass by reference)
#### What are generic types and why are they used?
#### What are mutable and immutable types?
#### What are the differences between abstract classes and interfaces?
#### What are the differences between classes and objects?
#### What are the differences between overriding and overloading?
#### What are the differences between static and instance members?
#### What do S & D stand for in SOLID?
#### What do S & I stand for in SOLID?
#### What do S & O stand for in SOLID?
#### What does "this" keyword do?
#### What does it mean that an object is Immutable?
#### What is a class?
#### What is a constructor?
#### What is abstraction and why is it used?
#### What is an abstraction?
#### What is an interface?
#### What is an object oriented program?
#### What is an object?
#### What is casting? What is the difference between up vs downcasting?
#### What is encapsulation and why is it used?
#### What is Encapsulation? Explain the concept with a realistic example!
#### What is exception handling?
#### What is garbage collection and when does it happen?
#### What is inheritance?
#### What is Inheritance? Explain the concept with a realistic example!
#### What is method overloading?
#### What is OOP? Inheritance? Polymorphism? Abstraction? Encapsulation?
#### What is polymorphism and why is it used?
#### What is Polymorphism? Explain the concept with a realistic example!
#### What is the difference between == and equals method?
#### What is variable scoping?
#### Whether static method can use non static members?
#### What is a UML class diagram? What are the typical elements?