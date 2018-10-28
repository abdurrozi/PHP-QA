A `TrainComposition` is built by attaching and detaching wagons from the left and the right sides, efficiently with respect to time used.

For example, if we start by attaching wagon `7` from the left followed by attaching wagon `13`, again from the left, we get a composition of two wagons (`13` and `7` from left to right). Now the first wagon that can be detached from the right is `7` and the first that can be detached from the left is `13`.

Implement a `TrainComposition` that models this problem.

``` csharp
using System;

public class TrainComposition
{
    public void AttachWagonFromLeft(int wagonId)
    {
        throw new NotImplementedException("Waiting to be implemented.");
    }

    public void AttachWagonFromRight(int wagonId)
    {
        throw new NotImplementedException("Waiting to be implemented.");
    }

    public int DetachWagonFromLeft()
    {
        throw new NotImplementedException("Waiting to be implemented.");
    }

    public int DetachWagonFromRight()
    {
        throw new NotImplementedException("Waiting to be implemented.");
    }

    public static void Main(string[] args)
    {
        TrainComposition tree = new TrainComposition();
        tree.AttachWagonFromLeft(7);
        tree.AttachWagonFromLeft(13);
        Console.WriteLine(tree.DetachWagonFromRight()); // 7 
        Console.WriteLine(tree.DetachWagonFromLeft()); // 13
    }
}
``` 

<details><summary>Answer</summary>

``` csharp
using System;
using System.Collections.Generic;

public class TrainComposition
{
    private readonly LinkedList<int> _linkedList = new LinkedList<int>();

    public void AttachWagonFromLeft(int wagonId)
    {
        _linkedList.AddFirst(wagonId);
    }

    public void AttachWagonFromRight(int wagonId)
    {
        _linkedList.AddLast(wagonId);
    }

    public int DetachWagonFromLeft()
    {
        var wagonId = _linkedList.First.Value;
        _linkedList.RemoveFirst();
        return wagonId;
    }

    public int DetachWagonFromRight()
    {
        var wagonId = _linkedList.Last.Value;
        _linkedList.RemoveLast();
        return wagonId;
    }
    
    public static void Main(params string[] args)
    {
        var trainComposition = new TrainComposition();
        trainComposition.AttachWagonFromLeft(7);
        trainComposition.AttachWagonFromLeft(13);

        // Should return 7 
        Console.WriteLine(trainComposition.DetachWagonFromRight()); 

        // Should return 13 
        Console.WriteLine(trainComposition.DetachWagonFromLeft());
    }
}
```

</details>
