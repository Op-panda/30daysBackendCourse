# 30daysBackendCourse
30 days of learning in single md file

## Day 1
- Efficient storage and delivery of info
- customised user experience 
- controlled access to content
- Notifications and communication

### Server function types
- software(HTTP)
- Hardware(Harddisk, database)

### Imp notes-
- Browser request for info and server serves the browser by sending a response.
- DNS (Domain Name System) is a server that is responsible for mapping in domain name and the ip address.
- HTTP (HyperText Transfer Protocol is a set of communication rules between client & Server).

## Day 2

### create a node server
```
const http = require('http');
const server = http.createServer((req, res)) = {        
console.log('Request from browser to server');

//REQUEST
//console.log(req.method())
//req.method -> GET, POST, etc.
//req.url -> url from which req has been made 

// RESPONSE
//res.setHeader('Content-Type', 'text/plain');
//res.write('Hello world :)');
//res.end();
};

//server listening on specific port
server.listen(3000, 'localhost', ()={
console.log('server is listening on port 3000');});
``` 
## day 3

suppose your folder structure looks like this, 
#### Views(Folder)
- 404.html
- about.html
- index.html

#### To read file and display content on browser,
```
fs.readFile('./views/index.html', (err, fileData)=>{
if(err){
console.log(err);
}
else{
res.write(fileData);
res.end();}

//we can also write, res.end(fileData);
```
#### Q. Lets take an example where, request url is to be fetched and displayed as a resdponse on browser.
Let path = './views';
```
switch(req.url){
case '/':
path+= '/index.html';
break;
case '/about':
path+= '/about.html';
break;

default:
path+= '/404.html';
}

fs.readFile(path, (err, fileData)=>{
if(err){
console.log(err);
}
else{
res.end(fileData);
}})
```
### Status codes 
- Each response has its associated status code.
- response comes with HTTP header which contains status code.

#### Benefit
- Debugging 
- SEO

#### Codes
- 100 to 199   -> Informational Purpose 
- 200 to 299   -> success
- 300 to 399   -> redirect
- 400 to 499   -> client error 
- 500 to 599   -> server error (crash, server down)

#### Most used codes are: 
- 200, 201, 307, 308, 400, 404, 500, 502 

#### Implementing status code in server 
```
Switch(req.url){
case '/about':
path += '/about.html'
res.StatusCode = 200;
break;
}
```

#### How to redirect to another route
```
case '/about-me':
res.StatusCode=301;
res.setHeader('Location', '/about');
res.end();
break;
```
