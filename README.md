# Snippets

## HTML

### Basic HTML Template

```html
<!DOCTYPE html>
<html>
<head>
  <title>Title</title>
  <link href="style.css" rel="stylesheet" type="text/css">
  <meta name="viewport" content="width=device-width, initial-scale=1">
</head>

<body>

</body>
</html>
```

### Sticky Footer

```html
<div id="wrap">
  Content
</div>

<footer id="footer-main">
  Footer.
</footer>
```
```scss
$height-footer: 100px;
html, body {
  height: 100%;
}
.#wrap {
  min-height: 100%;
  /* equal to footer height */
  margin-bottom: -1 * $height-footer; 
}
#wrap:after {
  content: "";
  display: block;
}
#footer-main, #wrap:after {
  height: $height-footer; 
}
#footer-main {
  background: orange;
}
```

## SCSS

### Retina background mixin
````scss
@mixin background-image-retina($file, $type) {
  background-image: url($file + '.' + $type);
  @media (-webkit-min-device-pixel-ratio: 2), (min-resolution: 192dpi) {
    background-image: url($file + '@2x.' + $type);
  }
}
````

## Javascript

### jQuery (Google)
```html
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>
```

### Email RegEx
```javascript
/^(([^<>()\[\]\\.,;:\s@"]+(\.[^<>()\[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
```


## React

### Basic React Component

```jsx
import React from "react";
import PropTypes from "prop-types";
import { connect } from "react-redux";

class Comp extends React.Component {
  constructor(props) {
    super(props);

    this.state = {}
  }

  render() {

    // ...

    return(
      <div>Content</div>
    );
  }
};

Comp.propTypes = {
  name: PropTypes.string
};

const mapStateToProps = function(store) {
  return {
    prop: store.location,
  };
}

const mapDispatchToProps = function(dispatch, ownProps) {
  return {
    action: function() {
      // Do something
    },
  }
}

export default connect(mapStateToProps, mapDispatchToProps)(Comp);
```

## Misc

### .bash_profile
```
alias showFiles='defaults write com.apple.finder AppleShowAllFiles YES; killall Finder /System/Library/CoreServices/Finder.app'
alias hideFiles='defaults write com.apple.finder AppleShowAllFiles NO; killall Finder /System/Library/CoreServices/Finder.app'
alias dockerKillAll='docker stop $(docker ps -a -q); docker rm $(docker ps -a -q)'
```
