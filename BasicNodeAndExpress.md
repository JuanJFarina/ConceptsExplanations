let express = require('express');
let app = express();
let bodyParser = require('body-parser');

app.use(bodyParser.urlencoded({extended: false}));

app.post('/name', function(req, res) {
  res.json({'name': req.body.first + " " + req.body.last});
});

app.get('/name', function(req, res) {
  res.json({'name': req.query.first + " " + req.query.last});
});

app.get('/:word/echo', function(req, res) {
  res.json({'echo': req.params.word});
});

app.use(function(req, res, next) {
  console.log(req.method + " " + req.path + " - " + req.ip);
  next();
});

app.get('/now', function(req, res, next) {
  req.time = new Date().toString();
  next();
}, function(req, res) {
  res.json({'time': req.time});
});

app.get('/', function(req, res) {
  res.sendFile(__dirname + '/views/index.html');
});

app.use('/public', express.static(__dirname + '/public'));

app.get('/json', function(req, res) {
  const mySecret = process.env['MESSAGE_STYLE'];

  if(mySecret === 'uppercase') {
    res.json({'message':'HELLO JSON'});
  }
  else {
    res.json({'message':'Hello json'});
  }
});

console.log('Hello World');

module.exports = app;
