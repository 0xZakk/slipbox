- **Type:** #[[__ 📦 Projects]] #[[🌱 Seed]] | [[JavaScript]]
- **Summary:** Article that walks through examples of how to use the `every` and `some` array methods in JavaScript as well as how to implement it it
- **Related Notes and Sources:**
    - https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/every
    - https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/some
- **Notes:**
- **Outline**
    - **Introduction**
        - **Description:** __What the method is used for and what it does__
    - **How it works**
        - **Description:** __3-4 samples of the method working, starting from very simple to a little complex__
        - `every()`
            - Revisit the `concat` method = #[[📦 Article: Array Methods: concat]]
            - We want to make sure every item passed in is an array
            - ```javascript
function concat(...args) {
  let areArrays = args.every(arg => Array.isArray(arg))
  if (!areArrays) return
  
  // Rest of code
}```
    - **Implementing our own**
        - **Description:** __Step by step, implement a version of this method. Start with the tests, then implement the code.__
