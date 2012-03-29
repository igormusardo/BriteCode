IP Address API
==============

The IP service validates an IP address and returns related geographic and ISP data. IP addresses are often given in blocks to internet service providers and other institutions. The location is an approximation based on the location of the institution.


Examples
--------

###A Valid IP

```text
http://bpi.briteverify.com/ips.json?address=000.00.000.0&apikey=your-api-key
```

```JavaScript
{
  "address":"000.00.000.0",
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

###An invalid IP

```text
http://bpi.briteverify.com/ips.json?address=000.00.000.023423423&apikey=your-api-key
```

```JavaScript
{
  "address":"000.00.000.023423423",
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