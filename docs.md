# Documentation

## Methods

### URL/URI parameters
Various methods have been added for getting URI parameters from requests.

* `string GetURLQueryParam(string name, Encoding encoding = null)`
* `string GetURLQueryString(Encoding encoding = null)`
* `Dictionary<string, string> GetURLQueryParamDict()`

These methods could be useful at some point, I suppose.

#### GetURLQueryParam()
`GetURLQueryParam()` returns a query parameter from the URL.

```csharp

// Original URL: https://myshitty.website/myterriblepage.html?stupidparam=horriblevalue

string value = GetURLQueryParam("stupidparam");

// value is now "horriblevalue"

```

#### GetURLQueryString()
`GetURLQueryString()` returns the whole query string from the URL.

```csharp

// Original URL: https://alcoholicsanonymous.org/relapse.html?user=JohnDoe42069

string param = GetURLQueryString();

// param is now "user=JohnDoe42069"

```

#### GetURLQueryParamDict()
This method returns a dictionary containing all the keys and values in the URL.

```
Original URL: https://raisins.com/purchase.html?product=50lbbarrelofraisins&quantity=37

Dictionary:

Key = Value
---

product  = 50lbbarrelofraisins
quantity = 37

```