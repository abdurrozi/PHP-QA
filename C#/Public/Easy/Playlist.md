A playlist is considered a repeating playlist if any of the songs contain a reference to a previous song in the playlist. Otherwise, the playlist will end with the last song which points to null.

Implement a function `IsRepeatingPlaylist` that, efficiently with respect to time used, returns `true` if a playlist is repeating or `false` if it is not.

For example, the following code prints `"True"` as both songs point to each other.

``` csharp
Song first = new Song("Hello");
Song second = new Song("Eye of the tiger");
    
first.NextSong = second;
second.NextSong = first;

Console.WriteLine(first.IsRepeatingPlaylist());
``` 

``` csharp
using System;

public class Song
{
    private string name;
    public Song NextSong { get; set; }
 
    public Song(string name)
    {
        this.name = name;
    }
    
    public bool IsRepeatingPlaylist()
    {
        throw new InvalidOperationException("Waiting to be implemented.");
    }
    
    public static void Main(string[] args)
    {
        Song first = new Song("Hello");
        Song second = new Song("Eye of the tiger");
    
        first.NextSong = second;
        second.NextSong = first;
    
        Console.WriteLine(first.IsRepeatingPlaylist());
    }
}
``` 

<details><summary>Answer</summary>

``` csharp
using System;
using System.Collections.Generic;

public class Song
{
    private readonly string _name;
    public Song NextSong { get; set; }
 
    public Song(string name)
    {
        this._name = name;
    }
    
    public bool IsRepeatingPlaylist()
    {
        var previousSongNames = new HashSet<Song>();

        var currentSong = this;
        while (currentSong != null)
        {
            if (!previousSongNames.Add(currentSong))
            {
                return true;
            }
            
            currentSong = currentSong.NextSong;
            
        }

        return false;
    }
    
    public static void Main(params string[] args)
    {
        var first = new Song("Hello");
        var second = new Song("Eye of the tiger");
    
        first.NextSong = second;
        second.NextSong = first;
    
        Console.WriteLine(first.IsRepeatingPlaylist());
    }
}
```

</details>
