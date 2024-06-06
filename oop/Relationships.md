1. Which of the following best describes association in Java?
   A) It is a "has-a" relationship between two classes.
   B) It is a "part-of" relationship between two classes.
   C) It is a "is-a" relationship between two classes.
   D) It is a "contains-a" relationship between two classes.

**Answer: A**

2. In Java, aggregation implies which of the following?
   A) The child object cannot exist without the parent object.
   B) The parent object owns the child object.
   C) The child object can exist independently of the parent object.
   D) The parent and child objects are the same.

**Answer: C**

3. Composition in Java enforces which kind of relationship?
   A) Weak "has-a" relationship.
   B) Strong "has-a" relationship.
   C) "is-a" relationship.
   D) None of the above.

**Answer: B**

4. What does a composition relationship imply about the lifecycle of the related objects?
   A) The contained object's lifecycle is independent of the container object.
   B) The container object's lifecycle is dependent on the contained object.
   C) The contained object's lifecycle is tied to the container object.
   D) The lifecycles of the objects are completely unrelated.

**Answer: C**

5. Which statement is true about the association relationship?
   A) It is always a one-to-one relationship between objects.
   B) It can be one-to-one, one-to-many, many-to-one, or many-to-many.
   C) It only allows for a one-to-many relationship.
   D) It is a special case of inheritance.

**Answer: B**

6. In the context of UML diagrams, how is aggregation represented?
   A) By a filled diamond.
   B) By a hollow diamond.
   C) By a solid line.
   D) By a dashed line.

**Answer: B**

7. Which of the following scenarios is an example of composition?
   A) A library has books.
   B) A car has an engine.
   C) A university has students.
   D) A shopping cart has products.

**Answer: B**

8. How does aggregation differ from composition when it comes to object ownership?
   A) Aggregation implies shared ownership, while composition implies exclusive ownership.
   B) Aggregation and composition both imply exclusive ownership.
   C) Aggregation implies exclusive ownership, while composition implies shared ownership.
   D) Neither aggregation nor composition implies any form of ownership.

**Answer: A**

9. If a class `Car` has an instance variable of type `Engine`, which relationship does it suggest?
   A) Association
   B) Aggregation
   C) Composition
   D) Inheritance

**Answer: C**

10. Which of the following is not a characteristic of the 'composition' relationship in Java?
    A) The composed object can exist without the composing object.
    B) The composed object is created within the composing object.
    C) The composed object is destroyed when the composing object is destroyed.
    D) The composed object cannot be accessed by any other object than the composing object.

**Answer: A**

# Code Design Problem: Routing and Storage System

Develop a routing and storage system that consists of three main components:

1. **Partition**
2. **Folder**
3. **File**

**Specifications:**

- A **Partition** can contain between zero to four **Folders**. Attempting to create a fifth folder should result in an exception regarding size limitations.
- A **Folder** can contain between zero to eight **Files**. Attempting to create a ninth file should result in an exception regarding size limitations.

**Object-Oriented Principles:**

Ensure that the design adheres to object-oriented principles, focusing on the relationships between the components.

**Attributes:**

Each **File**, **Partition**, and **Folder** must have at least the following attributes:

- Name
- Type
- Amount of free space available

The system should be designed with scalability and maintainability in mind, allowing for future enhancements and modifications.
