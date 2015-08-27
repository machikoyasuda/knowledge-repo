# Props and propTypes

- Props are like element attributes
- Validate propTypes to help others consume our components

```
  propTypes: {
    email: React.PropTypes.string.isRequired,
  }
```
http://facebook.github.io/react/docs/reusable-components.html

# Props vs. State

- Do I need to change this? No -> Prop
- Does anyone else unrelated to me need to change this? Y -> Store
- Do my changes need to persist if I'm remounted? No -> State

# Reduce takes an array and reduces it into a single value