Name API
========

The Name API does essentially three things:

1. Parses a full name into its component parts (first, middle, last ...)
2. Verifies the name does not include profanity, illegal charters, etc and attempts to match it to a known names database.
3. Appends gender if the name is known

Like all out APIs it is dead simple.

```text
http://bpi.briteverify.com/names.json?fullname=James+McLachlan&apikey=your-api-key
```

```JavaScript
{
  "fullname":"James McLachlan",
  "first":"James",
  "last":"McLachlan",
  "gender":"male",
  "salutation":"Mr. McLachlan",
  "status":"valid",
  "duration":0.124829515
}
```

And because we are nice guys, if you can't pass a fullname, we let you pass in first and last name instead ;-)

http://bpi.briteverify.com/names.json?first=James&last=McLachlan&apikey=your-api-key

Both of these requests will provide the same results.

Invalid Names & Error Codes
---------------------------

If there is something shady about the name, we will respond with an invalid status and and error code and error message that explain why we think the name is bunk.

```text
http://bpi.briteverify.com/names.json?fullname=Senor+Butt+Head&apikey=your-api-key
```

```JavaScript
{
  "fullname":"Senor Butt Head",
  "prefix":"Sr.",
  "first":"Butt",
  "last":"Head",
  "gender":"male",
  "salutation":"Sr. Head",
  "status":"invalid",
  "error_code":"contains_vulgarity",
  "error":"Contains vulgarity",
  "duration":0.137997264
}
```

Not to offend Senor Butt Head, and he maybe the exception to the rule here, but most of the time I doubt we want consider a name like this valid. So it is be marked invalid and the error_code is contains_vulgarity. Below is a list of all the error codes for the Name API.

## Error Codes
* unrecognized_name_format
* contains_multiple_first_names
* contains_vulgarity
* contains_nuisance_name
* contains_company_name
* contains_non_alphabetic

Statuses
--------

So like post of our APIs the statues are limited to the three values below.

* valid
* invalid
* unknown

This helps us keep things simple. But in this case the unknown status require a bit more discussion.

Unknown Names
-------------

If a first and last name match a database of known names, then the status will be set to "valid". If there is no match the status is set to "unknown." This is because is would be nearly impossible to match every possible name on the planet with 100% accuracy in a real-time. So rather than flagging a valid, non-western name as invalid we flag it as invalid and leave it up to you to decide how to handle it. This does mean names like "Aasdfasdf KJDSFKJSDFsdfsd" might get flagged as unknown, even though to a human eye this might seem to be obvious garbage. The unknown status does indicate that the name is suspicious, but since we can't be absolutely sure we leave it up to you.

And that's the Name API. 

