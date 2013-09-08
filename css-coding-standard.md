# CSS
We use Sass or Less when writing CSS depending on the environment we're working in

# Naming conventions
- Elements that occur only once may use IDs, f.x. #container, #footer, #nav but use classes if in any doubt
- Class names, attributes and values should be written in lowercase, with words seperated by dashes, f.x.: `.main-image`
- Don't use too generic names for classes:

  **Bad:** `.facebook`
  **Recommended:** `.share-facebook`

  **Bad:** .`date`
  **Recommended:** `.post-date`


# CSS code style
- Group CSS attributes by their nature:
- Put a blank line between rulesets

```scss
.selector {
  // Positioning
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  z-index: 1001;

  // Box model
  display: inline;
  box-sizing: border-box;
  width: 100px;
  height: 100px;
  overflow: hidden;
  margin: 1em;
  border: 1px solid #eee;
  padding: 1em;

  // Background and text styles
  background: #000;
  text-align: center;
  color: #fff;
  font-family: sans-serif;
  font-size: 16px;

  // Pseudo elements
  &:before {
    content: "\25BB";
    font-family: "SSStandard";
  }

  // Animations and transitions
  @include transition(  
    top 0.25s ease-in-out,
    opacity 0.15s ease-in
  );

  @include spin-animation(1.5s);

  // States
  &.selected, &:hover {
    background: #fff;
    color: #000;
  }

  // Use one-line format for single attributes
  &.disabled { opacity: 0.8;   }

  // Nested styles for child elements
  .nav {
    position: relative;

    ul.nav-left > li {
      display: inline;
      background: blue;

      a {
        display: block;
        font-weight: bold;
      }
    }
    
    &.affix {
      position: fixed;
    }
  }
}
```


# File Organization

- Split your code logically into many files and group in directories. When in doubt: Split.
- When splitting, think of reusability. Files should have relatively generic names and their styles should be generic.

```
assets/css
├── main.scss
├── variables.scss
├── components
│   ├── navigation.scss
│   ├── panels.scss
│   └── type.scss
├── mixins
│   ├── responsive.scss
│   ├── animation.scss
├── vendor
│   ├── jquery.bloated.css
│   └── normalize.scss
```


# Specificity and Reusability

- Think twice before adding location of elements to class names. You might want to use the same styles in more than one page:

    **Bad:** `.frontpage-top-banner`

    **Recommended:** `.top-banner`

- Go from generic to specific:

    **Bad:**

    ```scss
    $body-font: "Arial";
    $heading-font: "Arial Black";
    $red-color: red;
    ```

    **Recommended:**

    ```scss
    $font-body: "Arial";
    $font-heading: "Arial Black";
    $color-red: red;
    ```
