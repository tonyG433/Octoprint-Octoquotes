# Octoprint-Octoquotes
A repository for the ocoquotes plugin.

## MVP Requirements
* The plugin shall show a quote inside an Octoprint alert box when the user interface is loaded in the browser.
* A settings screen should be available where users can choose prevent certain quote categories from showing.
* The quote shall be chosen at random from a list of quotes upon page load.
* The list of quotes from which it chooses shall have a filter applied to it when categories are to be filtered out.
* Quotes shall be loaded from a JSON file inside the plugin's repo such as `quotes.json`
* The quotes.json data shall contain an array of objects formatted as such:
```
[
  {
    text: string,
    category: 'sarcastic' | 'quotes' | 'reminders',
    author: string,
    date: string,
    formatDate: boolean,
    url: string
  }
]
```
* `text` is a required field and shall contain the text of the quote.
* `category` is a required field and shall contain the name of the category this quote belongs to.
* `category` shall not be displayed as part of the quote alerts.
* The `author`, `date`, `formatDate` and `url` fields are all optional and will not be shown anywhere if not provided.
* The `date` field shall be a string to allow for more flexible options such as "circa 400BC"
* If an actual date is to be used, it shall be provided as an ISO 8601 date string (yyyy-mm-dd) such as 2021-05-25
* Where a date string has been provided as described above, `formatDate` should be set to `true`, it is otherwise assumed `false`.  This will cause the plugin to format the date using the appropriate date format for the user's region according to their browser.
* If `url` is specified, the quote shall be displayed with a small icon along side it, indicating that a webpage with more information (perhaps the origin or the theory behind the quote) can be found.  Clicking this icon shall load the url in a new browser tab.
* All values being rendered into code shall be sanitised to prevent cross site scripting attacks.