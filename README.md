# Run AWS Lambda Function either locally or via API Gateway

https://github.com/coding-to-music/lamda-local-or-api-gateway

https://www.youtube.com/watch?v=AUQRyl1SNcU&ab_channel=BeABetterDev

https://github.com/beabetterdevv/lambda_local

## To run locally:

```java
sam local invoke -e ./lambda/lambda_event.json LambdaDemoFunction
```

## To run using API Gateway:

GET request in the query string parameters:

POST request in the body:

```java
sam local invoke -e ./apigateway/apigateway_event.json ApiGatewayFunction

sam local start-api
```

## To run using API Gateway locally with hot reload: (keeps docker running and reloads code)

```java
sam local start-api
```

Our template.yaml sets the routes

````java
Path: /hello

http://127.0.0.1:3000/hello

# Gives us:
{"message":"Internal server error"}

Because we did not return a 200 status code API Gateway will return a 500 status code.

```java
Lambda returned empty body!
Invalid lambda response received: Invalid API Gateway Response Keys: {'errorType', 'trace', 'errorMessage'} in {'errorType': 'TypeError', 'errorMessage': "Cannot read property 'foo' of null", 'trace': ["TypeError: Cannot read property 'foo' of null", '    at Runtime.exports.lambdaHandler [as handler] (/var/task/apigateway.js:2:40)', '    at Runtime.handleOnce (/var/runtime/Runtime.js:66:25)']}
2022-02-27 03:34:53 127.0.0.1 - - [27/Feb/2022 03:34:53] "GET /hello HTTP/1.1" 502 -
````
