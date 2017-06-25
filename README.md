# Snippets

## HTML

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

## React

### React Component

```jsx
import React from "react";
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
