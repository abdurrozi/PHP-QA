A palindrome is a word that reads the same backward or forward.

Write a function that checks if a given word is a palindrome. Character case should be ignored.

For example, `IsPalindrome("Deleveled")` should return true as character case should be ignored, resulting in `"deleveled"`, which is a palindrome since it reads the same backward and forward.

``` csharp
using System;

public class Palindrome
{
    public static bool IsPalindrome(string word)
    {
        throw new NotImplementedException("Waiting to be implemented.");
    }

    public static void Main(string[] args)
    {
        Console.WriteLine(Palindrome.IsPalindrome("Deleveled"));
    }
}
```

<details><summary>Answer</summary>

``` csharp
using System;

public class Palindrome
{
    public static bool IsPalindrome(string word)
    {
        if (word == null)
        {
            return true;
        }
        
        var length = word.Length;

        var half = length / 2;

        var isOddLength = length % 2;

        var j = isOddLength == 0 ? 
            half:
            half + 1;

        for(var i = half - 1; i >= 0; i--)
        {                
            if(char.ToLower(word[i]) != char.ToLower(word[j]))
            {
                return false;
            }
            j++;

        }
        
        return true;
    }

    public static void Main(params string[] args)
    {
        Console.WriteLine(Palindrome.IsPalindrome("Deleveled"));
    }
}
```

</details>

