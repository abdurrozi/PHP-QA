Consider the following code sample:

``` csharp
public class UserController : Controller
{
    [Route("/user")]
    public IActionResult GetUser()
    {
        return Content("Ask for specific user on URL: /user/{userId}");
    }

    [Route("/user/{userId}")]
    public IActionResult GetUserById(string userId)
    {
        return Content($"User with id: {userId}");
    }
}
```

Select which of the following URLs that will be routed to the `GetUserById` method.

_(multiple correct answers possible)_
- `/user/someid`
- `/user/user/1`
- `/user/123`
- `/user/21id`
- `/user/name/password`
- `/user/`

<details><summary>Answer</summary>

> - `/user/someid`
> - `/user/123`
> - `/user/21id`

</details>
