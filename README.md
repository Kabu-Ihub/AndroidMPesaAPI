# Android MPESA SDK [![CircleCI](https://circleci.com/gh/twigaeng/android-mpesa-sdk/tree/master.svg?style=shield)](https://circleci.com/gh/twigaeng/android-mpesa-sdk/tree/master)
This is a simple Android MPESA SDK to allow you to integrate Safaricom MPESA API dubbed Daraja with your Android App with ease. 
> This version only offers the STKPush Support

## Getting Started
These instructions will help you set up this library easily on your current project and working in no time. You only need a few configurations to start working!

## Setting Up
To be able to use the following library, you will need to add the following gradle dependency in your build.gradle(module:app) file

```gradle
dependencies {
  implementation 'com.twigafoods.daraja:mpesa-daraja:0.0.1'
}
```

That is the basic set up needed to be able to use the library in your applications! Daraja requires minSdkVersion Level 16 

## Permissions
If you are using this Library, this means your Application is using Internet, so don't forget the following permission also:

```
<uses-permission android:name="android.permission.INTERNET"/>
```

That's it, you have set up the required permissions and ready to go!

## How do I use Daraja?

Simple use cases with Daraja will look something like this:

```java
//For Sandbox Mode
Daraja.with(CONSUMER_KEY, CONSUMER_SECRET, Env.SANDBOX);

//For Production Mode
Daraja.with(CONSUMER_KEY, CONSUMER_SECRET, Env.PRODUCTION);
```
This initializes Daraja and also generates a Token to be used for further requests. This should be done in your Application onCreate Method, to allow Daraja generate the Authorization Token as early as possible.

With the Token generated, we can now request an STKPush with ease. Just call the sendSTKPush as shown here:

```java
Daraja.sendSTKPush(Env.SANDBOX, BUSINESS_SHORT_CODE, PASS_KEY, AMOUNT, PARTY_A, PARTY_B, PHONE_NUMBER, CALLBACK_URL, ACCOUNT_REFERENCE, TRANSACTION_REFERENCE);
```

This sanitizes all the data, as required by Safaricom before making a request for the STKPush. You only need to pass the parameters and Daraja will do the rest!