# [What Google Learned From Its Quest to Build the Perfect Team](https://www.nytimes.com/2016/02/28/magazine/what-google-learned-from-its-quest-to-build-the-perfect-team.html)  

> ‘‘employee performance optimization’’ — isn’t enough

- communication and limited micro-managing is critical
- distinguishment  between good team and dysfunctional teams all boils down to how teammates treat each other
- good team qualities: talking time distribution ("conversational turn-taking") & social sensitivity ("empathy") —> psychological safety

# [A conversation about REST with my brother](https://gist.github.com/brookr/5977550)  

## HTTP
- tells the browser what protocol to use
- capable of describing the location of something
- foundation of the web

## REST
- architechural style that the www is built on
- provides a definition of a resource (web page is a representation of a resource)
- redirect: having one machine tell another machine about a resource that might be on another machine
- URL - connects every programming language/database/etc.

# [SuperAgent](https://visionmedia.github.io/superagent/)  
- light-weight progressive ajax API
- flexibility, readability, and low learning curve
- works with Node

### Request basics
- invoke method on `request` object
- call `.then()` (or `.end()` or `await` to send the request

### Setting header fields
- invoke `.set()` with a field name and value

### GET requests
- `.query()` method accepts objects, which when used with the GET method will form a query-string

### HEAD requests
- use the `.query()` method

### POST / PUT requests
- set the Content-Type header field appropriately and "write" some data

### Setting the Content-Type
- `.set()` method

### Serializing request body
- `request.serialize`

### Retrying requests
- `.retry()` method
- two optional arguments: number of retries (default 1) and a callback. It calls `callback(err, res)` before each retry. The callback may return true/false to control whether the request should be retried (but the maximum number of retries is always applied)

### Setting Accept
- `.accept()` references `request.types` as well allowing you to specify either the full canonicalized MIME type name as `type/subtype`, or the extension suffix form as "xml", "json", "png", etc.

### Query strings
- `req.query(obj)`

# API Keys
- [Geocoding API Docs](https://locationiq.com/)  
- [Weather Bit API Docs](https://www.weatherbit.io/)  
- [Yelp API Docs](https://www.yelp.com/developers/documentation/v3/business_search)  
- [The Movie DB API Docs](https://developers.themoviedb.org/3/getting-started/introduction)  
- [The Hiking Project API Docs](https://www.hikingproject.com/data)  