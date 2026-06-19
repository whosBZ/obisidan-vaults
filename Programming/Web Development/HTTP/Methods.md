## GET
- Used only to fetch data from a location
- Does not make any updates
- Does not have a body
- Uses query parameters

## POST
- Used to send new data to a server
- Is not idempotent
- Does have a body

## PUT
- Used to completely change an item on the server
- Is idempotent
- Does have a body

## Patch
- Used to make partial updates to an item on a serer
- Is not idempotent
- Does have a body

## DELETE
- Used to remove items from a server
- Is not idempotent
- Does not have a body
- Uses query parameters