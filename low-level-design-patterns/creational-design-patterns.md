# Creational Design Patterns

The "Creational Design Patterns" section in "Dive into Design Patterns" covers five fundamental patterns that help in creating objects in a manner suitable for the situation. These patterns abstract the instantiation process, making the system independent of how its objects are created, composed, and represented. Here's a summary of each creational design pattern discussed:

1. **Factory Method**:
   - **Purpose**: Defines an interface for creating an object but allows subclasses to alter the type of objects that will be created.
   - **Usage**: When a class can't anticipate the type of objects it needs to create or when a class wants its subclasses to specify the objects to be created.

2. **Abstract Factory**:
   - **Purpose**: Provides an interface for creating families of related or dependent objects without specifying their concrete classes.
   - **Usage**: When the system needs to be independent of the way its objects are created or when families of related objects need to be used together.

3. **Builder**:
   - **Purpose**: Separates the construction of a complex object from its representation, allowing the same construction process to create different representations.
   - **Usage**: When creating complex objects where the construction process needs to allow different representations or configurations.

4. **Prototype**:
   - **Purpose**: Specifies the kind of objects to create using a prototypical instance and creates new objects by copying this prototype.
   - **Usage**: When a system needs to be independent of how its products are created, composed, and represented, or when instances of a class can have one of only a few different combinations of state.

5. **Singleton**:
   - **Purpose**: Ensures a class has only one instance and provides a global point of access to it.
   - **Usage**: When exactly one instance of a class is needed to control actions like configuration settings or when an object that is expensive to create should only be instantiated once.

These patterns offer different approaches to object creation, helping to increase flexibility and reuse of existing code. By abstracting the instantiation process, creational patterns enable developers to write more robust and scalable software.