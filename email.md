Email API
=========

The email api is pretty straightforward. It is a simple GET request with two parameters:

1. address: the email address to be verified.
2. apikey: the api key for your BriteVerify account.

Here is an example request:

```text
https://bpi.briteverify.com/emails.json?address=james@briteverify.com&apikey=your-api-key
```

Unless something goes wrong, the HTTP status code will always be 200, regardless if the email is valid or invalid. The above request would yield the follow response.
```Javascript
{
  "address":"james@briteverify.com",
  "account":"james",
  "domain":"briteverify.com",
  "status":"valid",
  "connected":"true",
  "duration":0.104516605
}
```

Now if I pass an invalid email I will get not only a status of "invalid", I will also get an error and and error code explaining why the email is invalid. 

```text
https://bpi.briteverify.com/emails.json?address=james@yahoo.com&apikey=your-api-key
```

```Javascript
{
  "address":"james@yahoo.com",
  "account":"james",
  "domain":"yahoo.com",
  "status":"invalid",
  "error_code":"email_account_invalid",
  "error":"Email account invalid",
  "duration":0.141539548
}
```

Response Attributes
-------------------

* address: the email that was passed
* account: the inbox or account parsed from the email
* domain: the domain parsed from the email
* status: the status of the given email address
* error: the error message if the email is invalid
* error_code: a code representation of error
* connected: whether or not a valid email is connected to active online networks
* disposable: is the email a temporary or "disposable" email address
* duration: the time it took to process your request

Status
-----

There are only 4 statuses for an email in BriteVerify.

1. valid: The email represents a real account / inbox available at the given domain
2. invalid: Not a real email 
3. unknown: For some reason we cannot verify valid or invalid. Most of the time a domain did not respond quickly enough.
4. accept_all: These are domains that respond to every verification request in the affirmative, and therefore cannot be fully verified.

Error & Error Code
------------------

The error is really just a humanized version of the error code. So that an error_code of "email_account_invalid" will have an error of "Email account invalid." The error in this sense is really the "error message," something intended to be displayed in a Web Form or application UI.

###Error Codes

* email_address_invalid: the email is not formatted correctly
* email_domain_invalid: the domain does not exist or is not capable of receiving email
* email_account_invalid: the email account does not exist on the domain

Connected
---------

If you pass an additional parameter of "verify_connected=true", and the email is valid, we will then scan the online networks, wishlists, public directories, social networks, photo sharing sites (basically the internet itself) to see if the email is "connected" to other active accounts. This indicates that the email is much more likely to be actively used and connected to a real person. The connected attribute will be present if the email is valid and the verify_connected parameter is passed as true. 

```text
https://bpi.briteverify.com/emails.json?address=james@briteverify.com&verify_connected=true&apikey=your-api-key
```

```Javascript
{
  "address":"james@briteverify.com",
  "account":"james",
  "domain":"briteverify.com",
  "status":"valid",
  "connected":true,
  "duration":0.236341246
}
```

Disposable
----------

A temporary or "disposable" email address is one that a user has set up to live for only a short period of time for a variety of reasons. Usually you don't want to accept these types of emails, but we leave that up to how you wish to implement your own applications. These emails are just like any other emails and the "status" will reflect that. However, the disposable flag will be present if the email is from a known temporary email provider.

```Javascript
{
  "address":"james@veryhidden.com",
  "account":"james",
  "domain":"veryhidden.com",
  "status":"valid",
  "disposable":true
}
```


