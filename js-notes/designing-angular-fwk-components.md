# Designing Angular Framework components

Structuring the components is an integral part of designing an effective angular application. We need to ensure separation of concerns for each component within the application. Following the same approach for an enterprise application, we need to categorize which component is your **presentation** component and which is your **smart** component, which interacts with the services.

# Use Case
In this article, we will be using an example of a products page.

Let's say, we are displaying a products catalog page. For displaying the products, we identify two components
1.  Catalog Component
2.  Product list Component

## Catalog Component
Catalog component is responsible for interacting with the Angular HTTP service to fetch the data from REST API. Here is the service code

<script src="https://gist.github.com/smuralee/1f105278274d01c4397825bd325d2c96.js"></script>

The service returns an `Observable` and is invoked by the Catalog component. The catalog component will be responsible to pass the data to the child component i.e. Product list Component.

<script src="https://gist.github.com/smuralee/9872670221f69e6142343ae725a2fdc4.js"></script>

The child component is being referenced via the HTML i.e. `./catalog.component.html`

As seen here, `[products]` is an input parameter, adorned with *@Input() decorators*. The catalog component becomes our **smart** component

## Product list Component
The Product list component will only respond to the data being fed from the parent. It is unaware of the existence of the product service and awaits only the products data being sent from the catalog component.

<script src="https://gist.github.com/smuralee/5d6c25ca1f434a9e823e17f824a9bd09.js"></script>

Hence this component is only responsible for **presentation**







