# Errors

We use HTTP response codes to indicate the success or failure of an API request. Codes in the `2xx` range indicate success. Codes in the `4xx` range indicate an error that failed given the information provided (e.g., an incorrect activation token was provided). Codes in the `5xx` range indicate an error with our servers.

All errors come with a response with a `message` parameter, and a `success` parameter with value `false`.

> While most error messages are acceptable to display to your users, the primary purpose is to give developers context of an issue. For example, you probably wouldn't want your users seeing something like "Incorrect activation token" and getting confused, but seeing something like "Key already activated" would be fine. This is where you have to use your own discretion.

### Example error
HTTP Status `404`
```json
{
  "success": false,
  "message": "Invalid activation token"  
}
```
