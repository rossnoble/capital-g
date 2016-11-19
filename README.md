# Capital G - Grid Framework

## Sass Config</h2>

Every project will require the following variables to be defined:</p>

<pre><code>$g-maxWidth: 1120px;
$g-maxWidth-tablet: 720px;
$g-containerGutter: 15px;
$g-columnGutter: 15px;
$g-break-desktop: $g-maxWidth;
$g-break-mobile: ($g-maxWidth-tablet + 19px);
$g-break-tablet: ($g-maxWidth-tablet + 20px);</code></pre>

## Flexibility

There are two ways you can implement a grid in your layout:

* Via HTML classes
* Via SASS mixins

Neither is more correct that the other. It all depends on your use case. The CSS route is perhaps cleaner, but may be more work if you have to name addtional components to style.

## HTML Method

Column widths and break rules are defined as classes in the HTML.

<pre><code>&lt;div class="Layout G-container"&gt;
  &lt;div class="G-row"&gt;
    &lt;div class="G-col-4 G-col-mobile--12"&gt;
      &lt;!-- content goes here --&gt;
    &lt;/div&gt;
    &lt;div class="G-col-8 G-col-mobile--12"&gt;
      &lt;!-- content goes here --&gt;
    &lt;/div&gt;
  &lt;/div&gt;
&lt;/div&gt;</code></pre>

## CSS Method

Elements are assigned classes in the HTML but the column widths and break rules are defined in the SASS/CSS using mixins.

<pre><code>&lt;div class="Layout"&gt;
  &lt;div class="Layout-inner"&gt;
    &lt;div class="Sidebar"&gt;
      &lt;!-- content goes here --&gt;
    &lt;/div&gt;

    &lt;div class="Content"&gt;
      &lt;!-- content goes here --&gt;
    &lt;/div&gt;
  &lt;/div&gt;
&lt;/div&gt;</code></pre>

<pre><code>.Layout {
  @include g();

  .Layout-inner {
    @include g-row();
  }

  .Sidebar {
    @include g-col(4);
    @include g-when-mobile {
      @include g-col(12);
    }
  }

  .Content {
    @include g-col(8);
    @include g-when-mobile {
      @include g-col(12);
    }
  }
}</code></pre>

## Reference

### SASS Mixins

#### Container
```
@include g($fluid: false, $flush: false, $gutter: true);
```

#### Row
```
@include g-row();
```

#### Column
```
@include g-column($columns);
```

#### Mobile media query helper
```
@include g-when-mobile() {
  // Styles here
}
```

#### Desktop media query helper
```
@include g-when-tablet() {
  // Styles here
}
```


#### Desktop media query helper
```
@include g-when-desktop() {
  // Styles here
}
```



### CSS Classes

#### Container

```html
<div class="G-container G-container--fluid">
  <!-- content goes here -->
</div>
```

#### Fluid Container (no max width)

```html
<div class="G-container G-container--fluid">
  <!-- content goes here -->
</div>
```

#### Flush Container (no container gutter)

```html
<div class="G-container G-container--flush">
  <!-- content goes here -->
</div>
```

#### Guttler Container (no column gutters)

```html
<div class="G-container G-container--gutterless">
  <!-- content goes here -->
</div>
```