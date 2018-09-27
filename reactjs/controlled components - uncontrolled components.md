# Controlled components - Uncontrolled components

## Controlled components
- Form data is handled by a `React component` (recommend)
- Example:
```jsx
render() {
  return (
    <form onSubmit={this.handleSubmit}>
      <label>
        Name:
        <input
          type="text"
          value={this.state.value}
          onChange={this.handleChange}
         />          
      </label>
      <input type="submit" value="Submit" />
    </form>
  )
}
```

## Uncontrolled components
- Form data is handled by the `DOM` itself
- Can use a `ref` to get form values from the `DOM`
- Default Values:
  - Support `defaultChecked`: `<input type="checkbox">` and `<input type="radio">`
  - Support `defaultValue`: `<input type="text">`, `<textarea>` and `<select>`
- Example:  
```jsx
render() {
  return (
    <form onSubmit={this.handleSubmit}>
      <label>
        Name:
        <input
          type="text"        
          defaultValue="Bob"
          ref={this.input}
         />
      </label>
      <input type="submit" value="Submit" />
    </form>
  )
}
```
