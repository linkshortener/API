## API
In addition to the website, you can use these APIs to create, delete and get URLs.

### Types

```
URL {
  createdAt {string} ISO timestamp of when the URL was created
  id {string} Unique ID of the URL
  target {string} Where the URL will redirect to
  password {boolean} Whether or not a password is required
  count {number} The amount of visits to this URL
  shortUrl {string} The shortened link 
}
```

In order to use these APIs you need to generate an API key from settings. Never put this key in the client side of your app or anywhere that is exposed to others.

All API requests and responses are in JSON format.

Include the API key as `X-API-Key` in the header of all below requests. Available API endpoints with body parameters:

**Get shortened URLs list:**
```
GET /api/url/geturls
```

Returns:
```
{
  list {Array<URL>} List of URL objects
  countAll {number} Amount of items in the list
}
```

**Submit a link to be shortened**:
```
POST /api/url/submit
```
Body:
  * `target`: Original long URL to be shortened.
  * `customurl` (optional): Set a custom URL.
  * `password` (optional): Set a password.
  * `reuse` (optional): If a URL with the specified target exists returns it, otherwise will send a new shortened URL.

Returns: URL object

**Delete a shortened URL** and **Get stats for a shortened URL:**
```
POST /api/url/deleteurl
GET /api/url/stats
```
Body (or query for GET request)
  * `id`: ID of the shortened URL.
  * `domain` (optional):  Required if a custom domain is used for short URL.
