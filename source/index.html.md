---
title: Data Drum API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - php
  - python
  - javascript
  - ruby

toc_footers:
  - <a href='mailto:info@datadrum.com'>Support</a>
  - <a href="https://datadrum.com">Back to Data Drum</a>

includes:
  - errors

search: false
---

# Introduction

Welcome to Data Drum's elegant and easy-to-use API. It's really easy to get going. All you need is an API Key and the ability to send that key in the headers of a GET request to:

`https://api.datadrum.com/...`

You can get access to any data you like by following the instructions below.

A list of indicators is available <a href="#available-indicators">through the API</a> (with no authentication required) or within the Data Drum platform itself. The examples to the right will be getting data on Ukraine annual inflation, using the indicator identifier `ua_inf_annual.cpi`.

And output will be in JSON. You can easily change this to CSV (`csv`), XML (`xml`) or Excel (`xlsx`) by replacing `json` with one of those in the URL.

# Data Retrieval

## Latest Value

```php
<?php
$curl = curl_init();
curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.datadrum.com/json/ua_inf_annual.cpi/latest",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "GET",
  CURLOPT_HTTPHEADER => array(
    "token: ".your_token
  ),
));
$response = curl_exec($curl);
curl_close($curl);

$json_response = json_decode($response, true);
var_dump($json_response);
?>
```

```python
import requests
import json

req = requests.get("https://api.datadrum.com/json/ua_inf_annual.cpi/latest", headers={"token": your_token})
print(json.loads(req.text))
```

```shell
curl "https://api.datadrum.com/json/ua_inf_annual.cpi/latest"
  -H "token: your_token"
```

```javascript
var request = new Request("https://api.datadrum.com/json/ua_inf_annual.cpi/latest", {
	method: 'GET',
	headers: new Headers({
		'token': your_token
	})
})

fetch(request)
	.then((response) => response.json())
	.then(function(json_response){
		console.log(json_response)
	});
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://api.datadrum.com/json/ua_inf_annual.cpi/latest")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true

request = Net::HTTP::Get.new(url)
request['token'] = your_token

response = http.request(request)
puts response.read_body
```

> The above code would return the following JSON output:

```json
{
	"status": 200,
	"error": null,
	"headers":
    [{
  		"name": "ua_inf_annual.cpi",
		"territory":"Ukraine",
  		"english": "CPI Annual Inflation",
  		"units": "%",
  		"source": "Data Drum calculations based on State Statistics Service of Ukraine"
  	}],
	"data":
    [
      {"date": "2018-07-31", "ua_inf_annual___cpi": 8.8996054362122}
    ]
}
```

`GET https://api.datadrum.com/json/<INDICATOR>/latest`

This endpoint returns the latest value held by Data Drum for a particular indicator.

Ukraine's annual inflation figure was just shy of 9% when this documentation was written in August 2018.

## Earliest Value

```php
<?php
$curl = curl_init();
curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.datadrum.com/json/ua_inf_annual.cpi/earliest",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "GET",
  CURLOPT_HTTPHEADER => array(
    "token: ".your_token
  ),
));
$response = curl_exec($curl);
curl_close($curl);

$json_response = json_decode($response, true);
var_dump($json_response);
?>
```

```python
import requests
import json

req = requests.get("https://api.datadrum.com/json/ua_inf_annual.cpi/earliest", headers={"token": your_token})
print(json.loads(req.text))
```

```shell
curl "https://api.datadrum.com/json/ua_inf_annual.cpi/earliest"
  -H "token: your_token"
```

```javascript
var request = new Request("https://api.datadrum.com/json/ua_inf_annual.cpi/earliest", {
	method: 'GET',
	headers: new Headers({
		'token': your_token
	})
})

fetch(request)
	.then((response) => response.json())
	.then(function(json_response){
		console.log(json_response)
	});
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://api.datadrum.com/json/ua_inf_annual.cpi/earliest")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true

request = Net::HTTP::Get.new(url)
request['token'] = your_token

response = http.request(request)
puts response.read_body
```

> The above code would return the following JSON output:

```json
{
  "status":200,
  "error":null,
  "headers":
    [{
      "name":"ua_inf_annual.cpi",
      "territory":"Ukraine",
      "english":"CPI Annual Inflation",
      "units":"%",
      "source":"Data Drum calculations based on State Statistics Service of Ukraine"
    }],
  "data":
    [
      {"date":"2006-01-31","ua_inf_annual___cpi":9.7251585623679}
    ]
}
```

`GET https://api.datadrum.com/json/<INDICATOR>/earliest`

This endpoint returns the earliest value held by Data Drum.

The earliest data we hold for Ukraine annual inflation is from January 2006 when the figure was 9.7%

## Specific Date

```php
<?php
$curl = curl_init();
curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.datadrum.com/json/ua_inf_annual.cpi/2015-04-30",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "GET",
  CURLOPT_HTTPHEADER => array(
    "token: ".your_token
  ),
));
$response = curl_exec($curl);
curl_close($curl);

$json_response = json_decode($response, true);
var_dump($json_response);
?>
```

```python
import requests
import json

req = requests.get("https://api.datadrum.com/json/ua_inf_annual.cpi/2015-04-30", headers={"token": your_token})
print(json.loads(req.text))
```

```shell
curl "https://api.datadrum.com/json/ua_inf_annual.cpi/2015-04-30"
  -H "token: your_token"
```

```javascript
var request = new Request("https://api.datadrum.com/json/ua_inf_annual.cpi/2015-04-30", {
	method: 'GET',
	headers: new Headers({
		'token': your_token
	})
})

fetch(request)
	.then((response) => response.json())
	.then(function(json_response){
		console.log(json_response)
	});
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://api.datadrum.com/json/ua_inf_annual.cpi/2015-04-30")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true

request = Net::HTTP::Get.new(url)
request['token'] = your_token

response = http.request(request)
puts response.read_body
```

> The above code would return the following JSON output:

```json
{
  "status":200,
  "error":null,
  "headers":
    [{
      "name":"ua_inf_annual.cpi",
      "territory":"Ukraine",
      "english":"CPI Annual Inflation",
      "units":"%",
      "source":"Data Drum calculations based on State Statistics Service of Ukraine"
    }],
  "data":
    [
      {"date":"2015-04-30","ua_inf_annual___cpi":60.931899641577}
    ]
}
```

`GET https://api.datadrum.com/json/<INDICATOR>/<DATE>`

This endpoint returns the value of an indicator on a specific date, which must be in the format `YYYY-MM-DD` or `earliest` or `latest`.

If no value is held for the date you specify, the latest value before the date you specify will be used.

Annual inflation in Ukraine was at more than 60% in April 2015.

## All Values

```php
<?php
$curl = curl_init();
curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.datadrum.com/json/ua_inf_annual.cpi",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "GET",
  CURLOPT_HTTPHEADER => array(
    "token: ".your_token
  ),
));
$response = curl_exec($curl);
curl_close($curl);

$json_response = json_decode($response, true);
var_dump($json_response);
?>
```

```python
import requests
import json

req = requests.get("https://api.datadrum.com/json/ua_inf_annual.cpi", headers={"token": your_token})
print(json.loads(req.text))
```

```shell
curl "https://api.datadrum.com/json/ua_inf_annual.cpi"
  -H "token: your_token"
```

```javascript
var request = new Request("https://api.datadrum.com/json/ua_inf_annual.cpi", {
	method: 'GET',
	headers: new Headers({
		'token': your_token
	})
})

fetch(request)
	.then((response) => response.json())
	.then(function(json_response){
		console.log(json_response)
	});
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://api.datadrum.com/json/ua_inf_annual.cpi")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true

request = Net::HTTP::Get.new(url)
request['token'] = your_token

response = http.request(request)
puts response.read_body
```

> The above code would return the following JSON output:

```json
{
  "status":200,
  "error":null,
  "headers":
    [{
      "name":"ua_inf_annual.cpi",
      "territory":"Ukraine",
      "english":"CPI Annual ",
      "units":"%",
      "source":"Data Drum calculations based on State Statistics Service of Ukraine"
    }],
  "data":
    [
      {"date":"2006-01-31","ua_inf_annual___cpi":9.7251585623679},
      {"date":"2006-02-28","ua_inf_annual___cpi":10.691823899371},
      {"date":"2006-03-31","ua_inf_annual___cpi":8.659793814433},
      {"date":"2006-04-30","ua_inf_annual___cpi":7.5819672131148},
      ...
    ]
}
```

`GET https://api.datadrum.com/json/<INDICATOR>`

This endpoint returns all values held by Data Drum for a particular indicator, and is equivalent to:

`GET https://api.datadrum.com/json/<INDICATOR>/earliest/latest`

## Range of Values

```php
<?php
$curl = curl_init();
curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.datadrum.com/json/ua_inf_annual.cpi/2008-08-01/2008-12-01",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "GET",
  CURLOPT_HTTPHEADER => array(
    "token: ".your_token
  ),
));
$response = curl_exec($curl);
curl_close($curl);

$json_response = json_decode($response, true);
var_dump($json_response);
?>
```

```python
import requests
import json

req = requests.get("https://api.datadrum.com/json/ua_inf_annual.cpi/2008-08-01/2008-12-01", headers={"token": your_token})
print(json.loads(req.text))
```

```shell
curl "https://api.datadrum.com/json/ua_inf_annual.cpi/2008-08-01/2008-12-01"
  -H "token: your_token"
```

```javascript
var request = new Request("https://api.datadrum.com/json/ua_inf_annual.cpi/2008-08-01/2008-12-01", {
	method: 'GET',
	headers: new Headers({
		'token': your_token
	})
})

fetch(request)
	.then((response) => response.json())
	.then(function(json_response){
		console.log(json_response)
	});
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://api.datadrum.com/json/ua_inf_annual.cpi/2008-08-01/2008-12-01")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true

request = Net::HTTP::Get.new(url)
request['token'] = your_token

response = http.request(request)
puts response.read_body
```

> The above code would return the following JSON output:

```json
{
  "status":200,
  "error":null,
  "headers":
    [{
      "name":"ua_inf_annual.cpi",
      "territory":"Ukraine",
      "english":"CPI Annual Inflation",
      "units":"%",
      "source":"Data Drum calculations based on State Statistics Service of Ukraine"
    }],
  "data":
    [
      {"date":"2008-08-31","ua_inf_annual___cpi":25.986842105263},
      {"date":"2008-09-30","ua_inf_annual___cpi":24.63768115942},
      {"date":"2008-10-31","ua_inf_annual___cpi":23.317683881064},
      {"date":"2008-11-30","ua_inf_annual___cpi":22.17125382263}
    ]
}
```

`GET https://api.datadrum.com/json/<INDICATOR>/<DATE>/<DATE>`

This endpoint returns a range of values between the two dates in the format `YYYY-MM-DD` or `earliest` or `latest`.

Annual inflation in Ukraine hovered around 23.5% in the last months of 2008.

## Multiple Indicators

```php
<?php
$curl = curl_init();
curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.datadrum.com/json/ua_inf_annual.cpi,mx_cpi_headline_annual.val/2008-08-01/2008-12-01",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "GET",
  CURLOPT_HTTPHEADER => array(
    "token: ".your_token
  ),
));
$response = curl_exec($curl);
curl_close($curl);

$json_response = json_decode($response, true);
var_dump($json_response);
?>
```

```python
import requests
import json

req = requests.get("https://api.datadrum.com/json/ua_inf_annual.cpi,mx_cpi_headline_annual.val/2008-08-01/2008-12-01", headers={"token": your_token})
print(json.loads(req.text))
```

```shell
curl "https://api.datadrum.com/json/ua_inf_annual.cpi,mx_cpi_headline_annual.val/2008-08-01/2008-12-01"
  -H "token: your_token"
```

```javascript
var request = new Request("https://api.datadrum.com/json/ua_inf_annual.cpi,mx_cpi_headline_annual.val/2008-08-01/2008-12-01", {
	method: 'GET',
	headers: new Headers({
		'token': your_token
	})
})

fetch(request)
	.then((response) => response.json())
	.then(function(json_response){
		console.log(json_response)
	});
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://api.datadrum.com/json/ua_inf_annual.cpi,mx_cpi_headline_annual.val/2008-08-01/2008-12-01")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true

request = Net::HTTP::Get.new(url)
request['token'] = your_token

response = http.request(request)
puts response.read_body
```

> The above code would return the following JSON output:

```json
{
  "status":200,
  "error":null,
  "headers":
    [
      {
        "name":"mx_cpi_headline_annual.val",
		"territory":"Mexico",
        "english":"CPI Monthly Inflation (Headline)",
        "units":"%",
        "source":"Data Drum calculations based on Bank of Mexico"
      },
      {
        "name":"ua_inf_annual.cpi",
		"territory":"Ukraine",
        "english":"CPI Annual Inflation",
        "units":"%",
        "source":"Data Drum calculations based on State Statistics Service of Ukraine"
      }
    ],
  "data":
    [
      {"date":"2008-08-31","ua_inf_annual___cpi":25.986842105263,"mx_cpi_headline_annual___val":5.5729370355884},
      {"date":"2008-09-30","ua_inf_annual___cpi":24.63768115942,"mx_cpi_headline_annual___val":5.4734050723982},
      {"date":"2008-10-31","ua_inf_annual___cpi":23.317683881064,"mx_cpi_headline_annual___val":5.7799325124224},
      {"date":"2008-11-30","ua_inf_annual___cpi":22.17125382263,"mx_cpi_headline_annual___val":6.2328564459756}
    ]
}
```

`GET https://api.datadrum.com/json/<INDICATOR_1>,<INDICATOR_2>,.../`

This endpoint does everything above but for two (or more) indicators. You can keep going with many more as long as they're separated by commas.

The example on the right compared Ukraine's annual inflation with that in Mexico with the indicator `mx_cpi_headline_annual.val`

Annual inflation in Mexico was around five times lower than that in Ukraine towards the end of 2008.

# Available Indicators

## All/By Country

```php
<?php
$curl = curl_init();
curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.datadrum.com/json/all_indicators/ua,mx/",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "GET"
));
$response = curl_exec($curl);
curl_close($curl);

$json_response = json_decode($response, true);
var_dump($json_response);
?>
```

```python
import requests
import json

req = requests.get("https://api.datadrum.com/json/all_indicators/ua,mx/")
print(json.loads(req.text))
```

```shell
curl "https://api.datadrum.com/json/all_indicators/ua,mx/"
  -H "token: your_token"
```

```javascript
var request = new Request("https://api.datadrum.com/json/all_indicators/ua,mx/", {
	method: 'GET'
})

fetch(request)
	.then((response) => response.json())
	.then(function(json_response){
		console.log(json_response)
	});
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://api.datadrum.com/json/all_indicators/ua,mx/")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true

request = Net::HTTP::Get.new(url)

response = http.request(request)
puts response.read_body
```

> The above code would return the following JSON output:

```json
{
	"status": 200,
	"error": null,
	"headers": null,
	"data": [{
		"name": "mx_cpi_core.val",
		"territory":"Mexico",
		"english": "Consumer Price Index (Core)",
		"units": "Dec 2010 = 100",
		"source": "Bank of Mexico"
	}, {
		"name": "ua_fdi.monaco",
		"territory":"Ukraine",
		"english": "Foreign Direct Investment (Monaco)",
		"units": "million USD",
		"source": "State Statistics Service of Ukraine"
	}
    ...]
}
```

`GET https://api.datadrum.com/json/all_indicators/<COUNTRY_CODE_1>,<COUNTRY_CODE_2>,.../`

This endpoint returns all indicators available at Data Drum with the optional ability to limit by country, using <a href="https://en.wikipedia.org/wiki/ISO_3166-2">ISO 3166-2</a> two-letter country codes separated by commas.

## Search

```php
<?php
$curl = curl_init();
curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.datadrum.com/json/search/ukraine,inflation/",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "GET"
));
$response = curl_exec($curl);
curl_close($curl);

$json_response = json_decode($response, true);
var_dump($json_response);
?>
```

```python
import requests
import json

req = requests.get("https://api.datadrum.com/json/search/ukraine,inflation/")
print(json.loads(req.text))
```

```shell
curl "https://api.datadrum.com/json/search/ukraine,inflation/"
```

```javascript
var request = new Request("https://api.datadrum.com/json/search/ukraine,inflation/", {
	method: 'GET'
})

fetch(request)
	.then((response) => response.json())
	.then(function(json_response){
		console.log(json_response)
	});
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://api.datadrum.com/json/search/ukraine,inflation/")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true

request = Net::HTTP::Get.new(url)

response = http.request(request)
puts response.read_body
```

> The above code would return the following JSON output:

```json
{
	"status": 200,
	"error": null,
	"headers": null,
	"data": [{
		"name": "ua_inf_annual.cpi",
		"territory": "Ukraine",
		"english": "CPI Annual Inflation (Headline)",
		"units": "%",
		"decimals": 2,
		"source": "State Statistics Service of Ukraine"
	}, {
		"name": "ua_inf_annual.alc_tobacco",
		"territory": "Ukraine",
		"english": "CPI Annual Inflation (Alcohol, Tobacco)",
		"units": "%",
		"decimals": 2,
		"source": "State Statistics Service of Ukraine"
	}
    ...]
}
```

`GET https://api.datadrum.com/json/search/<SEARCH_TERM_1>,<SEARCH_TERM_2>,.../`

This endpoint searches all indicators that match the query, with search terms separated by commas.
