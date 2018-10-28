Consider the following code:

``` csharp
public class Crab 
{
    public virtual string PinchClaws()
    {
        return "clap clap";
    }
}

public class CoconutCrab : Crab
{
    public override string PinchClaws()
    {
        return "CLAP CLAP";
    }
}
```

Select the statements that are correct.

_(multiple correct answers possible)_


- Calling `PinchClaws()` on an instance of `CoconutCrab` will return `"CLAP CLAP"`.
- Calling `PinchClaws()` on an instance of `Crab` will return `"CLAP CLAP"`.
- Casting an instance of `CoconutCrab` into `Crab` and then calling the - `PinchClaws` method will return `"clap clap"`.
- Casting an instance of `Crab` into `CoconutCrab` will throw an exception.

<details><summary>Answer</summary>

> - Calling `PinchClaws()` on an instance of `CoconutCrab` will return `"CLAP CLAP"`.
> - Casting an instance of `Crab` into `CoconutCrab` will throw an exception.

</details>
