- JavaScript is single threaded, meaning can only run one task at a time
- To counteract long running tasks blocking the application you use asynchronous programming
- The application can then continue while a script waits for a result
- Once that result is made available it will be picked up and continue where it left off

## Promises

- Defer further tasks until a previous action has completed or failed
- They don't return an immediate result but return a "Promise" that they will at a later point.
- Promises have 2 properties, State and Result
	- State: Pending, Result: undefined
	- State: Fulfilled, Result: resolved value
	- State: Rejected, Result: Error object
- A promise is created either by creating a new Promise or calling a function that returns a Promise.
- A promise will then call **then** as soon as the state changes from pending to fulfilled and passes the returned data to it and then onto any following chained **then**
- The promise will only invoke a catch if the state changes to rejected

```javascript
function fetchData(url) {
    fetch(url)
        .then((response) => response.json())
        .then((json) => console.log(json))
        .catch((error) => {
            console.error(`Error : ${error}`);
        });
}
fetchData("https://­www​.­usemodernfullstack​.­dev​/­api​/­v1​/­users");
```
## Async / Await

- Allows for simpler and cleaner handling of Asynchronous requests
- You no longer need chained functions and can instead use a standard function similar to synchronous functions
- You do this by marking a function as **async**
- When you call this function, if you want to wait for the resolved result, you use the keyword **await**

```javascript
async function fetchData (url) {
    try {
        const response = await fetch(url);
        const json = await response.json();
        console.log(json);
    } catch (error) {
        console.error(`Error : ${error}`);
    }
}

await fetchData("http://fakeurl.com/v1/data)
```

- 

