لازم تتفرج علي كل بلاي ليست دي
[SOLID Principles](https://youtube.com/playlist?list=PLwWuxCLlF_uevri_OpofVLXkRRFnZ7TSV&si=llpAPlS1GJduE1Go)

<p align="center">
  <img src="../oopPhotos/let&apos;sgo.jpeg" alt="Alt text" />
</p>

# questions (MCQs)

1. Which SOLID principle advocates that a class should have only one reason to change?
   A) Open/Closed Principle
   B) Liskov Substitution Principle
   C) Single Responsibility Principle
   D) Dependency Inversion Principle

**Answer: C**

2. According to the Open/Closed Principle, a class should be:
   A) Open for extension, closed for modification
   B) Open for modification, closed for extension
   C) Closed for both extension and modification
   D) Open for both extension and modification

**Answer: A**

3. The Liskov Substitution Principle primarily ensures that:
   A) Subclasses can serve as base classes without affecting the program

C) Interfaces are not implemented by classes
D) Dependencies are inverted in the class hierarchy

**Answer: A**

4. What does the Interface Segregation Principle aim to prevent?
   A) Classes that are tightly coupled
   B) Classes that implement interfaces they do not use
   C) Subclasses from inheriting properties of the base class
   D) Classes from depending on each other

**Answer: B**

5. The Dependency Inversion Principle states that:
   A) High-level modules should not depend on low-level modules
   B) Both high-level and low-level modules should depend on abstractions
   D) All of the above

**Answer: D**

6. Which principle is being violated if a change in a low-level class requires changes in high-level classes?
   A) Single Responsibility Principle
   B) Open/Closed Principle
   C) Liskov Substitution Principle
   D) Dependency Inversion Principle

**Answer: D**

7. When applying the Single Responsibility Principle, what outcome is expected?
   A) Increased number of classes in the system
   B) Decreased flexibility of the system
   C) Increased complexity of individual classes
   D) Reduced scope for code reuse

**Answer: A**

8. In the context of the Open/Closed Principle, which of the following is a recommended practice?
   A) Modifying existing code to add new functionality
   B) Using inheritance to extend the behavior of a class
   C) Copying and pasting code to avoid modifying the original class
   D) Creating large classes that handle multiple responsibilities

**Answer: B**

9. The Liskov Substitution Principle helps in:
   A) Ensuring that inheritance is used only when necessary
   B) Making sure that new derived classes just extend without replacing the functionality of old classes
   C) Guaranteeing that new subclasses replace the functionality of old classes
   D) Allowing multiple implementations of an interface

**Answer: B**

10. Which of the following best describes the Interface Segregation Principle?
    A) A client should not be forced to depend on interfaces it does not use
    B) A client should depend on interfaces that are large and comprehensive
    C) A client should implement as many interfaces as possible
    D) A client should use multiple small interfaces instead of a single large one

**Answer: A**

# Question

Here are five Java code examples that violate SOLID principles, write explanations on how they can be improved
and write code to improve it

1.

```java
public class UserSettings {
    private User user;

    public void changeEmail(String newEmail) {
        if(checkAccess(user)) {
            user.setEmail(newEmail);
            System.out.println("Email changed!");
        }
    }

    private boolean checkAccess(User u) {
        // Verify if the user has access
        return true;
    }
}
```

**Improvement**: The `UserSettings` class should not be responsible for both changing the user's email and verifying access. These responsibilities should be separated into different classes.

2.

```java
public class Rectangle {
    public double width;
    public double height;
}

public class AreaCalculator {
    public double calculateRectangleArea(Rectangle rectangle) {
        return rectangle.width * rectangle.height;
    }
}
```

**Improvement**: The `AreaCalculator` class should be open for extension but closed for modification. To add support for more shapes without modifying the `AreaCalculator`, we can introduce an interface or abstract class for shapes.

3.

```java
public class Bird {
    public void fly(){}
}

public class Ostrich extends Bird {
    @Override
    public void fly() {
        throw new UnsupportedOperationException();
    }
}
```

**Improvement**: The `Ostrich` class should not inherit from `Bird` if it cannot fly. Instead, we can have a separate hierarchy for birds that can fly and those that cannot.

4.

```java
public interface Worker {
    void work();
    void eat();
}

public class HumanWorker implements Worker {
    public void work() {
        // working
    }

    public void eat() {
        // eating
    }
}

public class RobotWorker implements Worker {
    public void work() {
        // working
    }

    public void eat() {
        // Robots don't eat, so this method should not be here
    }
}
```

**Improvement**: The `Worker` interface should be split into separate interfaces, such as `Workable` and `Eatable`, so that classes like `RobotWorker` don't have to implement unnecessary methods.

5.

```java
public class LightBulb {
    public void turnOn() {
        // Turn on the light bulb
    }

    public void turnOff() {
        // Turn off the light bulb
    }
}

public class Switch {
    private LightBulb lightBulb;

    public Switch(LightBulb lightBulb) {
        this.lightBulb = lightBulb;
    }

    public void operate() {
        // Operate the switch
    }
}
```

**Improvement**: The `Switch` class should not directly depend on the `LightBulb` class. Instead, we can introduce an interface, such as `Switchable`, that `LightBulb` implements. This way, `Switch` depends on an abstraction, not a concretion.

answers with code

1. **Single Responsibility Principle (SRP)**

```java
public class User {
    private String email;

    // Getters and setters for email
    // ...
}

public class UserAuth {
    public boolean checkAccess(User user) {
        // Verify if the user has access
        return true;
    }
}

public class UserEmailChanger {
    private UserAuth userAuth;

    public UserEmailChanger(UserAuth userAuth) {
        this.userAuth = userAuth;
    }

    public void changeEmail(User user, String newEmail) {
        if(userAuth.checkAccess(user)) {
            user.setEmail(newEmail);
            System.out.println("Email changed!");
        }
    }
}
```

2. **Open/Closed Principle (OCP)**

```java
public interface Shape {
    double calculateArea();
}

public class Rectangle implements Shape {
    private double width;
    private double height;

    // Constructor, getters, and setters

    @Override
    public double calculateArea() {
        return width * height;
    }
}

public class AreaCalculator {
    public double calculateShapeArea(Shape shape) {
        return shape.calculateArea();
    }
}
```

3. **Liskov Substitution Principle (LSP)**

```java
public abstract class Bird {
    // Common methods for all birds
}

public class FlyingBird extends Bird {
    public void fly() {
        // Implementation for flying
    }
}

public class Ostrich extends Bird {
    // Ostrich-specific methods
}
```

4. **Interface Segregation Principle (ISP)**

```java
public interface Workable {
    void work();
}

public interface Eatable {
    void eat();
}

public class HumanWorker implements Workable, Eatable {
    @Override
    public void work() {
        // working
    }

    @Override
    public void eat() {
        // eating
    }
}

public class RobotWorker implements Workable {
    @Override
    public void work() {
        // working
    }
}
```

5. **Dependency Inversion Principle (DIP)**

```java
public interface Switchable {
    void turnOn();
    void turnOff();
}

public class LightBulb implements Switchable {
    @Override
    public void turnOn() {
        // Turn on the light bulb
    }

    @Override
    public void turnOff() {
        // Turn off the light bulb
    }
}

public class Switch {
    private Switchable device;

    public Switch(Switchable device) {
        this.device = device;
    }

    public void operate() {
        // Operate the switch
    }
}
```
