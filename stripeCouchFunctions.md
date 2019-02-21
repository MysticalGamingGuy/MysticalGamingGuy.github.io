---
layout: default
comments: true
---

[Back](index)

# Stripe Couch and Functions

At Duck Labs I'm currently working on a marketplace style app where payments work similarly to the model that lyft uses. whereby users can pay for products/services that other users are providing. The seller and the platform will then get a cut of the sales.

# The Stack

We are using the current technologies in our app:

- React Native w/ Expo
- CouchDB
- Azure Functions
- Stripe

Important things to note. Expo, at the time of writing, does not support the inclusion of native code into projects. due to this limitation, any native support that stripe has is useless to us. Now techniaclly expo allows native code itf you go those the process of ejection your app. This is where native project files are created for xcode and andriod studio and expo no longer handles the building process as new native code wouldn't be accounted for. Expo is currenly working on experimental features to work around this limitation, but currently it's not mature enough to warrent it's use in our app. This now leaves us with using stripes web authentication. 

My inital idea was to have stripe 'on completion' redirect take to user to our app through a deep link. essential a link whos protocol isnt http:// but myApp://. this woud've worked if stripe allowed those types of links... but they don't. so the question then is, where DO i redirect to. Well, this was what i decided to go with.


# The Flow

- React Native App
- Open Browser modal for Stripe Oauth
- Redirect to HTTP Azure function on complete
- Call out to stripe to verify the users stripe account creation
- returns http with hyperlink with a Deep link to the app that passes in query params
- receive and parse deep link
- close the browser window
