The following code initializes three types representing the colors: red, green and blue.

``` typescript
type ColorType = [string, number, number, number];
let red: ColorType = ['Red', 1, 0, 0];
let green: [string, number, number, number] = ['Green', 0, 1, 0];
let blue = ['Blue', 0, 0, 1];
```

Select the statements that are correct.

_(multiple correct answers possible)_

- All three colors can have new elements of any type appended to them.
- `ColorType` is an alias to a tuple.
- All three colors would compile to the same JavaScript type signature.
- `ColorType` is an array where the type of a fixed number of elements is known.
- All three variables are immutable.

<details><summary>Answer</summary>

> - `ColorType` is an alias to a tuple.
> - All three colors would compile to the same JavaScript type signature.
> - `ColorType` is an array where the type of a fixed number of elements is known.

</details>
