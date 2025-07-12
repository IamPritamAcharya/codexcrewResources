# Dart Programming Basics

![Dart Logo](https://upload.wikimedia.org/wikipedia/commons/7/7e/Dart-logo.png)

## Introduction to Dart

Dart is a client-optimized programming language for apps on multiple platforms. It is developed by Google and is used to build mobile, desktop, server, and web applications.

### Variables and Data Types

```dart
// Variables
var name = 'John';
String lastName = 'Doe';
int age = 25;
double height = 5.9;
bool isStudent = true;

// Lists
List<String> fruits = ['apple', 'banana', 'orange'];

// Maps
Map<String, int> scores = {
  'math': 95,
  'science': 87,
  'english': 92
};
```

### Functions

```dart
// Function with return type
String greet(String name) {
  return 'Hello, $name!';
}

// Arrow function
int add(int a, int b) => a + b;

// Optional parameters
void printInfo(String name, {int? age}) {
  print('Name: $name');
  if (age != null) {
    print('Age: $age');
  }
}
```

### Classes and Objects

```dart
class Person {
  String name;
  int age;
  
  Person(this.name, this.age);
  
  void introduce() {
    print('Hi, I am $name and I am $age years old.');
  }
}

// Usage
var person = Person('Alice', 30);
person.introduce();
```

### Best Practices

1. Use meaningful variable names
2. Follow Dart naming conventions
3. Use null safety features
4. Write clean, readable code
5. Add documentation comments

> Dart is easy to learn and provides powerful features for building modern applications.