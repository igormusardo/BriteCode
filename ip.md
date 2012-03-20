IP Address API
==============

```text
http://bpi.briteverify.com/ips.json?address=174.96.214.3&apikey=your-api-key
```

```JavaScript
{
  "address":"174.96.214.3",
  "isp":"Road Runner Holdco LLC",
  "domain":"rr.com",
  "zip":"28201",
  "city":"Charlotte",
  "region":"North Carolina",
  "country":"United States",
  "country_code":"US",
  "longitude":"-80.843127",
  "latitude":"35.227087",
  "status":"valid",
  "duration":0.482947435
}
```

```text
http://bpi.briteverify.com/ips.json?address=174.96.214.323423423&apikey=your-api-key
```

```JavaScript
{
  "address":"174.96.214.323423423",
  "longitude":"0",
  "latitude":"0",
  "status":"invalid",
  "error_code":"address_invalid",
  "error":"Address invalid",
  "duration":1.517247136
}
```

Error Codes
-----------
* address_invalid