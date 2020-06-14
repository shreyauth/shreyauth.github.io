# Keys

The keys API allows you to easily create and view keys programatically

### Create key(s)

#### `POST` **/keys**
Example lifetime key request:
```json
{
	"payment_type": "card",
	"discord_role_id": "601816059191885850",
	"key_type": "lifetime",
	"price": 25,
	"quantity": 3,
	"allow_unbinding": true
}
```

Example renewal key request:
```json
{
    "payment_type": "card",
    "discord_role_id": "601816059191885850",
    "key_type": "renewal",
    "plan": "shreyauth_200",
    "initial_charge_amount": 500,
    "quantity": 3,
		"allow_unbinding": true
}
```
The `initial_charge_amount` parameter should **only** be used if you have a pricing structure that involves an initial charge of a different price from your normal subscription

Example response:
```json
{
  "success": true,
  "keys": [
    {
      "key": "FCE28-660FE-E7DCE-F4E3C",
      "expiration": null,
      "banned": false,
      "key_type": "renewal",
      "price": 0,
      "plan": "shreyauth_200",
      "fresh": true,
      "release_id": null,
      "trial_days": 0,
      "user": null
    },
    {
      "key": "4E584-F8275-A87D9-650A5",
      "expiration": null,
      "banned": false,
      "key_type": "renewal",
      "price": 0,
      "plan": "shreyauth_200",
      "fresh": true,
      "release_id": null,
      "trial_days": 0,
      "user": null
    },
    {
      "key": "138AC-61FFA-C2918-9C1A3",
      "expiration": null,
      "banned": false,
      "key_type": "renewal",
      "price": 0,
      "plan": "shreyauth_200",
      "fresh": true,
      "release_id": null,
      "trial_days": 0,
      "user": null
    }
  ]
}
```
