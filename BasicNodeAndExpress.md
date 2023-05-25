// Importing required modules
let express = require('express'); // Importing the 'express' module
let app = express(); // Creating an instance of the Express application
let bodyParser = require('body-parser'); // Importing the 'body-parser' module

app.use(bodyParser.urlencoded({extended: false}));
// Configuring body-parser middleware to parse URL-encoded request bodies

app.post('/name', function(req, res) {
  // Handling POST requests to '/name' endpoint
  res.json({'name': req.body.first + " " + req.body.last});
  // Sending a JSON response containing the 'first' and 'last' properties from the request body
});

app.get('/name', function(req, res) {
  // Handling GET requests to '/name' endpoint
  res.json({'name': req.query.first + " " + req.query.last});
  // Sending a JSON response containing the 'first' and 'last' properties from the query parameters
});

app.get('/:word/echo', function(req, res) {
  // Handling GET requests to '/:word/echo' endpoint
  res.json({'echo': req.params.word});
  // Sending a JSON response containing the captured word from the URL parameter
});

app.use(function(req, res, next) {
  // Middleware that logs the request method, path, and IP address
  console.log(req.method + " " + req.path + " - " + req.ip);
  next(); // Calling 'next()' to pass control to the next middleware/route handler
});

app.get('/now', function(req, res, next) {
  // Handling GET requests to '/now' endpoint
  req.time = new Date().toString(); // Adding a 'time' property to the request object
  next(); // Calling 'next()' to pass control to the next middleware/route handler
}, function(req, res) {
  // Second middleware function in the '/now' endpoint
  res.json({'time': req.time}); // Sending a JSON response containing the 'time' property from the request object
});

app.get('/', function(req, res) {
  // Handling GET requests to the root endpoint '/'
  res.sendFile(__dirname + '/views/index.html');
  // Sending the 'index.html' file located in the 'views' directory
});

app.use('/public', express.static(__dirname + '/public'));
// Serving static files from the 'public' directory when the '/public' URL prefix is matched

app.get('/json', function(req, res) {
  // Handling GET requests to '/json' endpoint
  const mySecret = process.env['MESSAGE_STYLE'];

  if (mySecret === 'uppercase') {
    res.json({'message': 'HELLO JSON'});
    // Sending a JSON response with 'message' as 'HELLO JSON' when the 'MESSAGE_STYLE' environment variable is set to 'uppercase'
  } else {
    res.json({'message': 'Hello json'});
    // Sending a JSON response with 'message' as 'Hello json' for other cases
  }
});

console.log('Hello World'); // Logging a message to the console

module.exports = app; // Exporting the Express application for use in other modules
