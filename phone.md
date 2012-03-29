Phone API
=========

The Phone verification service verifies phone numbers down to 7 and 10 digits, updates area codes, and appends location and service type information. This will enable you to not only know that a phone number is valid, but that it is from Charlotte, NC and is a mobile phone.

Valid Phone Number Example
--------------------------

```text
http://bpi.briteverify.com/phones.json?number=704-555-5555&apikey=your-api-key
```

```JavaScript
{
  "number":"7045555555",
  "areacode":"704",
  "prefix":"555",
  "suffix":"5555",
  "latitude":"35.226002",
  "longitude":"-80.838997",
  "city":"Charlotte",
  "state":"NC",
  "country":"United States of America",
  "country_code":"US",
  "timezone":"Eastern Time",
  "timezone_code":"05",
  "status":"valid",
  "service_type":"mobile".
  "duration":0.232561194
}
```

Service Types
-------------
* mobile
* pots (Plain Old Telephone Service, landline)
* digital

Invalid Phone Number Example
----------------------------

```text
http://bpi.briteverify.com/phones.json?number=704-123-1234&apikey=your-api-key
```

```JavaScript
{
  "number":"7041231234",
  "areacode":"704",
  "prefix":"123",
  "suffix":"1234",
  "state":"NC",
  "country":"United States of America",
  "country_code":"US",
  "status":"invalid",
  "error":"Invalid prefix",
  "error_code":"invalid_prefix",
  "duration":0.205319144
}
```

Error Codes
-----------

* invalid_areacode
* blank_phone_number
* invalid_format
* multiple_match
* invalid_prefix