Write a function that provides change directory (cd) function for an abstract file system.

Notes:

- Root path is `'/'`.
- Path separator is `'/'`.
- Parent directory is addressable as `".."`.
- Directory names consist only of English alphabet letters (`A-Z` and `a-z`).
- The function should support both relative and absolute paths.
- The function will not be passed any invalid paths.
Do not use built-in path-related functions.

For example:

``` csharp
var path = new Path("/a/b/c/d");
path.Cd("../x");
Console.WriteLine(path.CurrentPath);
```

``` csharp
using System;
using System.Linq;

public class Path
{
    public string CurrentPath { get; private set; }

    public Path(string path)
    {
        this.CurrentPath = path;
    }

    public void Cd(string newPath)
    {
        var newP = newPath.Split('/');
        var oldP = CurrentPath.Split('/');
        var lnCount = newP.Count(str => str.Equals(".."));

        var len = oldP.Length;
        var strOut = "";
        for (var i = 0; i < len - lnCount; i++)
        {
            strOut = strOut + oldP[i] + "/";
        }

        len = newP.Length;
        for (var i = 0; i < len; i++)
        {
            if (!newP[i].Equals(".."))
            {
                strOut = strOut + newP[i] + "/";
            }
        }
        CurrentPath = strOut.Substring(0, strOut.Length - 1);
    }

    public static void Main(string[] args)
    {
        Path path = new Path("/a/b/c/d");
        path.Cd("../x");
        Console.WriteLine(path.CurrentPath);
    }
}
```

<details><summary>Answer</summary>

``` csharp
using System;
using System.Text;
using System.Linq;

public class Path
{
    private const char Separator = '/';
    private const string ParentString = "..";

    public string CurrentPath { get; private set; }

    public Path(string currentPath)
    {
        CurrentPath = currentPath;
    }

    public void Cd(string path)
    {
        var newPathParts = path.Split(Separator);
        var oldPathParts = CurrentPath.Split(Separator);
        var newPathPartCount = newPathParts.Count(part => part.Equals(ParentString));

        var oldPathPartCount = oldPathParts.Length;
        var stringBuilder = new StringBuilder();

        for (var i = 0; i < oldPathPartCount - newPathPartCount; i++)
        {
            stringBuilder.Append(oldPathParts[i] + Separator);
        }

        oldPathPartCount = newPathParts.Length;

        for (var i = 0; i < oldPathPartCount; i++)
        {
            if (!newPathParts[i].Equals(ParentString))
            {
                stringBuilder.Append(newPathParts[i] + Separator);
            }
        }

        CurrentPath = stringBuilder.Remove(stringBuilder.Length - 1, 1).ToString();
    }

    public static void Main(string[] args)
    {
        var path = new Path("/a/b/c/d");
        path.Cd("../x");
        Console.WriteLine(path.CurrentPath);
    }
}
```

</details>
