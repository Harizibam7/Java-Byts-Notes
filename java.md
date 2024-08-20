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

- Java is Strictly typed or Strongly typed language

### Java Setup

- Download the latest version of java from [oracle.com](http://oracle.com) and install it.
- Check whethere the blow commands are working fine or not after installation.

`javac -version`   

**`java - version`** 

First Java Program

```java
class Test{
	public static void main(String[] args){
		System.out.println("Hello World ...");
	}
}
```

Compilation: javac Test.java

Execution   : java Test

### Platform Independence of Java

If we are able to run the code.  (In java, byte code) on any platform irrespective of in which platform it is compiled then it is called as platfrom independent.

![Screenshot from 2024-08-20 21-19-36.png](Java%20Byts%20Notes%20fed23fdf428045d488f7bd9183adda3e/Screenshot_from_2024-08-20_21-19-36.png)

**Data Types & Literals**

![Screenshot from 2024-08-20 21-26-19.png](Java%20Byts%20Notes%20fed23fdf428045d488f7bd9183adda3e/Screenshot_from_2024-08-20_21-26-19.png)

There are two type of data type

- Primitive data type
- Non Primitive data type

### Primitive Data type

![Screenshot from 2024-08-20 21-35-00.png](Java%20Byts%20Notes%20fed23fdf428045d488f7bd9183adda3e/Screenshot_from_2024-08-20_21-35-00.png)

| Data Type | Size | Rangle | Default Value | Wrapper Class |
| --- | --- | --- | --- | --- |
| byte | 1 byte | -128 to 127 | 0  | Byte |
| short  | 2 bytes | -32768 to 32767 | 0 | Short |
| int | 4 bytes | -2147483648 to 2147483647 | 0 | Int |
| long | 8 bytes |  |  |  |