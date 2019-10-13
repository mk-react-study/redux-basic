# redux-basic

* Component -> Dispatches(Actions) -> Reducers (Updates) -> Central Store  -> Triggers(Subscriptions)
* npm install --save-dev cross-env
* Create Reducers 
```
import * as actionTypes from '../actions';
const initialState = {
    counter: 0
};
const reducer = ( state = initialState, action ) => {
    switch ( action.type ) {
        case actionTypes.INCREMENT:
           return {
                ...state,
                counter: state.counter + 1
            }
        case actionTypes.ADD:
            return {
                ...state,
                counter: state.counter + action.val
            }
    }
    return state;
};
export default reducer;
```
*  
 ```
 import { createStore, combineReducers } from 'redux';
const rootReducer = combineReducers({
  prop1: reducer1,
  prop2: reducer2
});
const store = createStore(rootReducer);
```
* Add Redux To App
```
import { Provider } from 'react-redux';
ReactDOM.render(<Provider store={store}><App /></Provider>, document.getElementById('root'));
```
* 
