# OOP Concepts

## Polymorphism

Polymorphism is a concept in object-oriented programming that allows objects of different classes to be treated as objects of a common superclass. It enables a single interface to represent multiple types of objects and allows methods to be defined in a superclass and overridden in subclasses.

### Types of Polymorphism

There are two main types of polymorphism in C#:

1. `Compile-Time Polymorphism (Static Polymorphism):` This type of polymorphism is resolved at compile time.  The compiler determines which method to call based on the types of the variables or arguments.  C# achieves compile-time polymorphism through:   

- **Method Overloading:** Defining multiple methods in the same class with the same name but different parameters (different number, types, or order of parameters).  The compiler chooses the correct method based on the arguments provided.

```csharp
public class Calculator
{
    public int Add(int a, int b)
    {
    return a + b;
    }

    public double Add(double a, double b) // Method overloading
    {
        return a + b;
    }

    public string Add(string a, string b) // Method overloading
    {
        return a + b;
    }
}

Calculator calc = new Calculator();
int sum1 = calc.Add(5, 10);        // Calls the first Add method
double sum2 = calc.Add(5.5, 10.2); // Calls the second Add method
string sum3 = calc.Add("Hello", "World"); // Calls the third Add method
```

- **Operator Overloading:** Defining how operators (like +, -, *, /) behave when applied to objects of a user-defined class.

```csharp
public class ComplexNumber
{
    public double Real { get; set; }
    public double Imaginary { get; set; }

    public ComplexNumber(double real, double imaginary)
    {
        Real = real;
        Imaginary = imaginary;
    }

    public static ComplexNumber operator +(ComplexNumber a, ComplexNumber b) // Operator overloading
    {
        return new ComplexNumber(a.Real + b.Real, a.Imaginary + b.Imaginary);
    }
}

ComplexNumber c1 = new ComplexNumber(2, 3);
ComplexNumber c2 = new ComplexNumber(4, 5);
ComplexNumber c3 = c1 + c2; // Uses the overloaded + operator
```

2. `Runtime Polymorphism (Dynamic Polymorphism):` This type of polymorphism is resolved at runtime. The decision about which method to call is made based on the actual type of the object at runtime, not the declared type of the variable. C# achieves runtime polymorphism through:   

- **Method Overriding (with virtual and override):** This is the most common and important form of runtime polymorphism.  It involves a base class declaring a method as virtual (allowing derived classes to override it) and derived classes using the override keyword to provide their own implementation.

```csharp
// 1. Base Class (Shape)
public abstract class Shape
{
    public string Color { get; set; } // Common property

    public Shape(string color)
    {
        Color = color;
    }

    public abstract void Draw(); // Abstract method (forces implementation in derived classes)

    public virtual string GetShapeType() // Virtual method (can be overridden)
    {
        return "Unknown Shape";
    }
}

// 2. Derived Classes (Circle, Rectangle)
public class Circle : Shape
{
    public double Radius { get; set; }

    public Circle(string color, double radius) : base(color)
    {
        Radius = radius;
    }

    public override void Draw() // Overriding the abstract method
    {
        Console.WriteLine($"Drawing a {Color} circle with radius {Radius}");
    }

    public override string GetShapeType() // Overriding the virtual method
    {
        return "Circle";
    }
}

public class Rectangle : Shape
{
    public double Width { get; set; }
    public double Height { get; set; }

    public Rectangle(string color, double width, double height) : base(color)
    {
        Width = width;
        Height = height;
    }

    public override void Draw() // Overriding the abstract method
    {
        Console.WriteLine($"Drawing a {Color} rectangle with width {Width} and height {Height}");
    }

    public override string GetShapeType() // Overriding the virtual method
    {
        return "Rectangle";
    }
}

// 3. Using Polymorphism
public class DrawingApplication
{
    public static void Main(string[] args)
    {
        List<Shape> shapes = new List<Shape>(); // List of Shape objects

        shapes.Add(new Circle("Red", 5));       // Adding a Circle
        shapes.Add(new Rectangle("Blue", 10, 7)); // Adding a Rectangle

        foreach (Shape shape in shapes) // Iterating through the list of Shapes
        {
            shape.Draw(); // Polymorphic call to Draw()
            Console.WriteLine($"Shape Type: {shape.GetShapeType()}"); // Polymorphic call to GetShapeType()
        }
    }
}
```
