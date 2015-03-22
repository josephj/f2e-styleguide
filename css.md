CSS Coding Style
-------------------

## Line Length

Avoid lines longer than 80 characters.

## Spacing

* Use soft-tabs with a 4 spaces indent. Spaces are the only way to guarantee code renders the same in any person's environment.
* Put spaces after `:` in property declarations.
* Put spaces before `{` in rule declarations.
* Put line breaks between rulesets.
* When grouping selectors, keep individual selectors to a single line.
* Place closing braces of declaration blocks on a new line.
* Each declaration should appear on its own line for more accurate error reporting.

```css
#selector1,
#selector2 {
    name1: value1;
    name2: value2;
    name3: value3;
}
```

## Formatting

* Use hex color codes `#000` unless using `rgba()`.
* Use `//` for comment blocks (instead of `/* */`).
* Avoid specifying units for zero values, e.g., `margin: 0;` instead of `margin: 0px;`
* Strive to limit use of shorthand declarations to instances where you must explicitly set all the available values.

    ```css
    // avoid! will not set the color of background to red
    background-color: red;
    background: url(images/bg.gif) no-repeat top right;
    ```

## Class Naming

Use lowercase dashed-words instead of camelCase.

Selectors should be **descriptive of function** rather than form. For instance, "red" and "bold" should not be used as class names
because they indicate the form of the text rather than its function. Selectors such as "button" or "hd" (short for "head") are preferred
because they indicate use.

Selector names should use *dash case*, meaning all words are lowercase with dashes as separators (**word1-word2-word3**). Examples:

* submit-button
* mod-hd
* user-icon

## Pixels vs. ems

Use `px` for `font-size`, because it offers absolute control over text.
Additionally, unit-less `line-height` is preferred because it does not inherit a percentage value of its parent element,
but instead is based on a multiplier of the font-size.

## Nesting in SCSS

As a rule of thumb, avoid unnecessary nesting in SCSS. At most, aim for 3 levels.
If you cannot help it, step back and rethink your overall strategy (either the specificity needed, or the layout of the nesting).

```css
// avoid
.type_module-name div ul li .exampleclass {
    ...
}
// better
.type_module-name .exampleclass {
    ...
}
```

## Declaration Order

The attribute names should be in alphabetical order. You can avoid duplicate attributes by doing this.
Though someone claims the ordering can cause some problems, I havn't experienced yet.

```css
.selector {
    color: #333;
    display: table;
    font-family: Calibri;
    font-size: 123.1%;
    margin: 0 10px 10px 0;
    padding: 5px;
    position: relative;
    width: 500px;
    _float: left;
}
```

## Use *-bottom and *-right

It's recommended to use *-bottom and *-right attributes rather than *-top and *-left attributes.
Because the page flow is from top-left to right-bottom, use *-bottom or *-right attributes often reduce both the
complexity and layout issues.

## SASS Format

* Always place `@extend` statements on the first lines of a declaration block.
* Where possible, group `@include` statements at the top of a declaration block, after any `@extend` statements.
* Consider prefixing custom functions with `x-` or another namespace. This helps to avoid any potential to
  confuse your function with a native CSS function, or to clash with functions from libraries.

```css
.selector-1 {
    @extend .other-rule;
    @include clearfix();
    @include box-sizing(border-box);
    width: x-grid-unit(1);
    // other declarations
}

```

## References

* [Github CSS Styleguide](https://github.com/styleguide/css)
* [Nicolas Gallagher's Idiomatic CSS](https://github.com/necolas/idiomatic-css)

