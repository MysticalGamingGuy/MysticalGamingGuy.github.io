---
layout: default
comments: true
---

[Back](index)

# Stripe Couch and Functions

We're currently building a marketplace style app where payments work similarly to the model that lyft uses. 
users can pay forproducts/services that other users are providing. the seller and the platform will then get 
cuts of the sales.

# The Stack

- React Native
- CouchDB
- Azure Functions
- Stripe

# The Flow

- React Native App
- Open Browser modal for Stripe Oauth
- Redirect to HTTP Azure function on complete
- Call out to stripe to verify the users stripe account creation
- returns http with hyperlink with a Deep link to the app that passes in query params
- receive and parse deep link
- close the browser window
