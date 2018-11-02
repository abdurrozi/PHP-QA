Consider the following application module:

``` typescript
import { NgModule }             from '@angular/core';
import { RouterModule, Routes } from '@angular/router';
import { HomeComponent }        from './home.component';
import { ItemDetailComponent }  from './item-detail.component';
const routes: Routes = [
    { path: '', redirectTo: '/home', pathMatch: 'full' },
    { path: 'home',  component: HomeComponent },
    { path: 'detail/:id', component: ItemDetailComponent, outlet: 'route1' }
];
@NgModule({
    imports: [ RouterModule.forRoot(routes) ],
    exports: [ RouterModule ]
})
export class AppRoutingModule {}
``` 

Which of the following statements about the routers behavior are correct?

_(multiple correct answers possible)_


- The home component can only be accessed via the root URL redirect.
- The `id` parameter is optional when a call is made to the `/detail/` URL.
- Optional parameters can be passed to any component via the query parameters of the `ActivatedRoute`.
- `/detail/100` will use the `<router-outlet name='route1'>` to determine the position of the view.
- Specifying an outlet name is a requirement for a component with multiple outlet routes.

<details><summary>Answer</summary>

> - Optional parameters can be passed to any component via the query parameters of the `ActivatedRoute`.
> - `/detail/100` will use the `<router-outlet name='route1'>` to determine the position of the view.

</details>
