# Capital G - Grid Framework

## Sass Config</h2>

Every project will require the following variable map to be defined:</p>

```sass
$g-config: (
  maxWidth: 1020px,
  tabletWidth: 720px,
  columnPadding: 15px,
  gutter: 20px
);
```

## Flexibility

There are two ways you can implement a grid in your layout:

* Via HTML classes
* Via SASS mixins

Neither is more correct that the other. It all depends on your use case. The CSS route is perhaps cleaner, but may be more work if you have to name addtional components to style.

## HTML Method

Column widths and break rules are defined as classes in the HTML.

```html
<div class="Layout G-container">
  <div class="G-row">
    <div class="G-col-4 G-col-mobile--12">
      <!-- content goes here -->
    </div>
    <div class="G-col-8 G-col-mobile--12">
      <!-- content goes here -->
    </div>
  </div>
</div>
```

## CSS Method

Elements are assigned classes in the HTML but the column widths and break rules are defined in the SASS/CSS using mixins.

```html
<div class="Layout">
  <div class="Layout-inner">
    <div class="Sidebar">
      <!-- content goes here -->
    </div>

    <div class="Content">
      <!-- content goes here -->
    </div>
  </div>
</div>
```

```sass
.Layout {
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
}
```

## Reference

### SASS Mixins

#### Container
```sass
@include g($fluid: false, $flush: false, $gutter: true);
```

#### Row
```sass
@include g-row();
```

#### Column
```sass
@include g-column($columns);
```

#### Mobile media query helper
```sass
@include g-when-mobile() {
  // Styles here
}
```

#### Desktop media query helper
```sass
@include g-when-tablet() {
  // Styles here
}
```


#### Desktop media query helper
```sass
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
