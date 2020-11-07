### Sending Form Data
When a form is submitted, where does the data go and how is it handled?

#### Client / Server Architecture
- client sends request to a server
- server answers the request
- HTTP form is a user-friendly way to configure a request to send data to a server

#### Sending the data
- `<form action="https.ex.com">` the `action` attribute defines where the data gets sent and if an attribute is not set, data is sent to the URL of the form page
- `name=value` are sent to the server as pairs joined with ampersands (&)
- `method` attribute defines how the data is sent (get / post)
- data is appended to the URL as a series of name/value pairs unless input is hidden (post instead of get)

#### POST method
- the method used by the browser to talk to the server
- asks for an appropriate response when providing data in the HTTP request

#### Viewing HTTP requests
1. Open the developer tools.
2. Select "Network"
3. Select "All"
4. Select "foo.com" (example) in the "Name" tab
5. Select "Headers"

#### Server side - retrieving data
- server receives a parsed string in order to get key/value pairs
- different languages and frameworks can be used to retrieve data

#### Sending data
- HTTP is a text protocol so handling binary data needs to be handled differently
- method attribute should be POST if the file content can't be put inside a URL
```
<form method="post" action="https://www.foo.com" enctype="multipart/form-data">
  <div>
    <label for="file">Choose a file</label>
    <input type="file" id="file" name="myFile">
  </div>
  <div>
    <button>Send the file</button>
  </div>
</form>
```
#### Security
- Always consider security when sending data (problems arise from how the server handles data)
- NEVER TRUST YOUR USERS
- NEVER TRUST YOURSELF
- limit the amount of incoming data to what's only necessary
- store data on different servers / domains

#### Additional Resources
[HTML5 Forms Reference](https://htmlreference.io/forms/)  
[Styling HTML5 Forms](https://www.youtube.com/playlist?list=PL4cUxeGkcC9g5_p_BVUGWykHfqx6bb7qK)  
