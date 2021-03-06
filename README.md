[Live demo!](https://benpong.com/dine_dash/)

jBerry is a JavaScript library that can be used for manipulating, traversing and event handling in the DOM. While the functions of jBerry can accomplished with vanilla Javascript, utilizing jBerry allows for DRY and shorter code.

Include the following script inside of your HTML document.

```
<script type="text/javascript" src="./lib/jberry.js" charset="utf-8"></script>
```

The core function of jBerry is `$b(arg)`. This function utilizes vanilla DOM function `querySelectorAll()` to select and return a Nodelist of HTML elements that match the arg. Once we have the Nodelist, we convert the Nodelist into an array and pass it in as a new instance of a DOMNodeCollection. jBerry methods are defined inside of this class.

#### jBerry methods include:

| Function                 | Description                                                                     |
| ------------------------ | ------------------------------------------------------------------------------- |
| `html()`                 | Returns the HTML contents of the array                                          |
| `find(selector)`         | Returns the descendants of each elements in the array that matches the selector |
| `append()`               | Inserts content to the end of each element in the array                         |
| `attr(attributeName)`    | Get or set an attribute for a specific element in the array                     |
| `children()`             | Returns the children of each element in the array                               |
| `addClass(className)`    | Adds classNames to each element in the array                                    |
| `removeClass(className)` | Removes classNames from each element in the array                               |
| `remove()`               | Removes the set of matched elements from the DOM                                |
| `empty()`                | Clears the content of all nodes in the internal array                           |
| `on()`                   | Attach an event handler function for one or more events                         |

### jBerry function examples

Bill calculating event submission listener

```
$b("#bill-form").on("submit", event => {
  event.preventDefault();
  let amountRaw = $b("#amount-input").array[0].value;
  let peopleRaw = $b("#people-input").array[0].value;
  let tipPercentRaw = $b("#tip-input").array[0].value;

  if (amountRaw.includes('$')) {
    amountRaw = amountRaw.replace('$', '')
  }

  if (tipPercentRaw.includes('%')) {
    tipPercentRaw = tipPercentRaw.replace('%', '')
  }

  const amount = Number(amountRaw);
  const people = Number(peopleRaw);
  const tipPercent = (Number(tipPercentRaw) / 100)
  const tipTotal = amount * tipPercent;
  const perPerson = ((amount + tipTotal) / people.toFixed(2));
  $b(".calculated-amount").append(`$${perPerson}`);
});
```
