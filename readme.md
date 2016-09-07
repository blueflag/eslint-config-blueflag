# Blue Flag linting configurations

# Installation

```
npm install eslint-config-blueflag
```

```js
// .eslintrc
{
    "extends": [
        "eslint-config-blueflag",
        "eslint-config-blueflag/flow.js" // With flow types
    ]
}
```

## Global linters (Sublime Linter)

If your linter can't handle using the current directory to find binaries you will need to install 
the plugins globally. **Make sure you install eslint 2.4.0 though. The babel parser is having issues with 
later versions.**

```sh
# Defaults
# eslint@2.4.0
# eslint-plugin-react
# 
# Flow Types
# eslint-plugin-flow-vars
# eslint-plugin-flowtype

# one liner
npm install -g eslint@2.4.0 eslint-plugin-flow-vars eslint-plugin-flowtype eslint-plugin-react

```


# Style Guide

## JSX

### Return JSX elements directly

```jsx
// Good
return <ul className="List">
    <li>list items</li>
    <li>list items</li>
</ul>;

// Bad
return (
    <ul className="List">
        <li>list items</li>
        <li>list items</li>
    </ul>
);
```

####Find and replace
Find: `return(\s+?)\((\s+?)<`

Automatic find and replaces are hard for this. You can replace `return(\s+?)\((\s+?)<` with `return <`, find the closing `);` and replace it with `;` and de-indent all lines between.

### Use self-closing tags for elements without children
```jsx
// Good
return <span />;

// Bad
return <span></span>;
```

### Multiple line components should have each prop on a new line, indented once

```jsx
// Good
return <ExampleComponent
    title="Example"
    author="Robert">
    <p>Child elements</p>
</ExampleComponent>;

return <ExampleComponent
    title="Example"
    author="Robert" />

// Bad
return <ExampleComponent title="Example"
    description="Hello"
>
    <p>Child elements</p>
</ExampleComponent>;

return <ExampleComponent
        title="Example"
        description="Hello">
    <p>Child elements</p>
</ExampleComponent>;
```

#### Find and replace
Find: `\s+?$\s+?(/?>;?)(\s*?)`
Replace: `$1\n` and then fix up indentation

## JS

### Chains of functions should be indented by 4 spaces

```jsx
// Good
return fromJS(list)
    .map(ii => ii.get('id'))
    .sort()
    .toJS();

// Bad
return fromJS(list).map(ii => ii.get('id')).sort().toJS();

return fromJS(list)
       .map(ii => ii.get('id'))
       .sort()
       .toJS();


```

### Named imports should have spaces between braces and words

```jsx
// Good
import React, { Component, Children } from 'react';

// Bad
import React, {Component, Children} from 'react';
```

## Naming

### Filenames should use TitleCase

```jsx
// Good
Button.jsx
CreateRoutes.js

// Bad
button.jsx
createRoutes.js
```

### Folders should always be camelCase

```jsx
// Good
src/users/
src/learningPlan/

// Bad
src/Users/
src/learning_plan/
```

### Route paths should be kebab-case

```jsx
// Good
http://example.com/free-hugs

// Bad
http://example.com/freeHugs
http://example.com/free_hugs
```
