# Payment Sample App

This is an app that can be run on OakOS and can be used to test the Payment module.  It is a simple web page with inputs and buttons to test various transactions.

# Current Version

Check [package.json](/package.json) for the current version.  See [Docker Hub](https://hub.docker.com/r/oaklabs/payment-demo/tags/) for version history.

# Install

You can use Postman to send the following to your local OakOS instance at `/application/install`:

```json
{
	"services": [
		{
			"image": "index.docker.io/oaklabs/payment-demo:0.1.1",
			"username": "{{dockerUsername}}",
			"password": "{{dockerPassword}}"
		},
		{
			"image": "index.docker.io/oaklabs/component-payment:0.0.11",
			"username": "{{dockerUsername}}",
			"password": "{{dockerPassword}}"
		},
		{
			"image": "index.docker.io/lumenday/lumenday-oaktest:0.1.1",
			"username": "{{dockerUsername}}",
			"password": "{{dockerPassword}}"
		}
	]
}
```

If you are successful you should see a webpage come up on the kiosk with 3 buttons: Info, Configure, and Sale.

# FreedomPay

For FreedomPay you will also have to have:

1. A Windows PC or VM running FreedomPay services
2. An ingenico IPP350 or similar device plugged into (1) via USB
3. (1) must be accessible via the network by the OakOS machine.  You will use the `configure` action on the `payment-demo` UI to tell `component-payment` what the IP address is for (1).
4. (1) must also have an active internet connection in order to contact the remote FreedomPay services.
