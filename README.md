# toggle
Anchor based toggle system using jQuery and Bulma (optional).

## What does it do

Simply, it works exactly how a radio button would work. Being able to select between `<a>` tags provides some additional styling options and flexibility that perhaps a radio button would not. There are other ways to accomplish this task however I wanted/needed a solution that didn't end up with a bloat of CSS to hide and distort elements.

## Prerequisites

jQuery (most versions will work since we don't do anything that would be regarded as elaborate)

Bulma (bulma.io) feel free to use any other CSS library/framework. This should be easy to swap out since we a pretty much just colouring buttons. The style section in the example has only one entry that will need to be adjusted.

Each anchor (button) requires the class `toggle` which is how our script identifies with the toggle buttons in our document.
Each anchor is required to have `data-grp="field"` and `data-val="value"` which is used to group the toggle buttons together with their respective values.

A hidden input form field is required for storing the selection and should be prepopulate with a value from the toggle group. The input should have at least an ID attribute which shares the data-grp name.

i.e.
```
<a class="button is-light toggle" data-grp="example" data-val="value 1"></a>
<a class="button is-light toggle" data-grp="example" data-val="value 2"></a>
<a class="button is-light toggle" data-grp="example" data-val="value 3"></a>

<input type="hidden" id="example" name="example" value="value 1">
```

## How it works

Each toggle group button `<a class="button is-light toggle" data-grp="my_field_name" data-val="some value"></a>` is added and the script will work through the DOM to find them (notice the class `toggle` which is important here), for each one found we attach a on click listener.

Upon this initial run we also check for our current value in our hidden input value and then add a class to the button that shares this value in its data-val attribute.

During the initial setup it is worth noting that an additional data attribute is appended; the `data-selected="false"` attribute will become true when selected.

One a click event is fired, jQuery will loop back through that group and set them all back to their original states before then updating the most recent element with a selected state.

Please note that the class selected is added to the toggle button that is currently selected.



