# Instruction: SignOut

The endpoint is intended for user logout and invalidation of access tokens. When calling this endpoint, the server should deauthorize the user and invalidate the current access token.


#### **Request Sample: Shell / cURL**

At the time of sending the request, the curl command should be as follows:

```cURL
curl --request POST \
  --url https://crpt-backend-main-service.sandbox.testessential.net/signout \
  --header 'Accept: application/json' \
  --header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiI4NTU0ZDc0My05ZDExLTQ5YTEtYTMyMy03YmRmOGQ4NDdjMjEiLCJleHAiOjE3MDk3MjQ1NjQsImlhdCI6MTcwOTYzODE2NH0.deZXGfjS7oVprz2XoZseeYa7l8ti8aAJaELBeDDtglI' \
  --header 'Content-Type: application/json' \
  --header 'X-DeviceId: '
```


### **Response Example**

The response status code indicates that the request was successfully processed.

```json

{
  "result": "ok"
}
```



