

## Promises

async operations can return promise objects instead of using callbacks.

The promise object can be in one of three states:

-   pending (not yet completed)
-   fulfilled (completed successfully)
-   rejected (completed with errors)

“settled” refers to a promise that is not pending (fulfilled OR rejected).

## then and catch
`promise.then(fn)`: Specifies a function to call when promise fulfilled.
`promise.catch(fn)`: Specifies a function to call when promise rejected.
`promise.finally(fn)`: Specifies a function to call when promise settled.

These can be chained together for sequences of operations.

```jsx
fetchFromAPI1()
	.then( response1 => fetchFromAPI2(response1) )
	.then( response2 => console.log(response2) )
	.catch( err => console.log("Error: " + err) )
	.finally( () => console.log("Done.") );
```


## all and any

`newPromise = all(arrayOfPromises)`
`Promise.all()` takes an array of promises and returns a new promise.
- Rejected with first reason if any component promise is rejected.
- Fulfilled with array of values if all component promises are fulfilled.
- Fulfilled immediately if array is empty

`newPromise = allSettled(arrayOfPromises)`
Fulfilled when all component promises settle, never rejected.
Returns array of objects:
```javascript
{
  status: “fulfilled” / “rejected”,
  value: fulfillmentValue,
  reason: rejectionReason
}
```

`newPromise = any(arrayOfPromises)`
Fulfilled with value from first fulfilled component promise.
Rejected with `AggregateError` if all promises are rejected.

`newPromise = race(arrayOfPromises)`
Settles with status and value/reason from first promise to settle.

## Implementing Promises

Prefer asynchronous operation inside promises where possible.

The promise constructor takes a function that itself takes two functions as arguments (resolve and reject). The function passed should call the appropriate passed-in function to resolve the promise.

```jsx
const fs = require("fs");

function readFile(filePath) {
    return new Promise((resolve, reject) => {
				if (!fileExists(filePath)) {
					reject("File doesn't exist!");
				} else {
	        try {
	            const data = fs.readFileSync(filePath, "utf-8");
	            resolve(data);
	        } catch (error) {
	            reject(error);
	        }
				}
	    });
}

readFile(filePath)
	.then(data => console.log(data))
	.catch(err => console.error(err))
```

# `async` / `await`

`async` functions return promises and can use `await`.

`await` can be used to wait for async operations to resolve.

```javaScript
async function getGifUrl() {
	let resp1 = await fetch(wordnikApi);
	let json1 = await resp1.json();
	let resp2 = await fetch(giphyApi + json1.word);
	let json2 = await resp2.json();
	let imgUrl = json2.data[0].images['fixed_height_small'].url;
	return imgUrl;
}
```