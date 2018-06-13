# Quick Start

## What you need to know

This quick tutorial assumes some basic familiarity with programming.

You’ll need to understand how to call a service using HTTP/S, how to set headers in HTTP messages and so on.

It will be handy to have some understanding of RESTFul design, but it’s not strictly necessary.

And JSON or XML for the message technology.

The purpose of this application to enable applications to send arbitrary messages to your email.

Step 1.

Create a [free account](https://www.fireanote.com/#!/signup).

Check your email and confirm your new account.

Then you may log into your dashboard.

Step 2.

Create a [new group](https://www.fireanote.com/#!/dashboard) of apps.

The group is a container for all the apps that are a set of apps in the same offering or group, for instance a group may contain an Android app and an IOS app, however they are the same app but on different platforms.

Step 3.

Add a [new app](https://www.fireanote.com/#!/widget/add-app).

Store the generated key as this identifies the app in the system and is used in the notifications you send from your app.

You may also find this key in [your apps](https://www.fireanote.com/#!/widget/your-apps).

Step 4.

Fire a note from the [test harness](https://www.fireanote.com/#!/widget/test-harness).

The message payload is displayed at the bottom of the page and it can be copy/pasted to be used in your calling system.

```
{
  "notificationId": "Y2xpZW50LWlkPU43M2lFb3=",
  "description": "DEFCON 1",
  "dataType": "text/plain",
  "category": "IMAGE_UPLOAD",
  "priority": "A1",
  "body": "It is the best car that I have ever driven!"
}
```

The notification is displayed in the [notifications console](https://www.fireanote.com/#!/widget/console) once you have clicked `Send`.

And the same notification will arrive in your email inbox in good time. If there are too many notifications a message will arrive telling you to check your [notifications console](https://www.fireanote.com/#!/widget/console).