# Csharp-Coding-Convention-Template
Example Coding Convention Template for C# if you do not know where to start.

## 1. Naming Conventions
### 1.1. Classes and Structs
Choose names for classes and structs that tell us what they represent. Use PascalCase for these names.
Example:

```csharp
public class CalculateCost { ... }
```
### 1.2. Interfaces
Begin interface names with 'I' and then use PascalCase for the rest of the name. Make sure the name conveys what the interface does.
Example:

```csharp
public interface IFileManager { ... }
```

### 1.3. Methods and Functions
Use names for methods that explain what they do. These should also be in PascalCase.
Example:

```csharp
public void CalculateTotalPrice(Order order) { ... }
```

### 1.4. Variables and Fields
Pick meaningful names for variables that describe what they hold. Use camelCase for these names.
Example:

```csharp
// YES
int itemCount = 10;

// NO
int a = 10;
```

### 1.5. Constants
For constants, use uppercase letters separated by underscores. Name them so that it's clear what they represent.
Example:

```csharp
const int MAX_RETRY_COUNT = 3;
```

### 1.6. Parameters
Give parameters descriptive names. These should also use camelCase.
Example:

```csharp
public void UpdateCustomerInfo(int customerId, CustomerData newData) { ... }
```

## 2. Formatting
### 2.1. Indentation and Braces
Use 4 spaces for each indentation level. Start curly braces on the same line as the corresponding statement or declaration.
Example:

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

## 2.2. Line Length
Keep your lines around 100-120 characters maximum. If a line is too long, break it into multiple lines.
Example:

```csharp
var longVariableName = someObject.SomeMethodWithLongName(
  parameter1,
  parameter2,
  parameter3);
```
### 2.3. Comments
Use XML comments to document public APIs, parameters, return values, and exceptions. Add inline comments when needed.
Example:

```csharp
/// <summary>
/// Calculates the total price for the given order.
/// </summary>
/// <param name="order">The order to calculate the total for.</param>
/// <returns>The total price of the order.</returns>
public decimal CalculateTotal(Order order) { ... }
```

### 2.4. Blank Lines
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

### 2.5. Using Directives
Put your using directives at the top of the file, outside of any namespaces. Group related directives together.

Example:

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
