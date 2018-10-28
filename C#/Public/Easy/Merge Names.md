Implement the `UniqueNames` method. When passed two arrays of names, it will return an array containing the names that appear in either or both arrays. The returned array should have no duplicates.

For example, calling `MergeNames.UniqueNames(new string[]{'Ava', 'Emma', 'Olivia'}, new string[]{'Olivia', 'Sophia', 'Emma'})` should return an array containing `"Ava"`, `"Emma"`, `"Olivia"`, and `"Sophia"` in any order.


``` csharp
using System;

public class MergeNames
{
    public static string[] UniqueNames(string[] names1, string[] names2)
    {
        throw new NotImplementedException();
    }
    
    public static void Main(string[] args)
    {
        string[] names1 = new string[] {"Ava", "Emma", "Olivia"};
        string[] names2 = new string[] {"Olivia", "Sophia", "Emma"};
        Console.WriteLine(string.Join(", ", MergeNames.UniqueNames(names1, names2))); // should print Ava, Emma, Olivia, Sophia
    }
}
``` 

<details><summary>Answer</summary>

``` csharp
using System;
using System.Linq;
using System.Collections.Generic;

public class MergeNames
{
    public static string[] UniqueNames(string[] names1, string[] names2)
    {
        var commonNames = new HashSet<string>();
        
        if (names1 != null)
        {
            foreach(var name in names1)
            {
                commonNames.Add(name);
            }
        }

        
        if (names2 != null)
        {
            foreach(var name in names2)
            {
                commonNames.Add(name);
            }
        }
        
        return commonNames.ToArray();
    }
    
    public static void Main(params string[] args)
    {
        var names1 = new string[] {"Ava", "Emma", "Olivia"};
        var names2 = new string[] {"Olivia", "Sophia", "Emma"};
        
        // should print Ava, Emma, Olivia, Sophia
        Console.WriteLine(string.Join(", ", MergeNames.UniqueNames(names1, names2))); 
    }
}
```

</details>
