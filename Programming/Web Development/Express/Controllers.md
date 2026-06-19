- Handle the logic behind a route to tell it which services to call
- This will handle the responses to the request to remove it from the routes
- Controllers take in a request, a response and a next function as parameters

```typescript
export const controlFunc = (req: Request, ses, Response, next: NextFunction) => {
	try {
		if(req.body){
			res.status(200).json({status: 'sucess', message: 'Found body})
		} else {
			res.status(400).json({status: 'fail', message: 'No body'})
		}
	} catch (error) {
		res.status(400).json({status: 'fail', message: 'An error occured'}))
	}

```

- You will use controllers to call service functions so isolate the control logic from the service logic, allowing you to easily change the service without touching controllers or routes