Implement function `CountNumbers` that accepts a sorted array of unique integers and, efficiently with respect to time used, counts the number of array elements that are less than the parameter lessThan.

For example, `SortedSearch.CountNumbers(new int[] { 1, 3, 5, 7 }, 4)` should return `2` because there are two array elements less than `4`.

``` csharp
using System;

public class SortedSearch
{
    public static int CountNumbers(int[] sortedArray, int lessThan)
    {
        throw new NotImplementedException("Waiting to be implemented.");
    }

    public static void Main(string[] args)
    {
        Console.WriteLine(SortedSearch.CountNumbers(new int[] { 1, 3, 5, 7 }, 4));
    }
}
``` 

<details><summary>Answer</summary>

``` csharp
using System;

public class SortedSearch
{
    public static int CountNumbers(int[] sortedArray, int lessThan)
    {
        var index = Array.BinarySearch(sortedArray, lessThan);

        if (index < 0)
        {
            // Bitwise complement of the bigger neighbour
            index = ~index;
        }

        return index;
    }

    public static void Main(params string[] args)
    {
        Console.WriteLine(SortedSearch.CountNumbers(new [] { 1, 3, 5, 7 }, 4));
    }
}
```

</details>
