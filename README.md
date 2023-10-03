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

## 3. General Guidelines
### 3.1. Consistency
Make sure your code follows the style guide everywhere. If you're working on an existing project, stick to the existing style.

### 3.2. Error Handling
Use try-catch blocks to handle exceptions properly. Catch specific exceptions first and then more general ones.
Example:

``` csharp
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

### 3.3. Single Responsibility Principle (SRP)
Aim for each method and class to do one thing really well. Avoid having methods that handle too many tasks.
Example:
Break down large methods into smaller ones that each have a clear purpose.

### 3.4. Avoid Magic Numbers and Strings
Instead of using raw numbers or strings in your code, create constants with descriptive names.
Example:

```csharp
const int MAX_RETRY_COUNT = 3;
int remainingRetries = MAX_RETRY_COUNT;
```

### 3.5. Use Language Features Wisely
Make the most of C#'s features like LINQ and async/await when they make your code clearer.
Example:

```csharp
var discountedProducts = products.Where(p => p.Price < 50);
await ProcessDataAsync();
```

## 4. Tools and Automation
### 4.1. Code Analysis
Utilize tools that automatically check your code against the style guide. These tools can help catch deviations.

Example:
Set up StyleCop or other code analysis tools to run as part of your build process.

### 4.2. Code Reviews
Regularly review each other's code to ensure it follows the style guide and discuss any deviations.

Example:
During code reviews, not only focus on functionality but also on maintaining consistent coding practices.

## 5. Documentation and Readability
### 5.1. XML Documentation
Document public methods, classes, and properties using XML comments. Describe their purpose and usage.

Example:
Provide comprehensive XML comments that explain how to use your code.

### 5.2. Meaningful Naming
Prioritize clear and descriptive names over clever or cryptic ones. Make your code self-explanatory.

Example:
Choose names that anyone reading your code can understand without needing extensive comments.

### 5.3. Modularity and Structure
Divide your code into smaller, logically organized functions and classes. Use namespaces to group related code.

Example:
Structure your codebase to make it easy to find and understand different parts of your application.
