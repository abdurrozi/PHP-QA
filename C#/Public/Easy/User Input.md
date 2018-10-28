User interface contains two types of user input controls: `TextInput`, which accepts all characters and `NumericInput`, which accepts only digits.

Implement the class `TextInput` that contains:

- `public void Add(char c)`: adds the given character to the current value
- `public string GetValue()`: returns the current value

Implement the class NumericInput that:

- Inherits `TextInput`
- Overrides the `Add` method so that each non-numeric character is ignored

For example, the following code should output `"10"`:

``` csharp
TextInput input = new NumericInput();
input.Add('1');
input.Add('a');
input.Add('0');
Console.WriteLine(input.GetValue());
``` 

``` csharp
using System;

public class TextInput {}

public class NumericInput {}

public class UserInput
{
    public static void Main(string[] args)
    {
        //TextInput input = new NumericInput();
        //input.Add('1');
        //input.Add('a');
        //input.Add('0');
        //Console.WriteLine(input.GetValue());
    }
}
``` 

<details><summary>Answer</summary>

``` csharp
using System;
using System.Text;

public class TextInput
{
    private readonly StringBuilder _stringBuilder = new StringBuilder();

    public virtual void Add(char c)
    {
        _stringBuilder.Append(c);
    }

    public string GetValue()
    {
        return _stringBuilder.ToString();
    }
}

public class NumericInput : TextInput
{
    public override void Add(char c)
    {
        if (char.IsDigit(c))
        {
            base.Add(c);
        }
    }
}

public class UserInput
{
    public static void Main(params string[] args)
    {
        var input = new NumericInput();
        input.Add('1');
        input.Add('a');
        input.Add('0');
        Console.WriteLine(input.GetValue());
    }
}
``` 

</details>
