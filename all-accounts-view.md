# All Accounts View

## https://github.com/ted-ncg/labs/blob/master/all-accounts-view.md

### References

* Thymeleaf 3: http://www.thymeleaf.org/doc/tutorials/3.0/usingthymeleaf.html#using-and-displaying-variables

## Lab Instructions

1. Create an HTML "template" (name it `all-accounts.html) in the `resources/templates` folder underneath the `/src/main` folder:

    ```
      <!DOCTYPE html>
      <html lang="en" xmlns:th="http://www.thymeleaf.org" >
      <head>
        <meta charset="UTF-8">
        <title>Accounts</title>
      </head>
      <body>
      <table>
        <tr>
          <th>Account ID</th>
          <th>Balance</th>
        </tr>
        <tr>
          <td>Account ID:<span>10</span></td>
          <td>Balance: $<span>99</span></td>
        </tr>
      </table>
      </body>
      </html>
    ```

1. Add in the th:text and th:each attributes in the span as needed. For example, if we were working with a collection of `products`:

       <tr th:each="product : ${products}">
         <td th:text="${product.name}">Onions</td>
         <td th:text="${product.price}">2.41</td>
       </tr>
    
1. Create a `WebController` class annotated with `@Controller`

1. Inject the `AccountRepository` into your `WebController` class.

1. Create a `@GetMapping()` to `/account/` that displays all accounts.

    * Add a `Model model` as your parameter to the method
    * use the `model.addAttribute()` method to add the account list to the name `"accounts"`
    * Return a `String` with the name of the html template you created in the first step -- **without** the `.html` suffix.

1. If you hit `localhost:8080/account/` you should see all of the accounts.