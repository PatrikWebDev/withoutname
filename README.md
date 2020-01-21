<h1> POST és GET közötti különbség</h1>
<p>GET is used to request data from a specified resource. </p>
GET is one of the most common HTTP methods.<br>
<ul>
<li>GET requests can be cached</li>
<li>GET requests remain in the browser history</li>
<li>GET requests can be bookmarked</li>
<li>GET requests should never be used when dealing with sensitive data</li>
<li>GET requests have length restrictions</li>
<li>GET requests are only used to request data (not modify)/li>
</ul>


<p>POST is used to send data to a server to create/update a resource. </p>
<ul>
<li>POST requests are never cached</li>
<li>POST requests do not remain in the browser history</li>
<li>POST requests cannot be bookmarked</li>
<li>POST requests have no restrictions on data length</li>
</ul>
</p>

<h1>Mire jó az express</h1>
<p>
Express.js is a modular web framework for Node.js.<br>
It is used for easier creation of web applications and services.<br>
Express.js simplifies development and makes it easier to write secure, modular and fast applications.<br>

Rövid bemutató az express js használatáról:
[Youtube video](https://www.youtube.com/watch?v=L72fhGm1tfE&t=2006s)
</p>

<h1>Mi a middleware + példa </h1>
<p>
Middleware functions are functions that have access to the request object (req),<br>
the response object (res), and the next middleware function in the application’s request-response cycle.<br>
The next middleware function is commonly denoted by a variable named next.<br>

Példák ezen az oldalon: https://medium.com/@selvaganesh93/how-node-js-middleware-works-d8e02a936113<br>
Middlewares: [Youtube video 1](https://www.youtube.com/watch?v=-lRgL9kj_h0&feature=youtu.be) | [Youtube video 2](https://www.youtube.com/watch?v=aPxKObvx9II&list=PLBAZWBMYeVYhZ_7V_dHNECjVCeBHVkqSo&index=13&t=0s)
</p>

<h1>Mi a query string és mi a parameter, 1-1 pelda </h1>
<p>
Query String = On the World Wide Web, a query string is the part of a uniform resource locator (URL) <br>
which assigns values to specified parameters. The query string commonly includes fields added to a base URL<br> 
by a Web browser or other client application, for example as part of an HTML form<br>
példa= "https://example.com/?foo=bar&foo2=bar2"; <br>
  
Parameter: <br>
Route parameters are named URL segments that are used to capture the values specified at their position in the URL. <br>
The captured values are populated in the req.params object,<br> with the name of the route parameter specified in the path as their respective keys.<br>

```
Route path: /users/:userId/books/:bookId
Request URL: http://localhost:3000/users/34/books/8989
req.params: { "userId": "34", "bookId": "8989" }
```

Query string: [Youtube video](https://www.youtube.com/watch?v=QTAYRmMsVCI)
</p>

<h1>Hogyan lesz elérhető a req.body </h1>
<p>
router.post('/addUser', userController.addNewUser); <br>
 addNewUser(req, res) {<br>
	        const data = req.body;<br>
	        users.push(data.username);<br>
	        res.status(204).send('ok');<br>
	    }<br>

Ahhoz hogy a fenti példában a data változó értéke ne undefined legyen és ténylegesen elérjük magát a request body-t használnunk kell az express két middleware függvényét.<br>

Azaz fel kell vennünk a programunkban az alábbi két utasítást:<br>
  app.use(express.json());<br>
  app.use(express.urlencoded({extended: false}));

  Összegezve

  ```js
const app = require('express')()

// without these the body will be undefined
app.use(express.json()) // for parsing application/json
app.use(express.urlencoded({ extended: true })) // for parsing application/x-www-form-urlencoded

app.post('/profile', function (req, res, next) {
  console.log(req.body)
  res.json(req.body)
})
  ```
</p>
<h1>Mi a controller</h1>
<p>
The brains of the application. The controller decides what the user's input was, <br>
how the model needs to change as a result of that input, and which resulting view should be used. <br>
  
egy másik definíció : A controller is a program component that serves as a mediator between a user and application <br>
and handles business-related tasks triggered in ASP.NET pages. <br>
A controller is used for scripting exposed and middle-tier endpoints for expected user actions and results. <br>
</p>

<h1>Mi a request, response </h1>
<p>
request = A HTTP request is a text string generated by the client and<br>
sent to the server containing the specifications of the resource the client is asking for.<br>
A resource is anything that can accessed via the web. The HTTP request communicates which resource a client wants to interact with<br>
and how the client wants to interact with it, along with some metadata held in the header related to the request.<br>

response = An HTTP response is what is sent by a server to a client in response to an HTTP request.<br>
These responses contain a status code and if the request was successful, the requested resource.<br>
An example status code for a successful request would be “200” and <br>
an example status code for an unsuccessful request would be “404”. <br>
Other common status codes include “300” for redirects and “500” for server errors.<br>

HTTP request/response/status codes: [Youtube video](https://www.youtube.com/watch?v=iYM2zFP3Zn0&t=1628s)
</p>

<h1>Mi egy route, példa egy létrehozására</h1>
<p>
routing: elfogadott HTTP path info minták és ("útvonalak", "routes") HTTP methodok és<br>
az útvonalak megnyitását/meghívását lekezelő függvények összekapcsolása<br>
figyelem: HTTP method != metódus JSben!<br>
/hello esetén az (1) anonim függvény fog lefutni<br>
a /hello az egyetlen meghívható útvonal<br>
router: a leképezést végző komponense<br>
adott egy default router<br>
testreszabható egyedi routerek (csak megemlítés szintjén)<br>
egymásba ágyazott, összetett routerek (csak említés szintjén)<br>
endpoint<br>
(ez a rész az órai index.md van másolva)<br>
példák: https://github.com/szcsl/bh-fst01/blob/master/docs/lectures/20200118/helloWorld/index.js <br>
</p>






