- **Type:** #[[__ 🟦  Reference Note]] #[[📥 Inbox]] #[[📝 To Process]] | [[React]] [[React Hooks API]]
- **Source:**  instapaper
- **Author:**
- **Summary:**
- ### Highlights first synced by [[Readwise]] [[November 24th, 2020]]
    - The Hooks API has brought with it a whole new way of writing and thinking about React apps. 
    - One of my favorite Hooks so far is useReducer, which allows you to handle complex state updates, and that’s what we’ll be looking at in this article. 
    - What is useReducer? 
    - It’s one of the new custom Hooks that now ship with React since v16.8. It allows you to update parts of your component’s state when certain actions are dispatched, and it is very similar to how Redux works. 
    - It takes in a reducer function and an initial state as arguments and then provides you with a state variable and a dispatch function to enable you to update the state. If you’re familiar with how Redux updates the store through reducers and actions, then you already know how useReducer works. 
    - How does useReducer work? 
    - A useReducer requires two things to work: an initial state and a reducer function. 
    - Consider the following snippet of code:


const initialState = { count: 0 }


function reducer(state, action) {
  switch(action.type) {
    case 'INCREMENT':
      return { count: state.count + 1 }
    case 'DECREMENT':
      return { count: state.count - 1 }
    case 'REPLACE':
      return { count: action.newCount }
    case 'RESET':
      return { count: 0 }
    default:
      return state
  }
}


const [state, dispatch] = useReducer(reducer, initialState); 
    - In the code snippet above, we have defined an initial state for our component — a reducer function that updates that state depending on the action dispatched — and we initialized the state for our component on line 21. 
    - Dispatching an action 
    - You’ll notice that useReducer returns two values in an array. The first one is the state object, and the second one is a function called dispatch. This is what we use to dispatch an action. 
    - For instance, if we wanted to dispatch replaceAction defined above, we’d do this:

dispatch(replaceAction)

// or

dispatch({
  type: 'REPLACE',
  newCount: 42,
}) 
    - Because of the dependence of the dispatch function on the useReducer call that returned it, you can’t use dispatch1 to trigger state updates in authStore, nor can you use dispatch2 to trigger state updates in notificationStore.

This limitation means you have to manually keep track of which dispatch function belongs to which reducer, and it may ultimately result in more bloat. As of the time of writing this article, there is no known way to combine dispatch functions or reducers. 
    - Conclusion 
