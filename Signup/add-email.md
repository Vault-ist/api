# Instruction: Add Email

This endpoint is designed for adding a new email address to a user's account.
> 📘 After [confirming the phone number](https://vault-bxou.readme.io/reference/confirm-phone-number) or after [user authorization](https://vault-bxou.readme.io/reference/signin), you will receive an **access_token**. You need to enter this **access_token** in the `Token` field.


## **The required body parameters**

```json json_schema
{
  "type": "object",
  "required": ["email"],
  "properties": {
    "email": {
      "type": "string",
      "description": "the new email address to be added to the user's account.",
    }
  }
}

```

## **Request Sample: cURL**

At the time of sending the request, the curl command should be as follows:

```curl cURL
curl --request PUT \
     --url https://api.vault.sandbox.testessential.net/v2/mobile/email/add \
     --header 'accept: application/json' \
     --header 'authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIwNTFhYTc3Mi0yNDk4LTQ0ZTEtODdmYi0zYzNhZDdlMTY1ODgiLCJleHAiOjE3MTEwMzgxMjAsImlhdCI6MTcxMDk1MTcyMH0.yUvwJWyilQOdeKi3rnCAyaU3QuCEV0ijoZGCHY9NhTA' \
     --header 'content-type: application/json' \
     --data '
{
  "email": "test@gmail.com"
}
'
```


## **Response Example**

The response status code indicates that the request was successfully processed.

```json
{
  "result": "ok"
}
```

![Logo](https://files.readme.io/0dcc41c-logo.png)

