# Java Byts Notes

## Core Java

- Java Introduction
- Oops
- Modifier
- Exception Handling
- Multithreading
- Collection Framework
- Java.lang.package

### Java Introduction

- Java is a Strictly typed or Strongly typed language

### Java Setup

- Download the latest version of Java from [oracle.com](http://oracle.com) and install it.
- Check whether the commands below work fine after installation.

`javac -version`   

**`java - version`** 

First Java Program

```java
class Test{
	public static void main(String[] args){
		System.out.println("Hello World ...");
	}
}
**OUTPUT:** Hello World ...
```

Compilation: javac [Test.java](http://Test.java)

Execution   : java Test

### Platform Independence of Java

If we can run the code.  (In java, byte code) on any platform irrespective of in which it is compiled, it is called platform independent.

![Screenshot from 2024-08-20 21-19-36.png](Screenshot_from_2024-08-20_21-19-36.png)

**Data Types & Literals**

![Screenshot from 2024-08-20 21-26-19.png](Screenshot_from_2024-08-20_21-26-19.png)

There are two types of data type

- Primitive data type
- Non Primitive data type

### Primitive Data type

![Screenshot from 2024-08-20 21-35-00.png](Screenshot_from_2024-08-20_21-35-00.png)

| Data Type | Size | Range | Default Value | Wrapper Class |
| --- | --- | --- | --- | --- |
| byte | 1 byte | -128 to 127 | 0  | Byte |
| short  | 2 bytes | -32768 to 32767 | 0 | Short |
| int | 4 bytes | -2147483648 to 2147483647 | 0 | Integer |
| long | 8 bytes | -9223372036854775808 to 9223372036854775807 | 0 | Long |
| float | 4 bytes | -3.4e38 to 3.4e38 | 0.0 | Float |
| double | 8 bytes | -1.7e308 to 1.7e308 | 0.0 | Double |
| boolean | Not Applicable (is JVM dependent) | Not Applicable (only values allowed are **true** or **false**) | false | Boolean |
| char | 2 bytes | 0 to 65535 | 0 (null character) | Character |

> NULL is different and null character is different.  In java, there is no representation for **`null`** character, so that we can use **`unicode`** to represent.
> 

---

## Types of variables

1. Based on the type of  value represented by a variable, variables are categorized into two types:
- **Primitive variables** - Primitive variables are used to represent primitive values.
- **Reference variables -** Reference variables are used to represent an object.

## NOTE

- Default value for any object reference is null.

```java
class Test{
   static String s;
	public static void main(String[] args){
		System.out.println("s");
	}
}
**OUTPUT : null**
```

> JVM will provide default value only for static and non-static(instance) variables, but not for local variables.
> 

Based on the purpose and position of the declaration, all the variables are categorized into 3 types.

- instance variable
- static variable
- local variable

### Instance Variable

If **`the** **value of the variable is varying from object to object**` then such type of variable is called instance variable.  Instance variables are also known as **`Attributes`** or **`Object level variables`**.

<aside>
💡 In case of instance variable a separate copy will be created for every object.

</aside>

- **When will be the instance created?**
    
    Instance variable will be created at a time of object creation. 
    
- **When will be the instance destroyed?**
    
     Instance variable will be destroyed at a time of destruction.
    

> Hence the scope of instance variable is as exactly same as object scope.
> 

### Types of Memory Areas Allocated By the JVM

- Method Area
- Head Area
- Stack Area
- PC Registers
- Java Native Stacks

> Instance variable will be created in **`Heap memory`** area as part of Object.  For instance variable JVM will always provide default value at the time of object creation.
> 

---

<aside>
⚠️ Compilation Error: non-static variable x cannot be referenced from a static context

</aside>

```java
public class Test{
    int x = 10;
    public static void main(String[] args){
        System.out.println(x);
    }
}
**Output**:(C.E)
```

![Screenshot from 2024-08-25 14-39-05.png](Screenshot_from_2024-08-25_14-39-05.png)

To overcome this error, we have to **`use object reference`** to access instance variables from the static area. 

> From instance area we can access instance member directly.
> 

Example:

```java
public class Test{
    int x = 10; // Instance variable
    public static void main(String[]args){
        Test t = new Test();
        System.out.println(t.x); //Inside static area access Instance variable using object.
        t.m1();
    }
    public void m1(){
        System.out.println(x); //Inside Non-static area, directly access
    }
}
**Output:** 
10
10
```

### Static Variable

- If the **`value of a variable is common for all the objects of the class`**, then we should go for a static variable.
- In the case of a static variable, **`only one copy will be created`** and **`shared by all the objects of that class`**.
- **When will be the static variable created?**
    
    Static variables will be created at the time of **`class loading`**.
    
- **When will be the static variable destroyed?**
    
    Static variable will be **`destroyed at the time of class unloading`**.
    

<aside>
💡 The scope of the static variable is the same as the class scope. The static variable will be created in the Method Area, which is also known as the Context Area.

</aside>

For static variables, JVM will always provide a default value at the time of class loading.

 

```java
public class Test{
    static int x;
    public static void main(String[] args){
        System.out.println(x);
    }
}
**Output: 0**
```

We can access a static variable either by using the class name or by using an object reference.  But usage of class names is recommended.  If it is within the same class then we can access it directly by using a variable name and the class name is also not required. 

```java
public class Test{
    static int x = 10;
    public static void main(String[] args){
        System.out.println(x);
        System.out.println(Test.x);
        Test t = new Test();
        System.out.println(t.x);
    }
}
**Output**:
10
10
10
```

We can **`access static variables directly`** from both **`static`** and **`instance areas`**.

```java
public class Test{
    static int x = 10;
    public static void main(String[] args){
        System.out.println(x);
        new Test().m1();
    }
    public void m1(){
        System.out.println(x);
    }
}
**Output**:
10
10 
```

> Static variables are also known as **`Fields`** or **`Class level`** variables.
> 

![Screenshot from 2024-08-25 22-05-39.png](Screenshot_from_2024-08-25_22-05-39.png)

### Local Variables:

We can declare variables within methods, blocks, loops, etc. These variables are called local variables. 

- **When will be the local variables created?**
    
    Local variables will be created by execution of the block where we have declared it.
    
- **When will be the local variables destroyed?**
    
    It will be destroyed automatically once the block execution is completed.
    

<aside>
💡 The scope of local variables is the same as the block scope.  Local variables will be created in the Stack Area.

</aside>

### **Note:**

Local variable JVM won’t provide default values; the programmer is only responsible for explicitly performing initialization.

```java
public class Test{
    public static void main(String[] args){
        int x; // declared a variable x and not used.
        System.out.println("Hello"); 
    }
}
**Output:** Hello
```

```java
public class Test{
    public static void main(String[] args){
        int x;
        ;;;;;;
        x = 10; // declared a variable x and used after initialization, so works fine
        System.out.println(x);
    }
} 
**Output:10**
```

<aside>
⚠️ **Compilation Error:** variable x might not have been initialized

</aside>

```java
public class Test{
    public static void main(String[] args){
        int x;
        System.out.println(x);
    }
}
```

![Screenshot from 2024-08-26 17-54-50.png](Screenshot_from_2024-08-26_17-54-50.png)

<aside>
⚠️ **Compilation Error:** cannot find symbol

</aside>

```java
public class Test{
    public static void main(String[] args){
        int i;
        for(i =0; i< 3;i++){
            for(int j = 0; j<3;j++){
                i = i + j;
            }
        }
        System.out.println(i + " ----- "+ j);
    }
}
```

![image.png](image.png)

> Local variables are also known as temporary variables or Automatic variables or Stack variables.
> 

### Command line arguments

- The arguments that we are **`passing from the command prompt`** to the program are called command line arguments.
- These are the arguments for the main() method and are available in the form of a string by default.

![Screenshot from 2024-08-26 18-08-24.png](Screenshot_from_2024-08-26_18-08-24.png)

<aside>
⚠️ **Runtime Error**: java.lang.ArrayIndexOutOfBoundsException

</aside>

```java

    public static void main(String[] args){
        for(int i = 0;i<=args.length;i++){
            System.out.println(args[i]);
        }
    }
}
```

![image.png](image%201.png)

The default form of argument in the main method is the string, to parse the string to int see the below code,

```java
public class Test{
    public static void main(String[] args){
        System.out.println(args[0] + args[1]);
        System.out.println(Integer.parseInt(args[0]) + Integer.parseInt(args[1]));
    }
}
```

![image.png](image%202.png)

<aside>
⚠️ **Runtime Error:** java.lang.NumberFormatException

</aside>

```java
class Test{
    public static void main(String[] args){
        int x = Integer.parseInt(args[0]);
        System.out.println(x);
    }
}
```

![image.png](image%203.png)

- **Guess the Output**
    
    ```java
    public class Test{
        public static void main(String[] args){
            try{
                int x = Integer.parseInt(args[0]);
                System.out.println(x);
            }catch(NumberFormatException e){
                x = 20;
                System.out.println("Inside Catch block: "+ x);
            }
        }
    }
    ```
    
    - **Answer**
        
        ![image.png](image%204.png)
        
        Because the local variable scope finished try block so we can access the x variable in the catch block.
        

---

If we initialize a variable with a control statement, The code should always be initialized otherwise the compiler raises the error.

```java

class Test{
    public static void main(String[] args){
        int x;
        if(args.length > 0){
            x = 10;
        }
        System.out.println(x); // There is a chance of not initializing a variable x.
    }
}
```

![image.png](image%205.png)

```java
public class Test{
    public static void main(String[] args){
        int x;
        if(args.length > 0){
            x = 0;
        }else{
            x = 20;
        }
        System.out.println(x);
    }
}
```

![image.png](image%206.png)

The above code compiles successfully. Because x will always be initialized.  

> It is always recommended to perform initialization of local variable at the time of declaration itself atleast with default value so that we won’t come across initialiation issues.
> 

## OOPS - **Object-Oriented Programming System**

### Topics:

- Class
- Object
- Data Hiding
- Abstraction
- Encapsulation
- Is-A relationship
- Has-A relationship
- Method Signature
- Method Overloading
- Method Overriding
- Method Hiding
- Static Control Flow
- Instance Control Flow
- Constructors
- Type Casting
- Coupling

### Class

The **`logical representation of the object`** is called a class (or) the **`structure of the object`** is called a class.

 Example:

```java
class Student{
    int id;
    String name;
}
```

### Object

An **`instance of the class is nothing but an object`**, Once if we have a class we can create any number of instances for that class, based on our requirement.

```java
class Student{
    int id;
    String name;
    Student(int sid, String sname){
        id = sid;
        name = sname;
    }
}
public class Test{
    public static void main(String[] args){
        Student s1 = new Student(101, "Jack");
        Student s2 = new Student(102, "Rose");
        System.out.println(s1.id + " ..... " + s1.name);
        System.out.println(s2.id + " ..... " + s2.name);
    }
}
```

### Data Hiding

- The process of hiding the data from direct access is called data hiding.
- The main advantage of data hiding is we can achieve security.
- By using a **`private`** modifier we can achieve data hiding.

<aside>
⚠️ Compilation Error: error: __Variable_Name__  has private access in __Class_Name__

</aside>

```java
class Account{
    private double balance = 10;
}
public class Test{
    public static void main(String[] args){
        Account a = new Account();
        System.out.println(a.balance);
        System.out.println(a.getBalance());
    }
}
```

- **Output**
    
    ![image.png](image%207.png)
    

To get a value of the private modifier variable we can get via the method call below the example,

```java
class Account{
    private double balance;
    public double getBalance(){
        //Validation logic
        return balance;
    }
}
public class Test{
    public static void main(String[] args){
        Account a = new Account();
        System.out.println(a.getBalance());
    }
}
```

- **Output**
    
    ![image.png](image%208.png)
    

Example for Data Hiding

```java
class Address{
    String house_no;
    String street;
    String city;
    String state;
    int pincode;
}
class Student{
    int id;
    String name;
    Address address;
    //Due to policy, should not access age directly
    private int age;
    public int getAge(){
        return age;
    }
    public void setAge(int age){
        this.age = age;
    }
}
public class Test{
    public static void main(String[] args){
        Address a = new Address();
        a.city = "Bangalore";
        Student s1 = new Student();
        s1.id = 10;
        s1.name= "Harizibam";
        s1.setAge(19);
        s1.address = a;  
    }
}
```

### Abstraction

The process of **`highlighting the required services by hiding their internal implementation`** is called abstraction.

> By using abstract classes and interfaces we can achieve abstraction.
> 

**The advantage of abstraction,**

- We can achieve security as we are not highlighting internal implementation.
- Enhancement will become easy.
- It improves the modularity and maintainability of the application

### Encapsulation

- Binding the data together with its relational methods is the concept of encapsulation.
- Class is the base to define encapsulation and we can achieve it by creating the object of the class.

```java
class Product{
    private int id;
    private String name;
    public void setId(int id){
        this.id = id;
    }
    public int getId(){
        return id;
    }
    public void setName(String name){
        this.name = name;
    }
    public String getName(){
        return name;
    }
}
```

> Note: In the above code, (int id, String name) both of them are instance variables.  The methods getId, setId, getName, setName are also instance methods. Means the id variable and name variable also visible in the instance methods.  The paramter variable (id, name) also have same name as instance variable. To identifiy the instance variable we are using ‘**`this`**’ keyword.
