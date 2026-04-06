# ExpressionEvaluator

A mathematical expression evaluator built with .NET 10 and C#. It parses and evaluates infix expressions (e.g. `2*7/4-(8-9^(1/2))+6`) using the **shunting-yard algorithm** to convert them to postfix notation, then computes the result from the postfix representation.

## Supported Operators

| Operator | Description    | Precedence |
|----------|----------------|------------|
| `^`      | Exponentiation | Highest    |
| `*` `/`  | Multiplication, Division | Medium |
| `+` `-`  | Addition, Subtraction | Lowest |
| `(` `)`  | Grouping       | —          |

## Projects

| Project | Type | Description |
|---------|------|-------------|
| **ExpressionEvaluator.Core** | Class Library | Contains the `Evaluator` class with the parsing and evaluation logic. |
| **ExpressionEvaluator.UI.Console** | Console App | Demonstrates expression evaluation with sample expressions. |
| **ExpressionEvaluator.UI.Win** | Windows Forms App | GUI front-end (in progress). |

## Getting Started

```bash
# Build the solution
dotnet build

# Run the console application
dotnet run --project ExpressionEvaluator.UI.Console
```

## Usage

```csharp
using ExpressionEvaluator.Core;

double result = Evaluator.Evaluate("4*(5+6-(8/2^3)-7)-1");
```

## How It Works

1. **Infix to Postfix** — The input expression is converted from infix notation to postfix (Reverse Polish Notation) using the shunting-yard algorithm, which handles operator precedence and parentheses.
2. **Postfix Evaluation** — The postfix expression is evaluated using a stack-based approach: operands are pushed onto the stack, and each operator pops its operands, computes the result, and pushes it back.
