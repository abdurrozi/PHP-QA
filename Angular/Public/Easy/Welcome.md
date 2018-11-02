Consider the following component:

``` typescript
import { Component, Input } from '@angular/core';

@Component({
  selector: 'welcome',
  template: `<h1>Welcome to {{name}}!</h1>`,
  styles: [`h1 { font-family: Lato; }`]
})
export class WelcomeComponent  {
  @Input() name: string;
}
```

Select the statements about its use (in another components template) that are correct.

_(multiple correct answers possible)_

- `<welcome name="TestDome"></welcome> will display: "Welcome to TestDome!".`
- `<welcome></welcome>` will display nothing.
- `@NgModule({ declarations: [ WelcomeComponent ] }) export class WelcomeModule {}` declares that the welcome component belongs to the welcome module.
- `<hello name="{{ name }}"></hello>` will display: `"Welcome to name!"`.

<details><summary>Answer</summary>

> - `<welcome name="TestDome"></welcome> will display: "Welcome to TestDome!".`
> - `@NgModule({ declarations: [ WelcomeComponent ] }) export class WelcomeModule {}` declares that the welcome component belongs to the welcome module.

</details>
