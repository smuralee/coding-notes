---
layout: post
title: "Designing Angular Framework components"
date: 2017-09-09
---

Structuring the components is an integral part of designing an effective angular application. We need to ensure separation of concerns for each component within the application. Following the same approach for an enterprise application, we need to categorize which component is your **presentation** component and which is your **smart** component, which interacts with the services.

# Use Case
In this article, we will be using an example of a products page.

Let's say, we are displaying a products catalog page. For displaying the products, we identify two components
1.  Catalog Component
2.  Product list Component

## Catalog Component
Catalog component is responsible for interacting with the Angular HTTP service to fetch the data from REST API. Here is the service code

```typescript
import {Injectable} from '@angular/core';
import {Http} from '@angular/http';
import {Observable} from 'rxjs/Observable';
import {Product} from '../models/product';

@Injectable()
export class ProductService {

    constructor(private _http: Http) {
    }

    getProducts(): Observable<Product[]> {
        return this._http.get('/products')
            .map(res => res.json())
            .catch(err => Observable.throw(err));
    }
}
```

The service returns an `Observable` and is invoked by the Catalog component. The catalog component will be responsible to pass the data to the child component i.e. Product list Component.

```typescript
import {Component, OnInit} from '@angular/core';
import {ProductService} from '../../services/product.service';
import {Observable} from 'rxjs/Observable';
import {Product} from '../../models/product';

@Component({
    selector: 'catalog',
    templateUrl: './catalog.component.html',
    styleUrls: ['./catalog.component.css']
})
export class CatalogComponent implements OnInit {

    private _products$: Observable<Product[]>;

    constructor(private _service: ProductService) {
    }

    ngOnInit(): void {
        this._products$ = this._service.getProducts();
    }

}
```

The child component is being referenced via the template - `./catalog.component.html`

```
<product-list [products]="_products$"></product-list>
```

As seen here, `[products]` is an input parameter, adorned with *@Input() decorators*. The catalog component becomes our **smart** component

## Product list Component
The Product list component will only respond to the data being fed from the parent. It is unaware of the existence of the product service and awaits only the products data being sent from the catalog component.

```typescript
import {Component, Input} from '@angular/core';
import {Product} from '../../models/product';

@Component({
   selector: 'product-list',
   templateUrl: './product-list.component.html',
   styleUrls: ['./product-list.component.css']
})
export class ProductListComponent {

   @Input()
   public products: Product[];

}
```

Below is the template `./product-list.component.html`

```
<div *ngFor="let product of products">{{product.name}}</div>
```

Hence this component is only responsible for **presentation**







