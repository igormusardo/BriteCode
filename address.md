US Postal Address API
=====================

The Postal Address service provides Delivery Point Verification (DPV) of a US address. This ensures that the address is capable of receiving mail, not just that if physically exists. This means that if an apartment number is omitted for an address that is a highrise apartment build, then it will be flagged invalid.

Examples
--------

###Valid US Address 

```text
http://bpi.briteverify.com/addresses.json?address[street]=120+N+Cedar&address[unit]=Apt+3201&address[zip]=28210&apikey=your-apikey
```

```JavaScript
{
  "street":"120 N Cedar St",
  "unit":"Apt 3201 ",
  "suite":"Apt 3201 ",
  "city":"Charlotte",
  "state":"North Carolina",
  "state_code":"NC","
  zip":"28202",
  "plus4":"1362",
  "country":"United States of America",
  "country_code":"US",
  "congressional_district":"12",
  "address_type":"Highrise",
  "status":"valid",
  "corrected":true,
  "duration":0.326942834
}
```

###Error Example

```text
http://bpi.briteverify.com/addresses.json?address[street]=120+N+Cedar&address[zip]=28210&apikey=your-apikey
```

```JavaScript
{
  "street":"120 N Cedar St",
  "city":"Charlotte",
  "state":"North Carolina",
  "state_code":"NC",
  "zip":"28202",
  "plus4":"1292",
  "country":"United States of America",
  "country_code":"US",
  "congressional_district":"12",
  "address_type":"Highrise",
  "status":"invalid",
  "corrected":true,
  "error_code":"suite_required",
  "error":"Suite required",
  "duration":0.383370784
}
```

Error Codes
-----------

* zip_code_invalid
* unknown_street
* directionals_or_suffix_invalid
* non_deliverable_address
* multiple_address_match
* early_warning_error
* missing_minimum_inputs
* suite_range_invalid
* suite_required
* street_number_invalid
* street_number_required
* box_number_invalid
* box_number_required
* private_mailbox_required
* suite_range_extraneous