Refactor the `AlertService` and `AlertDAO` classes:

- Create a new interface, named `IAlertDAO`, that contains the same methods as `AlertDAO`.
- `AlertDAO` should implement the `IAlertDAO` interface.
- `AlertService` should have a constructor that accepts `IAlertDAO`.
- The `RaiseAlert` and `GetAlertTime` methods should use the object passed through the constructor.

``` csharp
using System;
using System.Collections.Generic;

public class AlertService	
{
    private readonly AlertDAO storage = new AlertDAO();
	
    public Guid RaiseAlert()
    {
        return this.storage.AddAlert(DateTime.Now);
    }
	
    public DateTime GetAlertTime(Guid id)
    {
        return this.storage.GetAlert(id);
    }	
}
	
public class AlertDAO
{
    private readonly Dictionary<Guid, DateTime> alerts = new Dictionary<Guid, DateTime>();
	
    public Guid AddAlert(DateTime time)
    {
        Guid id = Guid.NewGuid();
        this.alerts.Add(id, time);
        return id;
    }
	
    public DateTime GetAlert(Guid id)
    {
        return this.alerts[id];
    }	
}
```

<details><summary>Answer</summary>

``` csharp
using System;
using System.Collections.Generic;

public class AlertService	
{
    // Don't change private members names...
    // They are used by the TestDome testing engine
    private readonly IAlertDAO storage;

    public AlertService(IAlertDAO alertDao)
    {       
        storage = alertDao;
    }

    public Guid RaiseAlert()
    {
        return storage.AddAlert(DateTime.Now);
    }

    public DateTime GetAlertTime(Guid id)
    {
        return storage.GetAlert(id);
    }	
}

public interface IAlertDAO
{
    Guid AddAlert(DateTime time);
    DateTime GetAlert(Guid id);
}

public class AlertDAO : IAlertDAO
{
    private readonly Dictionary<Guid, DateTime> alerts = new Dictionary<Guid, DateTime>();

    public Guid AddAlert(DateTime time)
    {
        var id = Guid.NewGuid();
        alerts.Add(id, time);
        return id;
    }

    public DateTime GetAlert(Guid id)
    {
        return alerts[id];
    }	
}
```

</details>

