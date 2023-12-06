# 1. Naming Conventions:
## 1.1. Classes, Structs, and Enums:
Choose names for classes and structs that tell us what they represent. Use PascalCase for these names.


```csharp
public class CalculateCost { ... }
public struct VehicleModel { ... }
public enum VehicleStates { ... }
```

## 1.2. Interfaces:
Begin interface names with I and then use PascalCase for the rest of the name. Make sure the name conveys what the interface does.

```charp
public interface IFileManager { ... }
```

## 1.3. Methods and Functions:
Use names for methods that explain what they do. These should also be in PascalCase.

```csharp
public void CalculateTotalPrice(Order order) { ... }
```

## 1.4. Variables and Fields:
Pick meaningful names for variables that describe what they hold. Use camelCase for these names.

```csharp
// YES
int itemCount = 10;

// NO
int a = 10;
```

Private variables should have an underscore (_) prefix attached to them. To save additional keystrokes, avoid using the keyword private as private int _a; as it is the same as int _a;

```csharp
// NO
private int a;
int a;

// YES
int _a;
float _rotationY;
```
How about the access modifiers between public and private? Do I have to use a _ as well?

```csharp
public int a;

protected internal int _b;
protected int _c
interal int _d;
private protected int _e;

// Don't use `private` in this case
int _f;
```

## 1.5. Constants:
For constants, use SCREAMING_CAPS which are uppercase letters separated by underscores. Name them so that it's clear what they represent.

```csharp
const int MAX_RETRY_COUNT = 3;
```

## 1.6. Parameters:
Give parameters descriptive names. These should also use camelCase.

```charp
public void UpdateCustomerInfo(int customerId, CustomerData newData) { ... }
```

#2. Formatting:
## 2.1. Indentation and Braces:
Use one tab for each indentation level. Start curly braces on the line after the corresponding statement or declaration.

```csharp
if (condition)
{
    // code here
}
else
{
    // code here
}
```

## 2.2. Line Length:
Although we don’t enforce line lengths its best to keep your lines around 100-120 characters maximum. If a line is too long, break it into multiple lines.

```csharp
var longVariableName = someObject.SomeMethodWithLongName(
  parameter1,
  parameter2,
  parameter3);
```

## 2.3.1 Class Comments:
Use XML comments to document public APIs, parameters, return values, and exceptions.
> NOTE: When you change the parameters or functionality of the method or function, remember to update the XML comment for that function

```csharp
/// <summary>
/// Calculates the total price for the given order.
/// </summary>
/// <param name="order">The order to calculate the total for.</param>
/// <returns>The total price of the order.</returns>
public decimal CalculateTotal(Order order) { ... }
type three forward slashes - /// to generate the above template in VS  and VS code.
```

## 2.3.2 In-line Comments:
When you want to add some notes about what your code does and why it is done in this way, add inline comments to clearly state your purpose.

```csharp
public decimal CalculateTotal(Order order) 
{ 
  // GST value based on the location of the order
  order += GST(); 
}
```

## 2.4. Blank Lines:
Insert blank lines to separate different logical sections within a method or class.
Example:

```csharp
public void ProcessOrder(Order order)
{
    // Logic for preparation...

    // Blank line for separation
    ProcessItems(order.Items);

    // Logic for finalization...
}
```

## 2.5. Using Directives:
Put your using directives at the top of the file, outside of any namespaces. Group related directives together.

```csharp
using System;
using System.Collections.Generic;

namespace MyNamespace
{
    // Class and namespace definitions...
}
```

## 2.5.1 Related Directive Grouping:

Format your directives in this order:

1. C# Directives

2. Unity Directives

3. 3rd Party Directives

```csharp
using System;
using System.Collections.Generic;

using UnityEngine;
using UnityEngine.SceneManagement;

using DO.Tween;
using TMPro;
```

# 3. General Guidelines:
## 3.1. Consistency:
Make sure your code follows the style guide everywhere. If you're working on an existing project, stick to the existing style of the project unless judgement says otherwise.

## 3.2. Error Handling:
Use try-catch blocks to handle exceptions properly. Catch specific exceptions first and then more general ones.

```csharp
try
{
    // Code that might throw an exception...
}
catch (SpecificException ex)
{
    // Handle specific exception...
}
catch (Exception ex)
{
    // Handle other exceptions...
}
```

## 3.3. Single Responsibility Principle (SRP):
Aim for each method and class to do one thing really well. Avoid having methods that handle too many tasks and break down large methods into smaller ones that each have a clear purpose.

## 3.4. Avoid Magic Numbers and Strings:
Instead of using raw numbers or strings in your code, create constants with descriptive names.

```csharp
const int MAX_RETRY_COUNT = 3;
int remainingRetries = MAX_RETRY_COUNT;
```

## 3.5 Prefer Type Declaration over var:
Use explicit type declarations when the variable’s type isn’t immediately clear, enhancing code clarity and maintainability

```csharp
// YES
List<string> names = GetNames(); // Clear type declaration

//NO
var age = 30; // We now that the type is evident from the assignment
```

# 4. switch / if-else if Condition Guidelines:
## 4.1 Use Early Returns / Guard Clauses :
Instead of nesting if conditions, it's a good practice to return early when a condition is not met. This approach makes the code easier to follow and reduces the indentation level.

Additionally, consider using guard clauses to check preconditions at the beginning of a function. If a precondition is not met, you can either return early or throw an exception, depending on the severity of the violation.

```csharp
public void ProcessData(Data data)
{
    if (data == null)
    {
        return;
    }
    // Process data...
}

public void ProcessData(Data data)
{
    if (data == null)
    {
        throw new ArgumentNullException(nameof(data));
    }
    // Process data...
}
```

## 4.2 Should I use switch or if-else if?
In summary, the choice between switch and if-else if depends on the nature of your conditions and your coding convention. switch is ideal for comparing values against constants, improving code readability, and streamlining maintenance. For complex conditions, if-else if remains a valuable option.


Use switch for comparing a value against constants to enhance readability. We usually favor switch statements for optimized execution


```csharp
switch (day)
{
  case 1: return "Sunday";
  case 2: return "Monday";
  // ... (other days) 
  default: return "Invalid Day";
}

// C# 8.0 Switch Expression
public static string GetDayOfWeek(DayOfWeek day)
{
    return day switch
    {
        DayOfWeek.Monday => "It's Monday!",
        DayOfWeek.Tuesday => "It's Tuesday!",
        DayOfWeek.Wednesday => "It's Wednesday!",
        DayOfWeek.Thursday => "It's Thursday!",
        DayOfWeek.Friday => "It's Friday!",
        DayOfWeek.Saturday => "It's Saturday!",
        DayOfWeek.Sunday => "It's Sunday!",
        _ => "Invalid day of the week"
    };
}
```
For complex conditions, consider using if-else if structures. Try and put the most likely cases at the top for performance reasons to avoid extra condition checks.

```csharp
if (order.TotalPrice > 1000 && order.CustomerType == CustomerType.Premium)
{
  /* ... */
}
else if (order.TotalPrice > 500) 
{
  /* ... */
}
else
{
  /* ... */
}
```

## 4.3 Ternary Operators:
Use ternary operators for simple conditional assignments or expressions; they're concise and replace if conditions effectively. But remember, never, ever use nested ternary operators – they seriously mess up code clarity and should be avoided at all costs.

```csharp
// YES
string status = (age >= 18)? "Adult" : "Minor";

// NO
 string result = (score >= 90) ? "A" : (score >= 80) ? "B" : (score >= 70) ? "C" : "F";
```

# 5. Code Smells :poop: 
## 5.1 Duplicated Code
Classes and functions should be written to limit the amount of similar or identical code. If there is lots of copy-pasted code or code that looks very similar, it will be brittle and will be riddled with bugs over the course of a project. Try and unify the code to make it as short as possible; this will also make it easier to read and debug.

## 5.2 Magic Numbers / Strings
Magic numbers are hard-coded numeric values lacking any context. They reduce code readability and make updates error-prone. To remedy this, replace magic numbers with named constants and comment why a constant was needed.

## 5.3 Global Variables
Avoid the use global variables to prevent polluting the namespace with variables. Use variables in the appropriate scope or use gets/set methods to access them explicitly.

## 5.4 Deep indentation
Excessively nested code makes it hard to read and follow. No code should be more than 3 indents deep. To address this, refactor by reduce nesting by using early returns, and breaking down complex logic into smaller functions.

## 5.5 Shotgun Surgery
If a single change in one file requires many files or places in files to be changed to accommodate, it may be that the code is too rigid. 

## 5.6 Large classes
A class that is over 1000 lines long is probably too complex to be able to manage properly. Break the functionality out into other classes to make the class easier to manage and understand.

## 5.7 Long Methods
No method/function should be longer than 150 lines long, and ideally under 100 lines. If there are long functions, their scope is too large and they should be refactored or broken into smaller functions.

## 5.8 Cyclomatic complexity
If the code has too many branches or loops, it needs to be simplified/refactored or needs to be broken up into smaller functions.

## 5.9 Too many parameters
Having too many input parameters makes it hard to understand and use. To address this, refactor by grouping related parameters into objects or structuring the code to minimize the number of inputs, promoting cleaner and more concise functions.

## 5.10 Inappropriate Intimacy 
Is when a class has dependencies on implementation details of another class. Classes should generally not be built with assumptions on how other classes are implemented. Use interfaces or redesign the system to encapsulate your code appropriately.

## 5.11 Lack of Adherence to the Principle of Least Privilege
Granting excessive permissions, access, or privileges that go beyond what is necessary may cause potential security vulnerability or misconfiguration. Review and reduce the level of access and permissions granted to the code or component so that you mitigate the risk of unauthorized access or misuse of resources.

## 5.12 Dead code
Code that is deprecated or no longer used is dead code. It should be deleted as you replace it with newer code or systems by that programmer.
