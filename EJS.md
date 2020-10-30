[Watch EJS tutorial from WalkThroughCode on YouTube, Videos 1-5](https://www.youtube.com/playlist?list=PL7sCSgsRZ-slYARh3YJIqPGZqtGVqZRGt)  

#### Intro to EJS

-evaluate injected variable inside a route 

-iterate/loop over an array of values 

-if/else statements 

-layouts 

-partials 

### Setup

- npm init -y
- npm install --save express body-parser cors ejs

```jsx
var express = require('express');
var bodyParser = require('body-parser');
var cors = require('cors');
var path = require('path');

// create instance of express app (instantiate server)
var app = express();

// configure app and call it to run everything through bodyParser & cors
app.use(bodyParser());
app.use(cors());

// set views directory
// path is core module for node - takes 2 paths and joins them
// concatenate current working directory in a folder called views
app.set('views', path.join(_dirname, 'views'));
app.set('view engine', 'ejs');

// route for root directory
app.get('/', function(request, response) {
	// takes name of the file and not the file path
	// response.render takes 3 parameters: view, object, callback
	response.render('index', {
		foo: 'bar'
	});
});

// server needs to listen!
app.listen(8000, function() {
	console.log("heard on 8000);
}
```

- create a folder called views → create file inside called index.ejs

```jsx
// index.ejs file
// ejs opening <% and closing %> signs
// = sign is assigning a variable
<h1>Hello <%= foo %></h1>
<img src="<%= foo %>" alt="">
```

### Iterate through array

```jsx
app.get('/', function(request, response) {
	response.render('index', {
		people: [
			{ name: 'dave' },
			{ name: 'jerry' }
		]
	});
});
```

```jsx
// index.ejs file
<ul>
	<% for(var person of people) { %>
	<li><%= person.name %></li>
	<% } %>
</ul>
```

### If/Else statement

```jsx
// index.ejs file
<ul>
	<% for(var person of people) { %>
		<% if(person.name === 'dave') { %>
		<li>This is definitely <%= person.name %>!!!</li>
		<% } else { %>
			<li>This is not dave! This is <%= person.name %>!!!</li>
		<% } %>
	<% } %>
</ul>
```

## Additional Resources

Reference: [Google Books API Docs](https://developers.google.com/books/docs/v1/using#WorkingVolumes)  

Reference: [EJS Docs](http://ejs.co/)  

- Skim: [EJS Tutorial](https://scotch.io/tutorials/use-ejs-to-template-your-node-application)  
- Skim: [Source Code for the EJS Tutorial](https://github.com/scotch-io/node-ejs)  