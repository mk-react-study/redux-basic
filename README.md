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
*  Create Store
 ```
 import { createStore, combineReducers } from 'redux';
const rootReducer = combineReducers({
  prop1: reducer1,
  prop2: reducer2
});
const store = createStore(rootReducer);
```
* Add Redux Store To App
```
import { Provider } from 'react-redux';
ReactDOM.render(<Provider store={store}><App /></Provider>, document.getElementById('root'));
```
* Setup container
```
import React, { Component } from 'react';
import { connect } from 'react-redux';

class Counter extends Component {
    render () {
        return (
            <div>
                <CounterOutput value={this.props.ctr} />
                <CounterControl label="Increment" clicked={this.props.onIncrementCounter} />
                <CounterControl label="Add10" clicked={this.props.onAddCounter}  />
            </div>
        );
    }
}
const mapStateToProps = state => {
    return {
        ctr: state.prop1.counter,
        storedResults: state.prop2.results
    }
};
const mapDispatchToProps = dispatch => {
    return {
        onIncrementCounter: () => dispatch({type: actionTypes.INCREMENT}),
        onAddCounter: () => dispatch({type: actionTypes.ADD, val: 10}),
    }
};
export default connect(mapStateToProps, mapDispatchToProps)(Counter);
```
