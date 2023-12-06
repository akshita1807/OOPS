# OOPS-Last minute revision notes✅

**Object oriented programming** enhances the readibility and maintainability of the code.In OOPS the whole code revolves around objects and classes.

# Class
blueprint or template on behalf of which object can be created

# Object
instance of the class

For eg:
class hai=fruits toh object hoga =apple,mango,banana method hoga =eat,wash,cut(these methods are basically the functions)  attribute hoga=taste ,color

**A class can exist without an object, but an object cannot exist without a class.**

# Function prototyping
declaration statement of the function(basically interface of the function)
function prototyping gives the compiler the details about the functions such as the number and types of arguments and the type of return values.

type function-name (arguments);

# Inline functions
inline functions are basically the small functions.function is expanded in line when it is invoked.function call is replaced by function body

inline function_type function name(arguments){
return a*a*a;
}

# Default arguments
assigns a defualt value to the function parameter which does not have a matching argument
also if one value is needed to be fixed

function can have default arguments from trailing

int mul(int i,int j=5,int k=6); **---true**  
int mul(int i=5,int j);  **--false**  
int mul(int i=5,int j,int k=10); **--false**  
int mul(int i=5,int j=6,int k=8); **--true**  


# Constructor
is a special method which is called automatically when an object of a class is created.It takes the same name as the class.It does not have any return value

```class anyname{
public:
anyname(){
cout<<"Hey"<<endl;
  }
}
```


Constructors can also take parameters (just like regular functions), which can be useful for setting initial values for attributes.

**Type of constructors**
default,parameterized,copy constructor

Constructors can also be defined outside the class--using scope resolution operator ::

```class Car {        // The class
  public:          // Access specifier
    string brand;  // Attribute
     
    int year;      // Attribute
    Car(string x, int z); // Constructor declaration with parameters
};


// Constructor definition outside the class
Car::Car(string x, int z) {
  brand = x;
 
  year = z;
}

int main() {
  // Create Car objects and call the constructor with different values
  Car carObj1("BMW", 1999);
  Car carObj2("Ford", 1969);

  // Print values
  cout << carObj1.brand << " " << carObj1.year;
  cout << carObj2.brand << " " << carObj2.year;
  return 0;
}
```
# scope resolution operator ::
-used for namespace  
-defining a function outside the class  
-to access a global variable when there is local variable with same name



# Access Specifiers
define how members(method and attributes)of a class can be accessed  
**public** - members are accessible from outside the class  
**private** - members cannot be accessed (or viewed) from outside the class  
**protected** - members cannot be accessed from outside the class, however, they can be accessed in inherited classes  


**By default, all members of a class are private if you don't specify an access specifier**

# Features of OOPS
# Encapsulation
is to make sure that "sensitive" data is hidden from users.To achieve this, you must declare class variables/attributes as private.If you want others to read or modify the value of a private member, you can provide public get and set methods.  
It allows us to bind data and functions of a class in a single unit which is done to protect data and functions from external misuse providing security. A class is the best example of encapsulation.

```#include <iostream>
using namespace std;

class Employee {
  private:
    // Private attribute
    int salary;

  public:
    // Setter
    void setSalary(int s) {
      salary = s;
    }
    // Getter
    int getSalary() {
      return salary;
    }
};

int main() {
  Employee myObj;
  myObj.setSalary(50000);
  cout << myObj.getSalary();
  return 0;
}
```

By Encapsulation, all the necessary data and methods are bind together and all the unnecessary details are hidden to the normal user. So Encapsulation is the process of binding data members and methods of a program together to do a specific job, without revealing unnecessary details.  
Encapsulation can also be defined in two different ways:  

**Data hiding**: Encapsulation is the process of hiding unwanted information, such as restricting access to any member of an object.  
**Data binding**: Encapsulation is the process of binding the data members and the methods together as a whole, as a class.  
getter and setter are used to read and modify private member of a class.  


# inheritance
is to inherit methods and attributes form one class to other
It is useful for code reusability: reuse attributes and methods of an existing class when you create a new class.

**base/parent class**-from which the child class is inherited
**derived/child class**-class which is inherited from other class

```#include <iostream>
#include <string>
using namespace std;

// Base class
class Vehicle {
  public: 
    string brand = "Ford";//attribute of base class
    void honk() {
      cout << "Tuut, tuut! \n" ;//method of base class
    }
};

// Derived class
class Car: public Vehicle {
  public: 
    string model = "Mustang";
};

int main() {
  Car myCar;//derived class ka object
  myCar.honk();
  cout << myCar.brand + " " + myCar.model;
  return 0;
//derived class ke object ke through hum parent class ke method and attribute access kr paa rhe
  
}
```
**Type of inheritance-single,multiple,multilevel,hybrid**  

**single** ek parent se ek base class inherit ki ho

**Multilevel** A class can also be derived from one class, which is already derived from another class.

```// Base class (parent)
class MyClass {
  public:
    void myFunction() {
      cout << "Some content in parent class." ;
    }
};

// Derived class (child)
class MyChild: public MyClass {
};

// Derived class (grandchild)
class MyGrandChild: public MyChild {
};

int main() {
  MyGrandChild myObj;
  myObj.myFunction();
  return 0;
}
```


**multiple** a class can also be derived from more than one class using comma

```class vehicle{//first base class
public:
void myfun(){
cout<<"Prent class"<<endl;
  }
}


class vehicle2{//second base class
public:
void myfun2(){
cout<<"also parent class"<<endl;
 }
}

class childvehicle:public vehicle,public vehicle2{//childvehicle is inheriting methods and attributes both from vehicle and vehicle2
};

int main() {
  childvehicle myObj;
  myObj.myfun();
  myObj.myfun2();
  return 0;
}
```


# diamond problem
It occurs when a class inherits from two or more classes that have a common ancestor. This common ancestor can lead to ambiguity because grandchild class will inherit menber of grandparent class from both parents.leads to duplication of data.

solution to this is=
make both parent class as virtual class .it will make ensure that content of grandparent class is present only once in grandchild

```class A {
public:
    virtual void method() {
        cout << "A method" << endl;
    }
};

class B : virtual public A {
public:
    void method() {
        cout << "B method" << endl;
    }
};

class C : virtual public A {
public:
    void method() {
        cout << "C method" << endl;
    }
};

class D : public B, public C {
};

int main() {
    D d;
    d.method(); // Calls D's method, which overrides A's method
    return 0;
}
```

# Abstraction 
If you are a user, and you have a problem statement, you don't want to know how the components of the software work, or how it's made. You only want to know how the software solves your problem. Abstraction is the method of hiding unnecessary details from the necessary ones. It is one of the main features of OOPs. 
For example, consider a car. You only need to know how to run a car, and not how the wires are connected inside it. This is obtained using Abstraction

# Polymorphism
poly(many) morphs(shapes)
A real-life example of polymorphism is a person who at the same time can have different characteristics. A man at the same time is a father, a husband, and an employee. So the same person exhibits different behavior in different situations. This is called polymorphism

**Polymorphism refers to the process by which some code, data, method, or object behaves differently under different circumstances or contexts**

**Compile time polymorphism**
(This type of polymorphism is achieved by function overloading or operator overloading.)

**function overloading**=When there are multiple functions with the same name but different parameters, then the functions are said to be overloaded, hence this is known as Function Overloading. Functions can be overloaded by changing the number of arguments or/and changing the type of arguments. 

**operator overloading**=C++ has the ability to provide the operators with a special meaning for a data type, this ability is known as operator overloading. For example, we can make use of the addition operator (+) for string class to concatenate two strings. We know that the task of this operator is to add two operands. So a single operator ‘+’, when placed between integer operands, adds them and when placed between string operands, concatenates them. 

Compile time polymorphism, also known as Static Polymorphism, refers to the type of Polymorphism that happens at compile time. What it means is that the compiler decides what shape or value has to be taken by the entity in the picture.

```#include <iostream>

class CompileTimePolymorphism {
public:
    // 1st method with name add
    int add(int x, int y) {
        return x + y;
    }

    // 2nd method with name add
    int add(int x, int y, int z) {
        return x + y + z;
    }

};

int main() {
    CompileTimePolymorphism demo;
    
    // In the below statement, the Compiler looks at the argument types and decides to call method 1
    cout << demo.add(2, 3) << endl;
    
    // Similarly, in the below statement, the compiler calls method 2
    cout << demo.add(2, 3, 4) <<endl;
    
    return 0;
}
```

The compiler looks at the method signature and decides which method to invoke for a particular method call at compile time.


**Run time polymorphism**=Runtime polymorphism, also known as Dynamic Polymorphism, refers to the type of Polymorphism that happens at the run time.This type of polymorphism is achieved by virtual functions and Function Overriding.
In runtime polymorphism, the compiler resolves the object at run time and then it decides which function call should be associated with that object.

**function overriding**=takes place when your derived class and base class both contain a function having the same name. Along with the same name, both the functions should have the same number of arguments as well as the same return type.For function overriding, inheritance is a must. It can only happen in a derived class.
//runtime ke wqt hi pta lgtahai ki base class ka function call hoga ya derived class ka isloye isko run time polymorphism bolte


```#include <iostream>

using namespace std;

// define a base class

class bird

{

   public:

   // display function of the base class

   void display()

   {

      cout << "I am the display function of the base class";

   }

};

class parrot:public bird

{

   public:

   // display function of the derived class

    void display() 

   {

      cout << "I am the display function of the derived class";

    

   }

};

int main()

{

   // create objects of base and child classes 

   bird b;

   parrot p;

   // call the diplay() function

   b.display();

   p.display();

}
```


Virtual Functions=A virtual function is a form of a member function declared within a base class and redefined by a derived class. The keyword virtual is used to create a virtual function, preceding the function's declaration in the base class.


when we use the same function name both in base and derived class the function in base class is declared as virtual 
virtual function is accessed by a pointer to the base class
Pure-virtual Functions with no defination.Starts with virtual keyword and end with =0.



# Friend Function
function which is present outside the class but it can access provate and protected members of the class

# Abstract Class
A class which has at least one pure virtual function.We can't make object of the abstract class.We can access it's memeber function using pointer or reference variable.


```class A{
public:
virtual void show()=0; //pure virtual function
}
```


# Interface
An interface is a contract between itself and any class that implements it. Interface can have methods, properties, or events. It contains only declaration of its members and implementation of its members will be given by the class who implements the interface. Interface makes it easy to maintain the program. Following are the specified terms of interface.
An interface can be defined by using interface keyword.
Interface can’t have private members.

``Syntax of interface declaration:
interface Interfacename{
//declare properties
//declare methods
}

Syntax of implementing interface:
class className:Interfacename{
//code
}
```

**Difference between struct and class?**
by default members of a class are private,that of struct are public.

# exception handling
used to catch errors-like syntax errors
three keywords=try,throw,catch

try{//detects error
throw exception;//if exception is detected it is thrown by throe keyword
}

catch{//catches and handles exception

}

cout<<"end";//final statement i.e executed irrespective of try catch




# imp que
```class A {
    A() {
        // Constructor code for class A
    }
}

class B extends A {
    B() {
        // Constructor code for class B
    }
}

class C extends B {
    C() {
        // Constructor code for class C
    }
}


order of constructors getting called

-A
-B
-C

order of destructors getting called

-C
-B
-A
```

item *ptr=new item[10];
creates memory space for an array of 10 items


# Types of variables

**ordinary variable**
int x=5;

**pointer variable**
int *p;
p=&x;
p is used to store address of x.for eg x has a value 5 and is stored at block 1000,p will give 100

**reference variable**

int &y=x;

y++ krne se x ki value increase hogi kyonki y now reprresents x


**Dynamic Memory Allocation
The mechanism by which storage/memory/cells can be allocated to variables during the run time is called Dynamic Memory Allocation.It allocates the memory during the run time which enables us to use as much storage as we want, without worrying about any wastage.

**Final Keyword**
can be applied to class,methods and variables.
Final class=A final class is a class that can not be subclassed.It prevents other classes from extending it and inheriting its behaviour.
A final method=can not be overridden
A final variable=can not be reassigned after its initial assignment

**static variable/data member** static variables maintain their value until the end of the program. It is initialized just once 
// Declare a static variable.
    static int temp = 0;
