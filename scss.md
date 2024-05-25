# SCSS MIXINS

### SIZE
```
@mixin size($width, $height: $width) {
  width: $width;
  height: $height;
}
```

### Flexbox Toolkit
```
@mixin flex(
  $justifyContent: flex-start,
  $alignItems: center,
  $flexDirection: row
) {
  display: flex;

  flex-direction: $flexDirection;

  justify-content: $justifyContent;

  align-items: $alignItems;
}

@mixin flex-column {
  display: flex;
  flex-direction: column;
}

@mixin flex-center {
  display: flex;
  align-items: center;
  justify-content: center;
}

@mixin flex-center-column {
  @include flex-center;
  flex-direction: column;
}

@mixin flex-center-vert {
  display: flex;
  align-items: center;
}

@mixin flex-center-horiz {
  display: flex;
  justify-content: center;
}
```

### Font Size
```
@mixin font-size($font-size, $line-height: normal, $letter-spacing: normal) {
  font-size: $font-size * 1px;
  // font-size: $font-size * 0.1rem;
  // example using rem values and 62.5% font-size so 1rem = 10px

  @if $line-height==normal {
    line-height: normal;
  } @else {
    line-height: $line-height / $font-size;
  }

  @if $letter-spacing==normal {
    letter-spacing: normal;
  } @else {
    letter-spacing: #{$letter-spacing / $font-size}em;
  }
}
```

### Media queries
```
$tablet: 768;
$large: 1024;
$desktop: 1280;

@mixin tablet {
  @media only screen and (min-width: $tablet * 1px) {
    @content;
  }
}

@mixin large {
  @media only screen and (min-width: $large * 1px) {
    @content;
  }
}

@mixin desktop {
  @media only screen and (min-width: $desktop * 1px) {
    @content;
  }
}

/* ===== Usage ===== */
h1 {
  font-size: 10px;

  @include tablet {
    font-size: 12px;
  }

  @include desktop {
    font-size: 20px;
  }
}
```
### Content children
```
@mixin children() {
  & > * {
    @content;
  }
}

@mixin first() {
  & > *:first-child {
    @content;
  }
}

@mixin last() {
  & > *:last-child {
    @content;
  }
}
```

### Visibility
```
@mixin fade($type) {
  @if $type== "hide" {
    visibility: hidden;
    opacity: 0;
    transition: visibility 1s, opacity 1s;
  } @else if $type== "show" {
    visibility: visible;
    opacity: 1;
    transition: visibility 1s, opacity 1s;
  }
}
```

### Center Block
```
@mixin center-block {
  display: block;
  margin-left: auto;
  margin-right: auto;
}
```

### Text overflow
```
@mixin text-truncate {
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}
```

### Placeholders
```
@mixin input-placeholder {
    &.placeholder { @content; }
    &:-moz-placeholder { @content; }
    &::-moz-placeholder { @content; }
    &:-ms-input-placeholder { @content; }
    &::-webkit-input-placeholder { @content; }
}
```