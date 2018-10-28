Implement a function FolderNames, which accepts a string containing an XML file that specifies folder structure and returns all folder names that start with startingLetter. The XML format is given in the example below.

For example, for the letter `'u'` and XML file:

``` xml
<?xml version="1.0" encoding="UTF-8"?>
<folder name="c">
    <folder name="program files">
        <folder name="uninstall information" />
    </folder>
    <folder name="users" />
</folder>
```

the function should return `"uninstall information"` and `"users"` (in any order).

``` csharp
using System;
using System.Collections.Generic;

public class Folders
{
    public static IEnumerable<string> FolderNames(string xml, char startingLetter)
    {
        throw new NotImplementedException("Waiting to be implemented.");
    }

    public static void Main(string[] args)
    {
        string xml =
            "<?xml version=\"1.0\" encoding=\"UTF-8\"?>" +
            "<folder name=\"c\">" +
                "<folder name=\"program files\">" +
                    "<folder name=\"uninstall information\" />" +
                "</folder>" +
                "<folder name=\"users\" />" +
            "</folder>";

        foreach (string name in Folders.FolderNames(xml, 'u'))
            Console.WriteLine(name);
    }
}
```

<details><summary>Answer</summary>

``` csharp
using System;
using System.Xml.Linq;
using System.Collections.Generic;

public class Folders
{
    public static IEnumerable<string> FolderNames(string xml, char startingLetter)
    {
        var xDocument = XDocument.Parse(xml);
        var folderElements = xDocument.Descendants("folder");
        foreach (var folderElement in folderElements)
        {
            var folderNameAttribute = folderElement.Attribute("name");
            if (folderNameAttribute != null &&
                folderNameAttribute.Value.StartsWith(startingLetter.ToString()))
            {
                yield return folderNameAttribute.Value;
            }
        }
    }

    public static void Main(params string[] args)
    {
        const string xml =
            "<?xml version=\"1.0\" encoding=\"UTF-8\"?>" +
            "<folder name=\"c\">" +
                "<folder name=\"program files\">" +
                    "<folder name=\"uninstall information\" />" +
                "</folder>" +
                "<folder name=\"users\" />" +
            "</folder>";

        foreach (var name in Folders.FolderNames(xml, 'u'))
        {
            Console.WriteLine(name);
        }
    }
}
```

</details>
