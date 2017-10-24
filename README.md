# Snippets

## HTML

### Basic HTML Template

```html
<!DOCTYPE html>
<html>
<head>
  <title>Feedr Home Static</title>

  <meta name="viewport" content="width=device-width, initial-scale=1">
  <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/4.0.0-beta/css/bootstrap.min.css" integrity="sha384-/Y6pD6FV/Vv2HJnA6t+vslU6fwYXjCFtcEpHbNJ0lyAFsXTsjBbfaDjzALeQsN6M" crossorigin="anonymous">
  <link href="css/style.css" rel="stylesheet" type="text/css">
</head>

<body>
<div class="skiptocontent"><a href="#maincontent">skip to main content</a></div>
<div class="page-wrap">

<header class='header-main'>

  <div class="container">
    <div class="row">
      <div class="col-12">

        <!-- content -->
        
      </div>
    </div>
  </div>

</header>

<div id="maincontent" class='body'>

  <div class="container">
    <div class="row">
      <div class="col-12">

        <!-- content -->

      </div>
    </div>
  </div>

</div> <!-- .main-content -->

</div> <!-- .page-wrap -->
<footer class='footer-man'>
  <div class="container">
    <div class="row">
      <div class="col-12">
        
        <!-- content -->

      </div>
    </div>
  </div>
</footer>

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
#wrap {
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

### Mobile Nav

```scss
#mobile-nav-overlay {
  display: none;
  position: fixed;
  top: $height-header;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(255, 255, 255, 0.9);
  z-index: 1000;
  padding: 25px;

  &.active {
    display: block;
  }

  ul {
    width: 100%;
    height: 100%;
    overflow: scroll;
    list-style: none;
    padding: 0;
    margin: 0;

    &.active {
      a {
        opacity: 1;
        transform: translateY(0);
      }
    }

    li {
      a {
        display: block;
        font-size: 24pt;
        color: #000;
        text-align: center;
        padding: 0.25em 0;
        transition: all .5s;
        opacity: 0;
        transform: translateY(20px);
      }
    }
  }
}
```

```scss
#mobile-menu-toggle {
  display: block;
  width: 44px;
  height: 44px;
  position: relative;

  .bar {
    background-color: #000;
    display: block;
    width: 20px;
    height: 2px;
    border-radius: 100px;
    position: absolute;
    top: 22px;
    right: 12px;
    transition: all 0.5s;
    &:first-child {
      transform: translateY(-6px);
    }
  }

  &.x .bar { transform: rotate(45deg); }
  &.x .bar:first-child { transform: rotate(-45deg) }
}
```

```js
$('#mobile-menu-toggle').click(function() {
    $(this).toggleClass('x');
    $('#mobile-nav-overlay').fadeToggle({
      done: function() {
        $('#mobile-nav-overlay ul').toggleClass('active');
      }
    });
  });
```
  
```html
<div id="mobile-nav-overlay">
  <ul>
    <li><a href="#home">About</a></li>
    <li><a href="#home">Why Join</a></li>
    <li><a href="#home">Research</a></li>
    <li><a href="#home">News</a></li>
    <li><a href="#home">Events</a></li>
    <li><a href="#home">Online Library</a></li>
  </ul>
</div>
```
  
```html
<a href="javascript:void(0)" id="mobile-menu-toggle">
  <s class="bar"></s>
  <s class="bar"></s>
</a>
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
import React from 'react';
import PropTypes from 'prop-types';
import { connect } from 'react-redux';

const propTypes = {
  prop: PropTypes.string
}

const defaultProps = {
  prop: "value"
}

class Comp extends React.Component {
  constructor(props) {
    super(props);
  }

  render() {
    return null;
  }
}

Comp.propTypes = propTypes;
Comp.defaultProps = defaultProps;

const mapStateToProps = function mapStateToProps(store) {
  return {
    prop: store.location,
  };
}

const mapDispatchToProps = function mapDispatchToProps(dispatch, ownProps) {
  return {
    action: () => {
      // Do something
    },
  }
}

export default connect(mapStateToProps, mapDispatchToProps)(Comp);
```

## Worpdress

### Page Title
```php
function theme_head_title() {
  if (function_exists('is_tag') && is_tag()) { 
	  echo 'Tag Archive for &quot;'.$tag.'&quot; - '; 
  } elseif (is_archive()) { 
  	wp_title(''); echo ' Archive - '; 
  } elseif (is_search()) { 
  	echo 'Search for &quot;'.wp_specialchars($s).'&quot; - '; 
  } elseif (!(is_404()) && (is_single()) || (is_page())) { 
  	wp_title(''); echo ' - '; 
  } elseif (is_404()) {
  	echo 'Not Found - '; 
  }
  bloginfo('name'); 
}
```

## Misc

### .bash_profile
```
alias showFiles='defaults write com.apple.finder AppleShowAllFiles YES; killall Finder /System/Library/CoreServices/Finder.app'
alias hideFiles='defaults write com.apple.finder AppleShowAllFiles NO; killall Finder /System/Library/CoreServices/Finder.app'
alias dockerKillAll='docker stop $(docker ps -a -q); docker rm $(docker ps -a -q)'
```
