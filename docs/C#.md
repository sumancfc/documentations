# Learning C# Programming Language

The information in this README were learned from various resources, including the excellent tutorials and documentation available at [W3Schools](https://www.w3schools.com/).  I highly recommend checking them out for further learning.

## Basic Concepts

### Comments

- Single-line comments start with `//`.
- Multi-line comments start with `/*` and end with `*/`.

### Data Types

This document describes the basic data types in C#, their sizes, and their uses.

| Data Type | Size (bytes) | Description |
|----------|---|---|
| `int`    | 4 | Stores whole numbers from -2,147,483,648 to 2,147,483,647. |
| `long`   | 8 | Stores whole numbers from -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807. |
| `float`  | 4 | Stores fractional numbers. Sufficient for storing 6 to 7 decimal digits. |
| `double` | 8 | Stores fractional numbers. Sufficient for storing 15 decimal digits. |
| `bool`   | 1 | Stores `true` or `false` values. |
| `char`   | 2 | Stores a single character/letter, surrounded by single quotes (e.g., 'A', '$'). |
| `string` | 2 bytes per character | Stores a sequence of characters, surrounded by double quotes (e.g., "Hello, World!"). |

`Note`: The `string` data type is an object, not a primitive type.  Strings are immutable, meaning they cannot be changed after they are created.
Use single quotes for `char` and double quotes for `string`.
### Type Casting

In C#, there are two types of casting:

- Implicit Casting (automatically) - converting a smaller type to a larger type size

```csharp
Char -> Int -> Long -> Float -> Double
```

- Explicit Casting (manually) - converting a larger type to a smaller size type

```csharp
Double -> Float -> Long -> Int -> Char
```

### Type Conversion Methods

- `ToBoolean`, `ToChar`, `ToSByte`, `ToByte`, `ToInt16`, `ToUInt16`, `ToInt32`, `ToUInt32`, `ToInt64`, `ToUInt64`, `ToSingle`, `ToDouble`, `ToDecimal`, `ToString`

```csharp
int myInt = 10;
double myDouble = 5.25;
bool myBool = true;

Console.WriteLine(Convert.ToString(myInt));    // convert int to string
Console.WriteLine(Convert.ToDouble(myInt));    // convert int to double
Console.WriteLine(Convert.ToInt32(myDouble));  // convert double to int
Console.WriteLine(Convert.ToString(myBool));   // convert bool to string
```

### User Input

To get user input in C#, use the `Console.ReadLine()` method.

```csharp
Console.WriteLine("Enter your name:");
string name = Console.ReadLine();
Console.WriteLine("Your name is: " + name);
```

`Note`: `Console.ReadLine()` method returns a string. If you want to convert it to other data types, you need to do it explicitly.

```csharp
Console.WriteLine("Enter your age:");
int age = Convert.ToInt32(Console.ReadLine());
Console.WriteLine("Your age is: " + age);
```

### Operators

This section describes the arithmetic operators in C#.

| Operator | Name | Description | Example |
|---|---|---|---|
| `+` | Addition | Adds together two values. | `x + y` |
| `-` | Subtraction | Subtracts one value from another. | `x - y` |
| `*` | Multiplication | Multiplies two values. | `x * y` |
| `/` | Division | Divides one value by another. | `x / y` |
| `%` | Modulus | Returns the division remainder. | `x % y` |
| `++` | Increment | Increases the value of a variable by 1. | `x++` |
| `--` | Decrement | Decreases the value of a variable by 1. | `x--` |

### Strings

Strings are used for storing text in C#. A string is a sequence of characters enclosed in double quotes.
Methods that are available for strings include:
`.Length`, `.ToUpper()`, `.ToLower()`, `.Trim()`, `.IndexOf()`, `.Substring()`, `.Replace()`, `.Split()`

Concatenation is the process of combining two strings. In C#, you can concatenate strings using the `+` operator or the `string.Concat()` method.

**Warning**: C# uses the + operator for both addition and concatenation.

**Remember**: Numbers are added. Strings are concatenated.

**String Interpolation** is the process of evaluating string literals containing one or more placeholders. Each placeholder is enclosed in curly braces `{}`.

```csharp
string firstName = "John";
string lastName = "Doe";
string name = $"My full name is: {firstName} {lastName}";
Console.WriteLine(name);
```

`Note:` The dollar sign `$` is required when using the string interpolation method.  It signals to the compiler that the string should be interpolated.

### Escape Sequences

Escape sequences are special character combinations that represent characters that cannot be directly typed or have special meaning within strings in C#. They begin with a backslash (`\`) followed by a character code.

Here's a table of common escape sequences in C#:

| Escape Sequence | Description | Example | Output |
|---|---|---|---|
| `\n` | Newline. Inserts a line break. | `Console.WriteLine("Hello\nWorld!");` | Hello<br>World! |
| `\r` | Carriage return. Moves the cursor to the beginning of the current line. Often used in combination with `\n` (e.g., `\r\n` for Windows line endings). | `Console.WriteLine("Hello\rWorld!");` (May vary depending on the system) | World! (Overwrites "Hello") |
| `\t` | Horizontal tab. Inserts a tab character. | `Console.WriteLine("Name\tAge");` | Name    Age |
| `\b` | Backspace. Deletes the character to the left of the cursor. | `Console.WriteLine("Hello\b!");` | Hello! |
| `\f` | Form feed. Advances the printer to the next page (may not have a visible effect in console applications). | `Console.WriteLine("Page 1\fPage 2");` (May not be visible in console) | Page 1<br>Page 2 (If supported) |
| `\'` | Single quote. Inserts a single quote character.  Needed when you want a single quote *inside* a string that's delimited by single quotes. | `Console.WriteLine('\'');` | ' |
| `\"` | Double quote. Inserts a double quote character. Needed when you want a double quote *inside* a string that's delimited by double quotes. | `Console.WriteLine("\"Hello\"");` | "Hello" |
| `\\` | Backslash. Inserts a backslash character. Needed when you want a literal backslash. | `Console.WriteLine("C:\\path\\to\\file");` | C:\path\to\file |
| `\0` | Null character. Represents the null character (Unicode character U+0000). | `Console.WriteLine("Null: \0");` (May not be visible) | Null:  |
| `\uXXXX` | Unicode character. Represents a Unicode character using its 4-digit hexadecimal code.  | `Console.WriteLine("\u0048\u0065\u006C\u006C\u006F");` | Hello |
| `\xXX` | Unicode character. Represents a Unicode character using its 2-digit hexadecimal code. | `Console.WriteLine("\x48\x65\x6C\x6C\x6F");` | Hello |
| `@""` (Verbatim strings) | Not an escape sequence, but related: A verbatim string literal. Treats all characters inside the string literally, including backslashes. Useful for file paths or regular expressions. | `string path = @"C:\My\File.txt";` | C:\My\File.txt |

**When to use escape sequences:**

* When you need to include characters that have special meaning in strings (like quotes or backslashes).
* When you need to represent characters that are not easily typed (like tabs or newlines).
* When working with Unicode characters.

### Switch Statement

Use `switch` statements to select one of many code blocks to be executed.

```csharp
switch (expression)
{
    case constant-expression:
        statement(s);
        break; // optional
    case constant-expression:
        statement(s);
        break; // optional
    // you can have any number of case statements
    default:
        statement(s);
        break; // optional
}
```

### Loops

While loop: It loops through a block of code as long as a specified condition is `True`:

```csharp
while (condition)
{
    // code block to be executed
}
```
Do-While loop: It loops through a block of code once, and then repeats the loop as long as a specified condition is `True`:

```csharp
do
{
    // code block to be executed
}
while (condition);
```

### For Loop

```csharp
for (initialization; condition; increment/decrement)
{
    // code block to be executed
}
```

### For Each Loop

It is used to loop through an array or collection.

```csharp
foreach (type variableName in arrayName)
{
    // code block to be executed
}
```
