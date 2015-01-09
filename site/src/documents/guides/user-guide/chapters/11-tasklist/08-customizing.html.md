---

title: 'Customizing'
category: 'Tasklist'

---

You can override the default configuration of Tasklist using a central configuration file
located in `app/tasklist/scripts/config.js`. Currently, the following configuration options are
available:

##Date Format

Dates can be configured by specifying a `dateFormat` object. The values of the properties of this
object must be strings representing date formats in accordance to
[moment.js](http://momentjs.com). Following date formats are used within the tasklist:

- `monthName` represents the name of a month (e.g., January).
- `day` represents the number of a day in a month (1..31).
- `abbr` represents a short format of a date including time.
- `normal` represents the standard format of a date including time.
- `long` represents a verbose format of a date including time and day of the week.
- `short` represents a short format of a date excluding time.


###Example

```javascript
"dateFormat": {
  "monthName": "MMM",
  "long":   "LLLL"
}
```

## Localization

The localization of Tasklist is contained in the `app/tasklist/locales/` directory. This
directory contains a separate localization file for every available language. The file name
consists of the language code and the suffix `.json` (e.g. `en.json`).

Tasklist uses a locale file corresponding to the language settings of the browser. You can
set the `availableLocales` property in the configuration file to provide a list of available
locales. The path to this configuration file is mentioned [above](ref:#tasklist-customizing).
Every locale which is contained in this list must have a locale file in the `locales`
directory with the corresponding language code.

If the browser uses a language which is not available, Tasklist uses the locale which is
defined via the `fallbackLocale` property in the configuration file:

```javascript
"locales": {
  "availableLocales": ["en", "de"],
  "fallbackLocale": "en"
}
```

To create a new localization for Tasklist, copy the provided language file, translate it and
save it as new localization file with the corresponding language code. To make the new translation
available, add it to the list of available locales in the configuration file.

## Logo and Header Color

To change visual aspects of Tasklist, you can edit the user stylesheet file located in
`app/tasklist/styles/user-styles.css`. This file contains CSS which is loaded into Tasklist
and can override the standard styles.

To display your own logo in the top-left corner, edit the `background-image` property of the
`.navbar-brand` to point to the URL of your logo image.

To set the color of the navigation bar (header), multiple properties have to be overwritten. You
can find an example in the default `user-styles.css` file.

## Advanced styles customization

In addition to the basic `user-styles.css` file, you can edit the source style- and layout files
using [less](http://lesscss.org/) to change the overall appearance of Tasklist.

If you want to customize the interface with `less`, you should probably start by having a look at the variables defined in the `client/styles/styles.less` and `client/bower_components/bootstrap/less/variables.less` files.

A sample file with variable overrides is available in the `client/styles` directory. To enable it, uncomment the line   
`// @import "_variables-override";` in `client/styles/styles.less`   
and re-compile the source.

### Compiling using grunt

From within the `camunda-tasklist-ui` directory:
```
grunt build
```
The command will build the whole frontend assets, styles included.
