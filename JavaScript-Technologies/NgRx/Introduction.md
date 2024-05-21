<h1>Introduction</h1>

- NgRx ia an framework for managing state in Angular.
- NgRx is a framework for building reactive applications in Angular.
- It's inspired from `Redux`.
- NgRx Used for Organising & handling for state-management in Angular.
- In Angular we have several approaches for state management all are having pros and concerns.
- For state management in Angular we can use @input & @output decorators, services, localstorage, sessionstorage and NgRx.

<h2>NgRx State Management Life Cycle</h2>

<img src="https://ngrx.io/generated/images/guide/store/state-management-lifecycle.png" alt="not found">

<h3>STATE</h3>

- State is an JSON object it can hold any data types.
- Unshared data, from data & Router data no need to keep in the state.
- State data can be changed but Structure never changed.

```ts
const initialState = {
    loading: true,
    userList: [],
    userObj: {},
    errorMessage: ""
}
```

<h3>ACTIONS</h3>

- Any event performed in component need to dispatch action using action creaters.
- Each action has the type property.
- Action name should be unique.
- Using payload option we can send data.

```js
export const makeRequest = () => {
    return {
        type: MAKE_REQUEST
    }
}
export const failRequest = (err) => {
    return {
        type: FAIL_REQUEST,
        payload: err
    }
}
export const getUserList = (data) => {
    return {
        type: GET_USER_LIST,
        payload: data
    }
}
export const deleteUser = () => {
    return {
        type: DELETE_USER,
    }
}
export const addUser = (data) => {
    return {
        type: ADD_USER,
    }
}
```

<h3>REDUCERS</h3>

- Reducers are pure functions.
- It takes action & initial state as the input.
- Reducers will calculate/finalize the data from action & initial state.
- Final state data will be available in store.

```js
export const Reducer = (state = initialState, action) => {
    switch (action.type) {
        case MAKE_REQUEST:
            return {
                ...state,
                loading: true
            }
        case FAIL_REQUEST:
            return {
                ...state,
                loading: false,
                errorMessage: action.payload
            }
        case GET_USER_LIST:
            return {
                loading: false,
                errorMessage: '',
                userList: action.payload,
                userObj: {}
            }
        default:
            return state
    }
}
```
**Sample ACTION Creaters:**

```js
export const fetchUserList = () => {
    return (dispatch) => {
        dispatch(makeRequest());
        axios.get('http://localhost:8000/user')
            .then((res) => {
                const userList = res.data;
                dispatch(getUserList(userList));
            })
            .catch((err) => {
                dispatch(failRequest(err.message));
            })
    }
}
export const RemoveUser = (code) => {
    return (dispatch) => {
        dispatch(makeRequest());
        axios.delete('http://localhost:8000/user/' + code)
            .then((res) => {
                dispatch(deleteUser());
            })
            .catch((err) => {
                dispatch(failRequest(err.message));
            })
    }
}
```


<h2><a href="https://github.com/sanjay9616/JavaScript/blob/master/JavaScript-Technologies/NgRx/README.md"> 🔙 Back</a></h2>
