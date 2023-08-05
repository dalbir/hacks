# Extracted data in JSON format from select
If you want to extract select options from an HTML file using JavaScript code embedded in a webpage, you can refer to the HTML content using the document object.

```javascript

// Replace 'your_html_string' with the actual HTML content you provided
// var your_html_string = `<!-- Your HTML content here -->`;
// var parser = new DOMParser();
// var doc = parser.parseFromString(your_html_string, 'text/html');
// var selectFields = doc.querySelectorAll('select');

var selectFields = document.querySelectorAll('select');
var optionsData = {};

selectFields.forEach(function(selectField) {
    var fieldName = selectField.getAttribute('name'); // You might need to adjust this based on the actual HTML structure
    var options = [];

    selectField.querySelectorAll('option').forEach(function(option) {
        var value = option.value;
        var text = option.textContent.trim();
        options.push({"value": value, "text": text});
    });

    optionsData[fieldName] = options;
});

var jsonData = JSON.stringify(optionsData, null, 2);

console.log(jsonData);
```

With this code, you don't need to provide the HTML content as a string. Instead, the JavaScript code operates directly on the HTML elements present in the currently loaded webpage. Just follow these steps:

- Open your web browser (Chrome, Firefox, etc.) and navigate to the webpage containing the HTML you want to extract select options from.

- Open the browser's developer console. You can usually do this by right-clicking on the page, selecting "Inspect" or "Inspect Element," and then navigating to the "Console" tab.

- In the developer console, paste the modified JavaScript code into the console and press Enter.

- The extracted options data in JSON format will be displayed in the console.

Remember to adjust the code if your HTML structure differs from the assumptions made in the code, especially when selecting fields and their attributes.

Here's the extracted data example in JSON format:
```json
{
  "batchCardField1": [
    { "value": "", "text": "" },
    { "value": "158201", "text": "CTA Clinical Research Report" },
    { "value": "158202", "text": "CTA End Of Trial" },
    /* ... other options ... */
    { "value": "177219", "text": "GMO Response to Competent Authority" }
  ],
  "batchCardField2": [
    { "value": "", "text": "" },
    { "value": "158237", "text": "Adam Paida" },
    { "value": "158253", "text": "Amira Caus" },
    /* ... other options ... */
    { "value": "193069", "text": "Wesley Smith" }
  ],
  /* ... other fields ... */
  "batchCardField10": [
    { "value": "", "text": "" },
    { "value": "163509", "text": "01. Not Selected" },
    { "value": "163510", "text": "02. 1-10" },
    /* ... other options ... */
    { "value": "163522", "text": "14. 261-300" }
  ]
}
```
