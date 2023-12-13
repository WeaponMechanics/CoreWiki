# Color

```yaml
Color: <String>
```

There are 3 valid formats for colors: `simple`, `rgb`, and `hex`. (Pick whichever one you like the most. I prefer `hex`)

Colors using the `simple` format are like the vanilla minecraft chat colors. Here is the predefined list:

* `"black"`
* `"dark_blue"`
* `"dark_green"`
* `"dark_aqua"`
* `"dark_red"`
* `"dark_purple"`
* `"gold"`
* `"gray"`
* `"dark_gray"`
* `"blue"`
* `"green"`
* `"aqua"`
* `"red"`
* `"light_purple"`
* `"yellow"`
* `"white"`

To use the `rgb` format, use `red-green-blue`. For example, purple could look like this: `255-0-255`. Online color calculators should have support for rgb.

For `hex`, use `#<code>`, where \<code> is the 6 digit hex. [Online color calculators](https://htmlcolorcodes.com/color-picker/) should have support for hex

Examples:

```yaml
Color: "red" # RED
```

```yaml
Color: "255-0-0" # RED 
```

```yaml
Color: "#FF0000" # RED
```
