# React Hooks

```fsharp

//-------------------------- State --------------------------
# useState
// when we have 'simple logic' to handle use 'useState'
const [count, setCount] = useState(5);



# useReducer
// when we have 'more complex logic' to handle use 'useReducer'
// reducerFn: is a pureFn, we can keep the logic outside of component
const [{ todos, updatedCount }, dispatch] = useReducer(reducer, { todos: [], updatedCount: 0 });


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



