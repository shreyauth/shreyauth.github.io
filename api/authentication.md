# Authentication

All authentication is done via your assigned **API Key**. Submit your API key via an `Authorization` header
as a Bearer token.

Your key can be found in the **API Authentication** section of your site settings. If for any reason your
API key becomes compromised or insecure, you may reroll it. Please reroll with caution as we do not allow
a grace period for any applications integrated to the API using any previous API keys.

### Header example
```
Content-Type: application/json
Authorization: Bearer xxxxxxxxxxxxx
```

### Unauthorized response
If you make a request and your `Authorization` header is invalid, you will see a JSON response that looks like this, with a HTTP `403` status
```json
{
  "success": false,
  "message": "Unauthorized"
}

```
