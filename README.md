# Getting started with Sass

Install: (http://sass-lang.com/install)

## Once Sass is installed, from the command line, you can run 
`sass input.scss output.css`

(also check for sublime compiler)

You can store things like colors, font stacks, or any CSS value you think you'll want to reuse. Sass uses the $ symbol to make something a variable. 

### SCSS
```
$font-stack:    Helvetica, sans-serif;
$primary-color: #333;

body {
  font: 100% $font-stack;
  color: $primary-color;
}
```

### SASS
```
$font-stack:    Helvetica, sans-serif
$primary-color: #333

body
  font: 100% $font-stack
  color: $primary-color

```

### CSS Results
```
body {
  font: 100% Helvetica, sans-serif;
  color: #333;
}
```

The difference - one uses semi-colons and brackets. The other uses indentation.

## SASS allows nested and visual hierarchy like HTML.
Typical styles for navigation
```
nav {
    ul {
        margin: 0;
        padding: 0;
        list-style: none;
    }

    li { display: inline-block; }

    a {
        display: block;
        padding: 6px 12px;
        text-decoration: none;
    }
}
```

### CSS Results
```
nav ul {
  margin: 0;
  padding: 0;
  list-style: none;
}

nav li {
  display: inline-block;
}

nav a {
  display: block;
  padding: 6px 12px;
  text-decoration: none;
}
```

## Import
Allows CSS to be spilt into smaller chunks. First create partials - identified with underscore: `_partial.scss`

```
// _reset.scss

html,
body,
ul,
ol {
    margin: 0;
    padding: 0;
}
```

```
// base.scss

@import 'reset'; //no need to include the extension

body {
  font: 100% Helvetica, sans-serif;
  background-color: #efefef;
}
```

### CSS Result
```
html, body, ul, ol {
  margin: 0;
  padding: 0;
}

body {
  font: 100% Helvetica, sans-serif;
  background-color: #efefef;
}
```

## Mixins
Especially useful with CSS3 vendor prefixes
```
@mixin border-radius($radius) {
  -webkit-border-radius: $radius;
     -moz-border-radius: $radius;
      -ms-border-radius: $radius;
          border-radius: $radius;
}

.box { @include border-radius(10px); }
```

### CSS Results
```
.box {
  -webkit-border-radius: 10px;
  -moz-border-radius: 10px;
  -ms-border-radius: 10px;
  border-radius: 10px;
}
```

## Extend/Inheritance
Share a set of CSS properties from one selector to another with `@extend`.
```
.message {
  border: 1px solid #ccc;
  padding: 10px;
  color: #333;
}

.success {
  @extend .message;
  border-color: green;
}

.error {
  @extend .message;
  border-color: red;
}

.warning {
  @extend .message;
  border-color: yellow;
}
```

Use the properties in `.message` and apply them to `.success`, `.error`, and `.warning`

### CSS Results
```
.message, .success, .error, .warning {
  border: 1px solid #cccccc;
  padding: 10px;
  color: #333;
}

.success {
  border-color: green;
}

.error {
  border-color: red;
}

.warning {
  border-color: yellow;
}
```

## Operators
Standard math operators `+`, `-`, `*`, `\`, `%`

Calculate widths for `aside` & `article`
```
.container { width: 100%; }


article[role="main"] {
  float: left;
  width: 600px / 960px * 100%;
}

aside[role="complementary"] {
  float: right;
  width: 300px / 960px * 100%;
}
```

### CSS Results
```
.container {
  width: 100%;
}

article[role="main"] {
  float: left;
  width: 62.5%;
}

aside[role="complementary"] {
  float: right;
  width: 31.25%;
}
```
### SASS With Grunt Notes
https://www.saltycrane.com/blog/2015/02/customizing-bootstrap-sass-version-using-grunt-and-bower/

