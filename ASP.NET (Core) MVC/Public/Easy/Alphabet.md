Select the code snippets that are valid in the Razor view engine, and when used, generate a paragraph containing the string: `"ABCDEFGHIJKLMNOPQRSTUVWXYZ"`.

_(multiple correct answers possible)_

``` csharp
<p>
    @for (char letter = 'A'; letter <= 'Z'; letter++)
    {<text>@letter</text>}
</p>
```

``` csharp
<p>
    @for (char letter = 'A'; letter <= 'Z'; letter++)
    {
        document.write(letter);
    }
</p>
```

``` csharp
@{
    StringBuilder sb = new StringBuilder();
    for (char letter = 'A'; letter <= 'Z'; letter++)
    {
        sb.Append(letter);
    }
}
<p>@sb.ToString()</p>
```

``` csharp
<p>
    @for (char letter = 'A'; letter <= 'Z'; letter++)
    {<span>letter</span>}
</p>
```

<details><summary>Answer</summary>

``` csharp
<p>
    @for (char letter = 'A'; letter <= 'Z'; letter++)
    {<text>@letter</text>}
</p>
```

``` csharp
@{
    StringBuilder sb = new StringBuilder();
    for (char letter = 'A'; letter <= 'Z'; letter++)
    {
        sb.Append(letter);
    }
}
<p>@sb.ToString()</p>
```

</details>
