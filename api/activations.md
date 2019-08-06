# Activations

Activations are the core resource to allowing members from your website to authenticate using your key.
For example, if you have a desktop application that you only want your members to access, then you can
integrate the Activations API to validate a key when they first open an app, save the activation, then
validate it every time they open the app.

> Before you can use the activations API, make sure you **allow activations** in your site settings, or you will get an error message with status `412`

The recommended flow/integration of the activations API in your app is:
1. On initial app open (if no activation is present), prompt them to enter a key and attempt to **create** an activation. Store the returned **activation token** for later use.
2. Every time a user opens the app when an activation is present, **retrieve** the activation using the stored **activation token** to validate their key.
3. When they click the deactivate button send a request to **destroy** the activation, and on success delete the stored **activation token**.

---

### Create an activation
Use this request when a user who hasn't yet activated opens your app. Requires the key, as well as some context about the device.

The **hwid** (unique hardware ID) and **device name** are displayed to the user on their dashboard so they can view their activation at any time.

#### `POST` **/activations**
Example request:
```json
{
	"key": "99CA4-BF382-32CC8-379A8",
	"activation": {
		"hwid": "11392i39291",
		"device_name": "Shreyas Macbook Pro"
	}
}
```

Example response:
```json
{
  "success": true,
  "key": "99CA4-BF382-32CC8-379A8",
  "activation_token": "i91xuxEVEoXs1t7z6Eda",
  "activation": {
    "hwid": "11392i39291",
    "device_name": "Shreyas Macbook Pro",
    "activated_at": 1564820349
  }
}
```

Save the `activation_token` given in the successful response, as you later use this to validate & destroy an activation.

---

### Retrieve an activation
Use this request when a user who has already activated logs into your app, and you need to validate their activation. This is necessary because users can deactivate from their dashboard, and you should block their access if their activation is no longer valid.


#### `GET` **/activations/{activation_token}**

Example response:
```json
{
  "success": true,
  "key": "99CA4-BF382-32CC8-379A8",
  "activation_token": "i91xuxEVEoXs1t7z6Eda",
  "activation": {
    "hwid": "11392i39291",
    "device_name": "Shreyas Macbook Pro",
    "activated_at": 1564820349
  }
}
```

A successful request will return the requested activation with `"success": true`. If this request is successful, it tells you that the user's activation is still valid and that you should allow them access.


---

### Destroy an activation
Use this request when a user wants to deactivate from within your app.


#### `DELETE` **/activations/{activation_token}**

Example response:
```json
{
  "success": true
}
```

On success you should delete their stored activation token, as it becomes obsolete after being destroyed.
