# `useEffect`

> In **React**, the useEffect hook is used to handle side effects in functional components. Side effects can include data fetching, subscriptions, timers, manually changing the DOM, and other operations that need to occur as a result of rendering.

```javascript
useEffect(`Effect Function`, `Dependency Array`);

useEffect(() => { ... }, []);

useEffect(() => { function; call the function }, []);
```


## Purpose of `useEffect`

The primary purposes of useEffect are:

- Data Fetching: To fetch data from an API when a component mounts or when certain dependencies change.
- Subscribing/Unsubscribing: To set up subscriptions (like WebSocket connections) and clean them up when the component unmounts or dependencies change.
- Timers: To manage timers (like setTimeout or setInterval) and ensure they are cleared when the component unmounts or when dependencies change.
- Direct DOM Manipulation: To perform direct DOM manipulations, although this should generally be avoided in favor of React's declarative approach.

## Usage of `useEffect`

The useEffect hook takes two arguments:

- **Effect Function**: A function that contains the code you want to run after rendering.
- **Dependency Array**: An optional array that specifies when the effect should re-run. If any value in the array changes, the effect will run again.

## Important Points

- **Runs After Render**: The effect function runs after the render phase, allowing you to interact with the DOM or fetch data without blocking rendering.
- **Cleanup Function**: If your effect returns a function, React will run that function before the component unmounts or before the effect runs again. This is useful for cleaning up subscriptions or timers.
- **Dependencies**: By specifying dependencies, you control when the effect should run again. If you omit the dependency array, the effect runs after every render. If you provide an empty array, it runs only once on mount.

## Basic Example

Here's a simple example demonstrating useEffect for data fetching:

```javascript
const [products, setProducts] = useState([]);

useEffect(() => {
    const fetchData = async () => {
      try {
        const data = await fetchAllProducts(setOffline);
        setProducts(data);
      } catch (err) {
        console.error(err);
        setOffline(true);
        setError("Unable to fetch data, offline mode");
      }
    };

    fetchData();
  }, []);
```
