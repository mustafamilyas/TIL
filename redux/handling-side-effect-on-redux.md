# Reactive Logic in React Redux Application

When you are woking on an application, there will be cases where you need to trigger some action when a specific event occurs. For example, you may want to show a notification when a user clicks on a button. Or you may want to send a request to the server when a user submits a form. Or you may want to update other parts of the application when a user changes a value in a form.

There are many ways to handle these cases. Let's talk about how you can handle these cases in a React Redux application.

## Using useEffect Hook

You can use `useEffect` hook to handle side effects in a React component. Here is an example:

```javascript
import React, { useEffect } from "react";
import { useDispatch } from "react-redux";

function MyComponent() {
  const dispatch = useDispatch();

  useEffect(() => {
    // Trigger an action when the component is mounted
    dispatch({ type: "SOME_ACTION" });
  }, [dispatch]);

  return <div>{/* ... */}</div>;
}
```

This is the simplest way to handle side effects in a React application in general. In this example, we are using `useEffect` hook to trigger an action when the component is mounted. We are using `dispatch` function to trigger the action.

This approach works well for simple cases and when we want to trigger something that only exists in the component. For example, you may want to trigger a toast notification when a component is mounted or sync some data when a redux store is updated.

If you are working on a complex application, you may need to handle side effects in a more organized way. You may need to handle side effects that are not specific to a component. For example, you may want to send a request to the server when a user submits a form. Or you may want to update other parts of the application when a user changes a value in a form.
This approach will quickly become complex and hard to maintain. That's why I suggest to use other approaches to handle side effects in a React Redux application if you can.

## Using Redux Thunk

You can use Redux Thunk to handle side effects in a React Redux application. Redux Thunk is a middleware that allows you to write action creators that return a function instead of an action object. Here is an example:

```javascript
// actions.js
export const someAction = () => {
  return async (dispatch, getState) => {
    // Trigger an action when the function is called
    dispatch({ type: "SOME_ACTION" });
    dispatch({ type: "ANOTHER_ACTION" });
    const awaitResult = await someAsyncFunction();
    dispatch({ type: "YET_ANOTHER_ACTION", payload: awaitResult });
  };
};

// MyComponent.js
import React from "react";

import { useDispatch } from "react-redux";
import { someAction } from "./actions";

function MyComponent() {
  const dispatch = useDispatch();

  const handleClick = () => {
    // Trigger an action when the button is clicked
    dispatch(someAction());
  };

  return <button onClick={handleClick}>Click me</button>;
}
```

In this example, we are using Redux Thunk to trigger an action when a button is clicked. We are using `someAction` action creator to trigger the action. `someAction` action creator returns a function that takes `dispatch` function as an argument. We are using `dispatch` function to trigger the action.

This approach works well when you want to trigger an action in specific order or when you want to trigger an action that depends on the result of another action. And it's really good to separate the logic from the UI layer.

## Using extraReducers in createSlice

The great thing about Redux Toolkit is that it isolates the local state and the logic that updates it in a "slice" of the Redux store. So, we don't have to worry mixing the local state with the global state. But, there are cases where we need to handle side effects in a slice. For example, we may want to update user status when the user update their subscription.

If you are using react toolkit, you can use `extraReducers` in `createSlice` to handle side effects in a React Redux application. `extraReducers` allows you to add extra reducers for actions that are not specific to the slice. Here is an example:

```javascript
import { createSlice } from "@reduxjs/toolkit";
import { subscribeSuccessAction } from "./actions";

export const slice = createSlice({
  name: "user",
  initialState: {
    name: "",
    status: "inactive",
  },
  reducers: {
    // ... other reducers
  },
  extraReducers: (builder) => {
    builder.addCase(subscribeSuccessAction, (state, action) => {
      state.status = action.payload.status;
    });
  },
});
```

With this approach, we don't need to fire an action to update the user status as we already have a reducer that listens to the `subscribeSuccessAction` action. This approach works well when you want to handle side effects that are specific to a slice.

But the downside of this approach is that it cannot trigger another action. If you need to trigger another action, you need to use Redux Thunk or another middleware.

## Using middleware

You can use middleware to handle side effects in a React Redux application. Middleware is a function that takes `store` as an argument and returns a function that takes `next` as an argument. Here is an example:

```javascript
const myMiddleware = (store) => (next) => (action) => {
  if (action.type === "SOME_ACTION") {
    // Trigger an action when "SOME_ACTION" is dispatched
    store.dispatch({ type: "ANOTHER_ACTION" });
  }

  return next(action);
};

export default myMiddleware;
```

In this example, `"ANOTHER_ACTION"` is triggered when `"SOME_ACTION"` is dispatched. But you have to be aware when using middleware as the `"next"` invocation means that the current action is passed to the next middleware or the reducer. If you want to stop the action from being passed to the next middleware or the reducer, you can return `null` or `undefined` from the middleware.

This provides a lot of flexibility and control over the side effects for example like authentication, logging, and other side effects that are not specific to a component or a slice but can decide whether the action should be passed to the next middleware or not.

But If you just want to trigger an action when a specific action is dispatched and don't want to deal with the complexity of middleware, you can use `createListenerMiddleware` from `@reduxjs/toolkit` package. This middleware allows you to listen to specific actions and trigger another action when the action is dispatched.

```javascript
import { createListenerMiddleware } from "@reduxjs/toolkit";

const listenerMiddleware = createListenerMiddleware();

listenerMiddleware.startListening({
  actionCreator: userSubscribed,
  effect: async (action, listenerApi) => {
    // Trigger an action when userSubscribed action is dispatched
    const result = await someAsyncFunction();
    listenerApi.dispatch({ type: "UPDATE_USER_STATUS", payload: result });
  },
});
```

## Conclusion

There are many ways to handle side effects in a React Redux application. You can use `useEffect` hook, Redux Thunk, `extraReducers` in `createSlice`, or middleware to handle side effects. Each approach has its own use case and you should choose the one that best fits your needs. If you are working on a complex application, you may need to use multiple approaches to handle side effects or even other libraries such as Redux Saga or Redux Observable. But you should always try to keep the side effects as simple as possible and avoid mixing the logic with the UI layer.
