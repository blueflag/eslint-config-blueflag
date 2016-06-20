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

### Use self-closing tags for elements without children
```jsx
// Good
return <span />;

// Bad
return <span></span>;
```



