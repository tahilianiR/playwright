### locators
https://playwright.dev/docs/locators



### select option
< select>   < option value="1">Jan</ option>   < option value="2">Feb</ option> </ select>
```ts
// Single selection matching the value or label
await page.getByLabel('Choose a color').selectOption('blue');

// Single selection matching the label
await page.getByLabel('Choose a color').selectOption({ label: 'Blue' });

// Single selection matching the value
await page.getByLabel('Choose a color').selectOption({ value: 'Blue' });

// Single selection matching the zero-based index
await page.getByLabel('Choose a color').selectOption({ index: 2 });


// Multiple selected items
await page.getByLabel('Choose multiple colors').selectOption(['red', 'green', 'blue']);
```

### My notes

1. Below is one example wherein in the DOM was like half broken so I used getByText which worked fine  : 

< span 
_ngcontent-ng-c916014599="" class="text">
"Clear Selections (11" 
<!---->
")" 
< /span >

```ts
      const clearSelection11: NamedLocator = { elementName: 'Clear Selections (11)', element: this.page.getByText("Clear Selections (11)") };
```
