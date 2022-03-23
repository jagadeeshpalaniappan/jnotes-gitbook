# React Hooks

```fsharp

//-------------------------- State --------------------------
# useState
// when we have 'simple logic' to handle use 'useState'
const [count, setCount] = useState(5);



# useReducer
// when we have 'more complex logic' to handle use 'useReducer'
// reducerFn: is a pureFn, we can keep the logic outside of component

function reducerFn(currState, action) {
  if (action.type === 'ADD_TODO') {
    const newTodo = action.payload;
    const newState = { todos: [...currState.todos, newTodo], updatedCount: state.updatedCount + 1 }
    return newState;
  }
  return currState;
}
const intialState = { todos: [], updatedCount: 0 };

function Btn({ label, increment }) {
  const [newState, dispatch] = useReducer(reducerFn, intialState);
  const { todos, updatedCount } = newState;
  
  const addTodo = () => dispatch({ type: 'ADD_TODO', payload: 'My new todo' });
  return (<div>
    <button onClick={addTodo}>Add</button>
    <ul>{todos.map(todo => <li>{todo}</>)}
    <p>{updatedCount}</p>
  <div/>);
});



//-------------------------- onStateChange --------------------------

# useEffect 
// when we have 'fn: that uses useState' which is supposed to call only when dependency prop change // NOT every render

const _state2Changed = () => {
  console.log("'state2' changed");
  const cleanup = () => {
    console.log("cleanup here (releated to 'state2') ");
  };
  return cleanup;
};

// useEffect: accepts 'twoArgs'  arg1:fn, arg2:array | returns: cleanUp actitivity
useEffect(_state2Changed, [state2]);
  

# useLayoutEffect 
// simmilarTo useEffect, but this will called after the browser layout/paints the component


//-------------------------- Fn (better version) --------------------------

# useCallback
// when we do not want to create a newFn everytime component render
// - This helps just creating the fn once, doesnt executeFn

const incrementFn = () => setCount(c => c + 1); // BAD: createsNewFn on ever render
const incrementFn = useCallback(() => setCount(c => c + 1), [setCount]); // GOOD: usesTheSameFn ref again


# useMemo
// when we have 'pureFn' which is supposed to call/execute the fn only when dependency prop change // NOT every render
// - this helps not 'executeFn' on every render

const longestUserId = findLongestUserIds(userIds); // BAD: executesFn on ever render
const longestUserId = useMemo(() => findLongestUserIds(userIds), [userIds]); // GOOD: executesFn only when 'userIds' changes

# React.memo(..)
function Btn({ label, increment }) {
  console.log("Btn:: render");
  return <button onClick={() => increment(5)}>{label}</button>;
});
const BtnMemoized = React.memo(Btn);
// React.memo: helps to 'render' the component only when 'prop' chnages
// here: whenever 'label' or 'increment' prop changes - it renders the components, otherwise it doesn't render


//-------------------------- Ref --------------------------


# useRef 
// - to get actual DOM component reference
// - when we want to change some value without affecting/calling the component render
const fnameInputRef = useRef();
const countRef = useRef(0); // countRef.current = countRef.current + 1


//-------------------------- Context API --------------------------

# createContext & useContext 
// if we do not want to pass 'prop' to each and every component, we can make use of these hooks.

const UserContext = createContext(null);

const App = () => {
  const [user, setUser] = useState(null);
  const value = useMemo(() => ({ user, setUser }), [user, setUser]);
  return (
    <div>
      <UserContext.Provider value={value}>
        <Comp1 />
        <Comp2 />
      </UserContext.Provider>
    </div>
  );
};

// Comp1:
const { user, setUser } = useContext(UserContext);  // we get or set user value from any component without passing to props

// Comp2:
const { user, setUser } = useContext(UserContext);  // we get or set user value from any component without passing to props


```



{% embed url="https://stackblitz.com/edit/jnotes-react" %}

