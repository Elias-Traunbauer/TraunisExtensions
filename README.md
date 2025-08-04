# Trauni's Extensions

[![NuGet](https://img.shields.io/nuget/v/TraunisExtensions.svg)](https://www.nuget.org/packages/TraunisExtensions/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

A small collection of useful C# extension methods and utilities to enhance your .NET development experience.

## Installation

Install the package via NuGet Package Manager:
dotnet add package TraunisExtensions
Or via Package Manager Console:
Install-Package TraunisExtensions
## Features

### Collection Extensions

#### Foreach Extensions
Execute actions on collections with enhanced foreach methods:
using TraunisExtensions;

// Execute action on each element
var numbers = new[] { 1, 2, 3, 4, 5 };
numbers.Foreach(x => Console.WriteLine(x * 2));

// Transform and return new collection
var doubled = numbers.ForeachReturn(x => x * 2);
### 2D Array Extensions

#### Array Rotation
Rotate 2D arrays by 90 degrees to the right:
int[,] matrix = { { 1, 2 }, { 3, 4 } };
var rotated = matrix.Rotate();
// Result: { { 3, 1 }, { 4, 2 } }
#### 2D Array Iteration
Iterate through 2D arrays with position information:
int[,] grid = { { 1, 2, 3 }, { 4, 5, 6 } };

// Execute action on each element with coordinates
grid.Foreach((x, y, value) => Console.WriteLine($"[{x},{y}] = {value}"));

// Execute action on selected elements only
grid.Foreach((x, y, value) => Console.WriteLine($"Even: {value}"), 
             value => value % 2 == 0);
#### Array Analysis
Find specific values in 2D arrays:
int[,] data = { { 0, 1, 0 }, { 0, 0, 1 }, { 1, 0, 0 } };

// Get the lowest row index where condition is true in column 1
int row = data.GetLowestValueAtColumn(value => value == 1, column: 1);
#### Array Size Information
Get array dimensions as a Size object:
var size = matrix.GetSize(); // Returns Size(width, height)
### Point Extensions

Enhanced Point operations for graphics and coordinate manipulation:
using System.Drawing;

Point p1 = new Point(10, 20);
Point p2 = new Point(5, 15);

// Add points
Point sum = p1.Add(p2); // (15, 35)
Point offset = p1.Add(5, 10); // (15, 30)

// Multiply points
Point product = p1.Multiply(p2); // (50, 300)
Point scaled = p1.Multiply(3); // (30, 60)

// Set console cursor position
p1.SetAsConsoleCursorPosition(); // Sets cursor to (10, 20)
### Object Cloning

Create deep clones of objects using reflection:
var original = new MyClass { Property1 = "value", Property2 = 42 };
var clone = original.Clone();
**Note:** The Clone method uses reflection and creates a shallow copy for reference types within the object.

### Enum Extensions

High-performance flag checking for enums:
[Flags]
enum MyFlags
{
    None = 0,
    Flag1 = 1,
    Flag2 = 2,
    Flag3 = 4
}

MyFlags flags = MyFlags.Flag1 | MyFlags.Flag3;
bool hasFlag = flags.FastHasFlag(MyFlags.Flag1); // true
## Requirements

- .NET 6.0 or later
- System.Drawing (for Point extensions)

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request to the [GitHub repository](https://github.com/Elias-Traunbauer/TraunisExtensions).

## License

This project is licensed under the MIT License - see the [LICENSE](https://opensource.org/licenses/MIT) for details.

## Author

**Elias Traunbauer (trauni)**

## Version History

- **2.0.0** - Current version with collection, array, point, and enum extensions
- Enhanced foreach methods for collections and arrays
- 2D array manipulation and analysis tools
- Point arithmetic operations
- Object cloning utilities
- High-performance enum flag checking

---

For more information and updates, visit the [GitHub repository](https://github.com/Elias-Traunbauer/TraunisExtensions).
