# Prototype Pattern
-----------
- ```The Prototype pattern is a creational design pattern that allows you to create new objects based on existing instances of those objects, instead of creating new instances from scratch ```
-  ```In this pattern, a "prototype" object is created and then copied to create new objects, rather than instantiating new objects from scratch each time.```
-  ```This can be useful when creating new objects is expensive or time-consuming, or when you want to ensure that new objects are similar to existing objects.```

--------
```
class Person implements Cloneable {
    private String name;
    private int age;
    
    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }
    
    @Override
    public Object clone() throws CloneNotSupportedException {
        return super.clone();
    }
    
    public void setName(String name) {
        this.name = name;
    }
    
    public String getName() {
        return name;
    }
    
    public void setAge(int age) {
        this.age = age;
    }
    
    public int getAge() {
        return age;
    }
}

public class CloneDemo {
    public static void main(String[] args) {
        Person p1 = new Person("Alice", 25);
        try {
            Person p2 = (Person) p1.clone();
            System.out.println("p1 name: " + p1.getName() + ", age: " + p1.getAge());
            System.out.println("p2 name: " + p2.getName() + ", age: " + p2.getAge());
            p2.setName("Bob");
            p2.setAge(30);
            System.out.println("p1 name: " + p1.getName() + ", age: " + p1.getAge());
            System.out.println("p2 name: " + p2.getName() + ", age: " + p2.getAge());
        } catch (CloneNotSupportedException e) {
            e.printStackTrace();
        }
    }
}
```

- ```Although the clone() method creates a new object, it can still be more efficient than creating a new object from scratch. This is because the clone() method avoids the overhead of calling a constructor, which can involve costly operations such as allocating memory and initializing fields.```
- ```Instead, the clone() method creates a new object with the same initial state as the original object. The new object can then be modified as needed, potentially saving time and resources compared to creating a new object and initializing all its fields from scratch.```
- ```However, it's worth noting that the efficiency of using the clone() method depends on the specific implementation and the complexity of the object being cloned. In some cases, it may be more efficient to use other techniques such as object pooling ```
