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

