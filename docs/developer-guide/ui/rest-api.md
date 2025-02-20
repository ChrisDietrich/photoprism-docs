Routes and parameters can be found in our API docs:
 
https://godoc.org/github.com/photoprism/photoprism/internal/api

## Examples

### Basic 
```
GET /api/v1/photos?count=10
```
_Note: Routes are going to change while we are developing the frontend. The API is not covered by a deprecation policy._

### With authentication

PhotoPrism [uses](https://github.com/photoprism/photoprism/blob/92df3aa/internal/api/session.go#L102) `X-Session-ID` HTTP header as authentication method:
```
curl -H "X-Session-ID: xyz" http://localhost:2342/api/v1/photos?count=10
```
Replace `xyz` by `session_id` value of your active browser session, which can be found inside local storage. 

## Links ##
- [Mat Ryer: How I write Go HTTP services after seven years](https://medium.com/statuscode/how-i-write-go-http-services-after-seven-years-37c208122831)
