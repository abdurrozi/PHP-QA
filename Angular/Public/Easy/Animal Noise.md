Consider the following component, which can be used to model an animal and the noise it makes.

``` typescript
import {Component, Input, Output} from '@angular/core';

@Component({
  selector: 'animal-noise',
  template: `
    <span>{{animal}}</span>
    <button (click)="makeNoise()">Make noise</button>
  `
})
export class AnimalNoise {
  @Input('animal') animal: string;
  @Input('noise') noise: string;

  makeNoise() {
    alert(`${this.noise}`);
  }
}
```

Select the statements about the `AnimalNoise` component that are correct.

_(multiple correct answers possible)_

- Component, `Input` and `Output` are all required imports for this component.
- Both animal and noise inputs must be provided when including the `AnimalNoise` component in a template.
- The `'animal'` parameter of the `@Input('animal')` declaration does not alter the interface of the component.
- When included in a components template, the `AnimalNoise` component creates a span containing the interpolated animals name and a button bound to `makeNoise()`.
- The `AnimalNoise` component can be included in another template using the `<AnimalNoise>` tag.

<details><summary>Answer</summary>

> - The `'animal'` parameter of the `@Input('animal')` declaration does not alter the interface of the component.
> - When included in a components template, the `AnimalNoise` component creates a span containing the interpolated animals name and a button bound to `makeNoise()`.

</details>
