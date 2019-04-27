## AWS Serverless Micro

Run [Micro](https://github.com/zeit/micro/) functions on AWS Lambda. A very thin
layer for Micro functions that does two things:

-   Reshape an API Gateway `event` object to [`http.IncomingMessage`](https://nodejs.org/api/http.html#http_class_http_incomingmessage)
-   Marshall the returned [`http.ServerResponse`](https://nodejs.org/api/http.html#http_class_http_serverresponse) to a Lambda Proxy object.

Inspired by [awslabs/aws-serverless-express](https://github.com/awslabs/aws-serverless-express/).

_With **Micro**:_

```js
// The Micro function
$ cat my-api.js
module.exports = async () => 'Welcome to Micro'

// Running with `micro`
$ micro my-api.js
micro: Accepting connections on port 3000
```

_With **aws-serverless-micro**:_

```js
// The Micro function
$ cat my-api.js
module.exports = async () => 'Welcome to Micro'

// Wrapped in `aws-serverless-micro`
$ cat lambda.js
module.exports = {
    handler: require('aws-serverless-micro')(require('./my-api')),
}

// Deploy `lambda.handler` with the tool of your choice
```

### Compatability

This libary is **100% compatible** with the Micro API. The full Micro test suite
is run against the library.

-   [x] micro.send
-   [x] micro.sendError
-   [x] micro.createError
-   [x] micro.buffer
-   [x] micro.text
-   [x] micro.json

### License

MIT