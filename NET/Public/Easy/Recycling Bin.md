Consider the following code:

``` csharp
public class RecyclingBin
{
    protected List<string> recyclables = new List<string>();
    
    public void Add(string recyclable)
    {
        if (recyclable.Split(' ').Length > 1)
        {
            recyclables.Add(recyclable);
        }
    }
    
    public List<IGrouping<string, string>> SortRecyclables()
    {
        return recyclables
        .GroupBy(recyclable => recyclable.Split(' ').First())
        .ToList();
    }
}
```

Select the statements that are `true` if a new `RecyclingBin` is instantiated and the `Add` method is called with the following recyclable parameters: `"metal pipe"`, `"plastic toy"`, `"metal bar"`, `"copper wire"`, and `"plastic button"`.

_(multiple correct answers possible)_
- One of the groups returned from `SortRecyclables` will have `"metal"` as its key and will contain `"metal bar"` and `"metal pipe"`.
- One of the groups returned from `SortRecyclables` will have `"wire"` as its key and will contain `"copper wire"`.
- The `List` returned from `SortRecyclables` will not be evaluated in the `SortRecyclables` method.
- The `Add` method will add a new recyclable only if it contains a space.

<details><summary>Answer</summary>

- One of the groups returned from `SortRecyclables` will have `"metal"` as its key and will contain `"metal bar"` and `"metal pipe"`.
- The `Add` method will add a new recyclable only if it contains a space.

</details>
