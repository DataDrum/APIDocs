---
title: Data Drum API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - php
  - python
  - javascript

toc_footers:
  - <a href='/api/'>Get an API Key!</a>
  - <a href='mailto:info@datadrum.com'>Support</a>
  - <a href="/">Back to Data Drum</a>

includes:
  - errors

search: false
---

# Introduction

Welcome to Data Drum's elegant and easy-to-use API!

It's really simple to get going. All you need is an API Key and the ability to send that key in the headers of a GET request to:

`https://api.datadrum.com/...`

You can get access to any indicator you like by changing that API endpoint. A list of indicators is available within the Data Drum platform.

For example, Ukraine annual inflation:

`ua_inf_annual.cpi`

Let's get started! Scroll down to see how you can access any indicator and look to the right for examples in various languages which give you Ukraine's annual inflation rate.

# Basic Data Retrieval

## Latest Value

```php
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

> The above command returns JSON structured like this:

```json
{
	"status": 200,
	"error": null,
	"headers": [{
		"name": "ua_inf_annual.cpi",
		"english": "CPI Annual Inflation",
		"units": "%",
		"source": "State Statistics Service of Ukraine"
	}],
	"data": [{
		"date": "2018-07-31",
		"ua_inf_annual___cpi": 8.8996054362122
	}]
}
```

`GET https://api.datadrum.com/json/<INDICATOR>/latest`

This endpoint retrieves the latest value held by Data Drum for a particular indicator.

## Earliest Value

```php
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

> The above command returns JSON structured like this:

```json
{
  "status":200,
  "error":null,
  "headers":[],
  "data":
    [
      {"date":"1913-01-01","us_inf_annual___cpi_SA":0}
    ]
}
```

`GET https://api.datadrum.com/json/<INDICATOR>/earliest`

This endpoint retrieves the earliest value held by Data Drum.

## All Values

```php
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

> The above command returns JSON structured like this:

```json
{"status": 200,
 "error": "None",
 "headers": [],
 "data":
  [
    {"date": "1913-01-01", "us_inf_annual___cpi_SA": 0},
    {"date": "1913-02-01", "us_inf_annual___cpi_SA": 0},
    {"date": "1913-03-01", "us_inf_annual___cpi_SA": 0},
    {"date": "1913-04-01", "us_inf_annual___cpi_SA": 0}
  ]
}
```

`GET https://api.datadrum.com/json/<INDICATOR>`

This endpoint retrieves all values held by Data Drum for a particular indicator, and is equivalent, as you'll see later, to:

`GET https://api.datadrum.com/json/<INDICATOR>/earliest/latest`

## Specific Date

```php
$curl = curl_init();
curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.datadrum.com/json/ua_inf_annual.cpi/1967-09-01",
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
```

```python
import requests
import json

req = requests.get("https://api.datadrum.com/json/ua_inf_annual.cpi/1967-09-01", headers={"token": your_token})
print(json.loads(req.text))
```

```shell
curl "https://api.datadrum.com/json/ua_inf_annual.cpi/1967-09-01"
  -H "token: your_token"
```

```javascript
var request = new Request("https://api.datadrum.com/json/ua_inf_annual.cpi/1967-09-01", {
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

> The above command returns JSON structured like this:

```json
{
  "status":200,
  "error":null,
  "headers":[],
  "data":
    [
      {"date":"1967-09-01","us_inf_annual___cpi_SA":2.9096477794793}
    ]
}
```

`GET https://api.datadrum.com/json/<INDICATOR>/<DATE>`

This endpoint retried the value on an indicator on a specific date, which must be in the format `YYYY-MM-DD` or `earliest` or `latest`, which return the earliest or latest value held by Data Drum respectively.

If no value is held for the date you specify, the date with a value previous to the date you specify is chosen.

## Range of Values

```php
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

> The above command returns JSON structured like this:

```json
{
  "status":200,
  "error":null,
  "headers":[],
  "data":
    [
      {"date":"2008-08-01","us_inf_annual___cpi_SA":5.3404815922699},
      {"date":"2008-09-01","us_inf_annual___cpi_SA":5.398065171645},
      {"date":"2008-10-01","us_inf_annual___cpi_SA":4.0508854119215},
      {"date":"2008-11-01","us_inf_annual___cpi_SA":1.8944500215115},
      {"date":"2008-12-01","us_inf_annual___cpi_SA":0.26750903554455}
    ]
}
```

`GET https://api.datadrum.com/json/<INDICATOR>/<DATE>/<DATE>`

This endpoint retrieves a range of values between the two dates in the format `YYYY-MM-DD` or `earliest` or `latest`.

# Multiple Indicators

`GET https://api.datadrum.com/json/<INDICATOR_1>,<INDICATOR_2>,.../`

This endpoint does everything above but for two indicators — and you can keep going with many more as long as they're separated by commas.

# Response Formats

`GET https://api.datadrum.com/<FORMAT>/...`

You can get your output in any of the following formats by putting that value in the endpoint as above.

`json`
`csv`
`xml`
`xlsx`