bootstrap-checkbox-x
=====================

An extended checkbox plugin for Bootstrap built using JQuery, which allows three checkbox states and includes additional styles. The plugin uses Bootstrap markup and CSS 3 styling by default, but it can be overridden with any other CSS markup. It also helps you to fallback to a native checkbox OR display native checkboxes with tristate capability.

> NOTE: The checkbox plugin stores the values as integer format (and not boolean format) for checked and unchecked states.

## Features  

1. Enhances any HTML input (preferrably a checkbox or text input) with `data-toggle=checkbox-x` to an extended checkbox control. 
2. The plugin offers the following three states and values for the checkboxes:
   - `1`: Checkbox is checked.
   - `0`: Checkbox is unchecked.
   - `null`: Checkbox is indeterminate.
3. You can set the plugin to allow **three states** or the default **two states** for the checkbox.
4. Specifically uses Bootstrap 3.x styles & glyphs. One can configure the checked, unchecked, and indeterminate icons to be shown for the checkboxes.
5. Special CSS 3 styling, to enhance the control to look like any Bootstrap 3 form control. Supports the `has-error`, `has-success`, `has-warning`
   styling states like other Bootstrap form-controls.
6. Plugin CSS styling automatically defaults the checkboxes to inline display. You can also control the markup for block display like in checkbox lists.
7. You can add a `label` before or after with a `for` attribute and click on the label to change the checkbox values. Alternatively you can enclose the 
   input within a `label` tag as well.
8. Ability to navigate to the checkbox controls via keyboard, and modify the values using the `space` bar on the keyboard.
9. Ability to size the checkbox control. Five prebuilt size templates are available `xl`, `lg`, `md`, `sm`, and `xs`.
10. Triggers JQuery events for advanced development. The plugin automatically triggers the `change` event for the input, whenever the checkbox value is changed via clicking. Events currently available are `change` and  `reset`.
11. Ability to access methods and refresh the input dynamically via javascript at runtime.
12. Disabled and readonly checkbox input support.
13. Added support for displaying native checkboxes with tristate capability. When displaying native checkboxes, the advanced styling offerred by the plugin will not be available.

> NOTE: The latest version of the plugin v1.3.0 has been released. Refer the [CHANGE LOG](https://github.com/kartik-v/bootstrap-checkbox-x/blob/master/CHANGE.md) for details.

## Demo

View the [plugin documentation](http://plugins.krajee.com/checkbox-x) and [plugin demos](http://plugins.krajee.com/checkbox-x/demo) at Krajee JQuery plugins. 

## Pre-requisites  

1. [Bootstrap 3.x](http://getbootstrap.com/)
2. Latest [JQuery](http://jquery.com/)
3. Most browsers supporting CSS3 & JQuery. 

## Installation

### Using Bower
You can use the `bower` package manager to install. Run:

    bower install bootstrap-checkbox-x

### Using Composer
You can use the `composer` package manager to install. Either run:

    $ php composer.phar require kartik-v/bootstrap-checkbox-x "dev-master"

or add:

    "kartik-v/bootstrap-checkbox-x": "dev-master"

to your composer.json file

### Manual Install

You can also manually install the plugin easily to your project. Just download the source [ZIP](https://github.com/kartik-v/bootstrap-checkbox-x/zipball/master) or [TAR ball](https://github.com/kartik-v/bootstrap-checkbox-x/tarball/master) and extract the plugin assets (css and js folders) into your project.

## Usage

Step 1: Load the following assets in your header. 

```html
<link href="http://netdna.bootstrapcdn.com/bootstrap/3.2.0/css/bootstrap.min.css" rel="stylesheet">
<link href="path/to/css/checkbox-x.min.css" media="all" rel="stylesheet" type="text/css" />
<script src="//ajax.googleapis.com/ajax/libs/jquery/1.11.0/jquery.min.js"></script>
<script src="path/to/js/checkbox-x.min.js" type="text/javascript"></script>
```

If you noticed, you need to load the `jquery.min.js` and `bootstrap.min.css` in addition to the `checkbox-x.min.css` and `checkbox-x.min.js` for
the plugin to work with default settings.

Step 2: Setup your input markup with `data-toggle="checkbox-x"` to automatically initialize the checkbox control
```html
<input id="input-id" value="1" data-toggle="checkbox-x" data-three-state="true" data-size="lg" >
```

Step 3: You can also initialize the plugin on your page using javascript as well, instead of using `data-toggle` attribute as above. For example,

```html
<input id="input-id">
<script>
$(document).on("ready", function() {
    // initialize with defaults
    $("#input-id").checkboxX();

    // with plugin options
    $("#input-id").checkboxX({threeState: true, size:'lg'});
});
</script>
```

The `#input-id` is the identifier for the input on your page, which is hidden automatically by the plugin. 

Alternatively, you can directly call the plugin options by setting data attributes to your input field.

## Documentation

### Plugin Options
The plugin supports these following options:

##### threeState
_boolean_, whether to use three states for the checkbox. This will allow you to save `null` values, in addition to the built in `1` and `0` values.
Defaults to `true`. If set to `false`, it will allow only the default two values: `1` and `0`.

##### inline
_boolean_, whether the checkboxes are to be styled in an inline-block with other elements placed before or after. Defaults to `true`. 
If set to `false`, checkboxes will be displayed as a block (like in checkbox lists).

##### iconChecked
_string_, the html markup for the glyph / icon to be displayed when the checkbox is checked. Defaults to `<i class="glyphicon glyphicon-ok"></i>`.

##### iconUnchecked
_string_, the html markup for the glyph / icon to be displayed when the checkbox is unchecked. Defaults to a blank character ` `.

##### iconNull
_string_, the html markup for the glyph / icon to be displayed when the checkbox is null. Defaults to `<i class="glyphicon glyphicon-stop"></i>`.

#### size
_string_, size of the checkbox control. Should be one of `xl`, `lg`, `md`, `sm`, or `xs`. Defaults to `md`.

#### enclosedLabel
_boolean_, whether the checkbox input is enclosed inside a label. Defaults to `false`. Setting it to `true` is important if you have enclosed the base input inside a `label` tag.

#### useNative
_boolean_, whether to display the native checkbox control instead of the advanced styled input generated by the plugin. Defaults to `false`. This property will be applied only if your source element is a checkbox input. Setting it to `true` will allow you to use a `threeState` native checkbox. Note that when you have set `useNative` to `true`, you will lose the advanced styling features offerred by `bootstrap-checkbox-x`.

### Plugin Events
The plugin supports these events:

#### change
This event is triggered on the input element, when the checkbox control is modified or changed. 

**Example:**
```js
$('#input-id').on('change', function() {
    console.log('checkbox changed');
});
```

#### reset
This event is triggered when the checkbox control is reset to initial value using the `reset` method or by resetting the form.

**Example:**
```js
$('#input-id').on('reset', function(event) {
    console.log("reset");
});
```

### Plugin Methods
The plugin supports these methods:

#### refresh
Use this method to dynamically refresh the checkbox control options via javascript after the plugin has been initialized. 
The method accepts the plugin options entered as an array.
```js
// Example: Call the method below in checkbox control.change event to disable the checkbox control and
// change the size to 'xl'.
$('#input-id').attr('disabled', 'disabled');
$('#input-id').checkboxX('refresh', {size: 'xl'});
```

#### reset
Reset the checkbox control.
```js
$('#input-id').checkboxX('reset');
```

## License

**bootstrap-checkbox-x** is released under the BSD 3-Clause License. See the bundled `LICENSE.md` for details.