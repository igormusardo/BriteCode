Phone API
=========

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
=============
* moble
* pots (Plain Ole Telephone Service, landline)
* digital

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