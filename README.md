# Run AWS Lambda Function either locally or via API Gateway

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
