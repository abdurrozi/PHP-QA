The following code initializes strings as three different types and attempts to make them uppercase. Which statements about the behavior of the typescript compiler are correct?

``` typescript
let stringType: string = "string type";
stringType.toUpperCase();

let anyType: any = "any type";
anyType.toUpper();
anyType.toUpperCase();

let objectType: Object = "object type";
objectType.toUpperCase();
``` 

_(multiple correct answers possible)_

- The typescript compiler confirms that `toUpperCase` exists on the `stringType` instance.
- The typescript compiler states that `toUpper` does not exist on the anyType instance;
- The typescript compiler confirms that `toUpperCase` exists on the anyType instance.
- The typescript compiler states that the `toUpperCase` function does not exist on the `objectType` instance.
- The typescript compiler confirms that the `toUpperCase` function exists on the `objectType` instance.

<details><summary>Answer</summary>

> - The typescript compiler confirms that `toUpperCase` exists on the `stringType` instance.
> - The typescript compiler states that the `toUpperCase` function does not exist on the `objectType` instance.

</details>
