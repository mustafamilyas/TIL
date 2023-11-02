# Comparison between React and Vue

1. **State**

   React uses `useState` and `useReducer` hook to manage state. Vue uses `ref` and `reactive` to manage state if you are using composition API. `ref` is used to create a any reactive value. `reactive` is used to create a reactive object.

   ```typescript
   // React
   const [state, setState] = useState(0);

   const [reducerState, dispatch] = useReducer(reducer, {
     counter: 0,
   });

   function reducer(state, action) {
     switch (action.type) {
       case "increment":
         return {
           ...state,
           counter: state.counter + 1,
         };
       case "decrement":
         return {
           ...state,
           counter: state.counter - 1,
         };

       default:
         return state;
     }
   }

   // to update the state
   setState(1);
   dispatch({ type: "increment" });

   // Vue
   const state = ref(0);
   const onlyObjectState = reactive({ counter: 0 });

   // To update the state
   state.value = 1; // need to add `.value to make it reactive`
   onlyObjectState.counter = 1;
   ```

   the reason why we need to add `.value` to make it reactive is because vue is using object proxy to make the object reactive. `ref` is using `getter` and `setter` to make the value reactive.

2.
