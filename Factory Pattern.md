# Factory Pattern
---------------
- ```The Factory Pattern is a creational design pattern that provides an interface for creating objects in a superclass but allows subclasses to alter the type of objects that will be created.```
- ```The idea behind the factory pattern is to provide a centralized place in your code where you can create objects of a certain type ```
- ```without the rest of your code needing to know how those objects are created```
- ```This allows you to easily swap out different implementations of those objects without having to make changes to the rest of your code.```
- ```The pattern involves creating a factory class with a method that creates objects of a certain type based on some input. ```
- ```The factory method can take parameters that specify the type of object to be created, and any additional information needed to create the object. ```

# Example
```
public interface Animal {
    String getName();
    String speak();
}

public class Dog implements Animal {
    private String name;

    public Dog(String name) {
        this.name = name;
    }

    @Override
    public String getName() {
        return name;
    }

    @Override
    public String speak() {
        return "Woof!";
    }
}

public class Cat implements Animal {
    private String name;

    public Cat(String name) {
        this.name = name;
    }

    @Override
    public String getName() {
        return name;
    }

    @Override
    public String speak() {
        return "Meow!";
    }
}

public class AnimalFactory {
    public static Animal createAnimal(String animalType, String name) {
        switch (animalType) {
            case "dog":
                return new Dog(name);
            case "cat":
                return new Cat(name);
            default:
                throw new IllegalArgumentException("Invalid animal type");
        }
    }
}

// Usage
Animal dog = AnimalFactory.createAnimal("dog", "Fido");
System.out.println(dog.getName() + " says " + dog.speak());

Animal cat = AnimalFactory.createAnimal("cat", "Whiskers");
System.out.println(cat.getName() + " says " + cat.speak());
```

# why we need a Factory Pattern

1 ***Encapsulation*** :
    - ```The Factory Pattern encapsulates object creation, so the client code does not need to know how the objects are created.```
    - ```This improves code maintainability, as it is easier to change the object creation logic in a single location without affecting the rest of the code```
    
 2 ***Abstarction*** :
    - ```he Factory Pattern allows for abstraction of the object creation process, which makes the code more flexible and easier to modify```
    - ```lients can request objects from the factory without knowing the exact class of the object they will receive.```
 
 3 ***Decoupling*** :
    - ``` The Factory Pattern decouples the client code from the object creation process```
    - ```  The client code only needs to know the interface of the objects it wants to use, not how they are created.```
    - ``` This improves code modularity and reduces dependencies between components ```
 
 4 ***Reusability*** :
    - ```The Factory Pattern promotes code reuse by allowing the creation of objects to be centralized in a single location.```
    - ```This avoids duplication of code and reduces the risk of errors.```
 
 5 ***Polymorphism*** :
    - ```The Factory Pattern supports polymorphism by allowing the creation of objects to be deferred to subclasses. ```
    - ```This allows different types of objects to be created based on runtime conditions or user input.```
    
   ***overall, the Factory Pattern is a powerful tool for improving code quality and maintainability by providing a flexible and modular approach to object creation.***
