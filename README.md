# Creational Design Patterns in Java

This repository showcases various **Creational Design Patterns** used in software development. These patterns focus on the efficient and flexible creation of objects, making your code scalable, maintainable, and easy to understand.

## Patterns Covered:

1. **Singleton Pattern**
2. **Factory Method Pattern**
3. **Abstract Factory Pattern**
4. **Builder Pattern**
5. **Prototype Pattern**

## Pattern Details:

### 1. **Singleton Pattern**
- **Purpose**: Ensures that a class has only one instance and provides a global access point to it.
- **When to Use**: When you need to manage a shared resource like configuration settings, logging, or a database connection.
- **Code Example**:
  ```java
  public class Singleton {
      private static Singleton instance;
      
      private Singleton() {} // Private constructor prevents instantiation
      
      public static Singleton getInstance() {
          if (instance == null) {
              instance = new Singleton();
          }
          return instance;
      }
  }
  

### 2. **Factory Method Pattern**
- **Purpose**: Defines an interface for creating objects, allowing subclasses to alter the type of objects created.
- **When to Use**: When you need to introduce flexibility by deferring the object creation to subclasses.
- **Code Example**:
  ```java
  abstract class Product {
    abstract void use();
  }
  
  class ConcreteProductA extends Product {
      void use() { System.out.println("Using Product A"); }
  }
  
  class Creator {
      public Product createProduct(String type) {
          if (type.equals("A")) return new ConcreteProductA();
          return null; // Other types can be added
      }
  }


### 3. **Abstract Factory Pattern**
- **Purpose**: Provides an interface for creating families of related objects without specifying concrete classes.
- **When to Use**: When you need to create objects that belong to a specific theme or set, such as different UI components for various platforms.
- **Code Example**:
  ```java
  interface GUIFactory {
    Button createButton();
    Checkbox createCheckbox();
  }
  
  class MacFactory implements GUIFactory {
      public Button createButton() { return new MacButton(); }
      public Checkbox createCheckbox() { return new MacCheckbox(); }
  }
  
  class WinFactory implements GUIFactory {
      public Button createButton() { return new WinButton(); }
      public Checkbox createCheckbox() { return new WinCheckbox(); }
  }


### 4. **Builder Pattern**
- **Purpose**: Separates the construction of a complex object from its representation, allowing the same construction process to create different objects.
- **When to Use**: When an object has many optional attributes or configurations, and you want to avoid a constructor with numerous parameters.
- **Code Example**:
  ```java
  class Product {
      private String part1;
      private String part2;
  
      public static class Builder {
          private String part1;
          private String part2;
  
          public Builder setPart1(String part1) {
              this.part1 = part1;
              return this;
          }
  
          public Builder setPart2(String part2) {
              this.part2 = part2;
              return this;
          }
  
          public Product build() {
              Product product = new Product();
              product.part1 = this.part1;
              product.part2 = this.part2;
              return product;
          }
      }
  }

### 5. **Prototype Pattern**
- **Purpose**: Creates new objects by copying a prototype instance.
- **When to Use**: When object creation is expensive or time-consuming, and you want to clone existing objects instead of creating new ones from scratch.
- **Code Example**:
  ```java
  class Prototype implements Cloneable {
      private String data;
  
      public Prototype(String data) {
          this.data = data;
      }
  
      public Prototype clone() throws CloneNotSupportedException {
          return (Prototype) super.clone();
      }
  }


### Explanation:
- **Purpose**: Each pattern is introduced with a brief explanation of when and why to use it.
- **Code Examples**: Simple Java code snippets demonstrate how each pattern can be implemented.

