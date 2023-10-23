# SASS
## 1. SASS installation
1. Open a new terminal and install SASS using the command `npm install -g sass`
2. Run `sass --version`

Now you can compile your Sass code to CSS using the sass command `sass ./scss/input.scss ./css/output.css`

You can also use the --watch flag `sass --watch ./scss/input.scss ./css/output.css`

## 2. Link Stylesheet
1. Link your HTML with your output.css file

## SASS Variables
To define a variable in SASS use the dollar sign `$`
1. Define these variables in your sass file 
```
primary color: #3498db;
secondary color: #e74c3c;
accent color: #ffc107;
featured color: #e74c3c;
standar border: 4px solid black;
```
2. Create an 'h1' element and use your SASS variables
```
h1 {

}
```

## Nesting
1. Create a navigation menu
```
<nav>
    <ul>
        <li><a href="#">Home</a></li>
        <li><a href="#">Contact</a></li>
        <li><a href="#">About</a></li>
        <li><a href="#">Services</a></li>
    </ul>
</nav>
```
2. Replicate these styles in SCSS

```
nav {
  background-color: #6c757d;
  padding: 10px;
  margin: 10px 0;
}
nav ul {
  list-style-type: none;
  margin: 0;
  padding: 0;
}
nav ul li {
  display: inline-block;
  margin-right: 10px;
}
nav ul li a {
  color: #ffffff;
  text-decoration: none;
}
```

2. To apply nested styles to pseudo-classes/elements use the `&` symbol to represents the current selector. 
Task: Use the `&` symbol to define the hover state of the anchor tag.

```
&:hover {
    text-decoration: underline;
}
```

## Practice - Nesting
1. Create a button element with a 'btn-secondary' class and target it in your SCSS
2. Use the secondary color SASS variable as the background color
3. When 'hover' change the opacity of the background color `background-color: rgba($secondary-color, 0.5);` 
4. When 'active' change any other style/color 

## Mixing
Mixin lets you make groups of CSS declarations that you want to reuse throughout your site.
To create a mixin you use the `@mixin` directive and give it a name. After you create your mixin, you can then use it as a CSS declaration starting with `@include` followed by the name of the mixin.
1. Create a mixin called 'theme'. Receive a parameter called $theme and set the default value as 'darkgray'. Use these styles:
```
{
    background: $theme;
    box-shadow: 0 0 1px rgba($theme, .25);
    color: #fff;
}
```

2. Generate these styles in SCSS using the mixin 'theme'
```
.info {
    background: darkgray;
    box-shadow: 0 0 10px darkgray;
    color: #fff;
}

.alert {
    background: darkred;
    box-shadow: 0 0 10px darkred;
    color: #fff;
}

.success {
    background: darkgreen;
    box-shadow: 0 0 10px darkgreen;
    color: #fff;
}
```


## Mixin practice
Use a @mixin to define different styles for buttons
1. Create a @mixin 'btn-styles' with the following styles. Use `$bg-color` and `$text-color` as parameters
```
padding: 10px 15px;
border: none;
border-radius: 4px;
cursor: pointer;
font-size: 16px;
background-color: $bg-color;
color: $text-color;
transition: background-color 0.3s;
```
2. Include the mixin within the class 'btn-primary' and 'btn-secondary'


## Extend
1. Use the class 'btn' with the following styles to create a base style for the buttons.
```
padding: 10px 15px;
border: none;
border-radius: 4px;
cursor: pointer;
font-size: 16px;
transition: background-color 0.3s;
```
2. Extend the button styles within .btn-primary
```
.btn-primary {
    // here extend base stles
    background-color: $primary-color;
}
```


## Extend practice
1. Define a html blog
```
<article class="post">
    <h2 class="post-title">Post Title 1</h2>
    <p class="post-content">Lorem ipsum...</p>
    <a href="#" class="read-more">Read More</a>
</article>
<article class="featured-post">
    <h2 class="post-title">Post Title 2</h2>
    <p class="post-content">Lorem ipsum...</p>
    <a href="#" class="read-more">Read More</a>
</article>
```

2. Define the base styles
```
.post {
    padding: 20px;
    margin-bottom: 20px;
    background-color: #fff;
    border: 1px solid #ddd;
}
```

3. Define .feature-blog extending the base styles, and add the style `border-color: $featured-color;`

```
.featured-post {
   
}
```

## SASS interpolation
1. Use interpolation to get this css selector. Create at least the `$button-prefix` variable
```
.btn-lg {
  padding: 15px 30px;
}
```

## SASS Control flow directives example
1. Define a SASS map '$button-colors' with the following colors
```
primary: #007bff,
secondary: #6c757d,
success: #28a745,
danger: #dc3545
```
2. Use the @each directive and the interpolation to generate the styles for all the button colors.
```
.btn-primary {
    background-color: #007bff;
    color: white;
}

.btn-secondary {
    background-color: #6c757d;
    color: white;
}

.btn-success {
    background-color: #28a745;
    color: white;
}

.btn-danger {
    background-color: #dc3545;
    color: white;
}

```



# Bootstrap customization

1. Install Bootstrap `npm install bootstrap`
2. Create Your Custom Sass File
```
// Custom.scss
// 1. Override Bootstrap's default variables

//2. Import Bootstrap's source Sass files
@import "../bootstrap/scss/bootstrap";

//3. Customize Components below
```

3. Compile Your Sass
```
sass --watch ./node_modules/scss/custom.scss ./css/custom.css
```

4. Include the Compiled CSS in Your Project
```
<!doctype html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>Custom Bootstrap</title>
    <link href="./css/custom.css" rel="stylesheet">
  </head>
  <body>
    <h1>Hello, world!</h1>
  </body>
</html>
```

5. Customize the primary color and button's padding variables.

```
// Override Bootstrap's default variables
$primary: #ff6600;             // Changing the primary color to a shade of orange

$btn-padding-y: 0.75rem;       // Adjusting vertical padding for buttons
$btn-padding-x: 1.5rem;        // Adjusting horizontal padding for buttons
$btn-border-radius: 0;         // Making the button corners square
$btn-font-weight: bold;        // Making the button text bold
```

6. Customize the .btn component
```
// Custom styles for the .btn-primary component
.btn-primary {
  &:hover {
    background-color: darken($primary, 10%); // Darken the primary color on hover
  }
}
```
