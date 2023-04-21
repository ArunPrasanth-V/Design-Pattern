# Null Object Design Pattern 
----------
- ``` The Null Object pattern is a design pattern used in object-oriented programming to represent the absence of an object. Instead of using a null reference to indicate the absence of an object```
- ```We create an abstract class specifying various operations to be done, concrete classes extending this class``` 
- ``` and a null object class providing do nothing implementation of this class```

# Example
 ```
 // Java program to illustrate Null
// Object Design Pattern

abstract class Emp
{
	protected String name;
	public abstract boolean isNull();
	public abstract String getName();
}

class Coder extends Emp
{
	public Coder(String name)
	{
		this.name = name;
	}
	@Override
	public String getName()
	{
		return name;
	}
	@Override
	public boolean isNull()
	{
		return false;
	}
}

class NoClient extends Emp
{
	@Override
	public String getName()
	{
		return "Not Available";
	}

	@Override
	public boolean isNull()
	{
		return true;
	}
}

class EmpData
{
	
	public static final String[] names = {"Lokesh", "Kushagra", "Vikram"};
	public static Emp getClient(String name)
	{
		for (int i = 0; i < names.length; i++)
		{
			if (names[i].equalsIgnoreCase(name))
			{
				return new Coder(name);
			}
		}
		return new NoClient();
	}
}

public class Main
{
	public static void main(String[] args)
	{
		Emp emp1 = EmpData.getClient("Lokesh");
		Emp emp2 = EmpData.getClient("Kushagra");
		Emp emp3 = EmpData.getClient("Vikram");
		Emp emp4 = EmpData.getClient("Rishabh");


		System.out.println(emp1.getName());
		System.out.println(emp2.getName());
		System.out.println(emp3.getName());
		System.out.println(emp4.getName());
	}
}
```
