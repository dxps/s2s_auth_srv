## Service-to-Service OAuth2 Auth Server

This sample supports OAuth2 Client Credentials Flow, relevant for service to service comm.

<br/>

### Usage

Create/get a set of credentials:

```shell
$ curl http://localhost:9096/credentials
{"CLIENT_ID":"da374969","CLIENT_SECRET":"a71ba2f0"}
$
```

Authenticate to get an access token:

```shell
$ curl 'http://localhost:9096/token?grant_type=client_credentials&client_id=da374969&client_secret=a71ba2f0'
{
    "access_token":"eyJhbGciOiJIUzUxMiIsInR5cCI6IkpXVCJ9.eyJhdWQiOiI3M2RlNGViMCIsImV4cCI6MTYyNTc2MDE2NH0.bAsWHqwmmrk22BisWWkfDicQXnvLdkG7RVm5Y6ITWzC7fyz8fMFsYHnHwGnMWG66OyPaVgAVGLVLgzEEJtijEw",
    "expires_in":7200,
    "token_type":"Bearer"
}
$
```

According to OAuth2 spec ([section 2.3.1](https://datatracker.ietf.org/doc/html/rfc6749#section-2.3.1)), this is actually not recommended:

> Including the client credentials in the request-body using the two
> parameters is NOT RECOMMENDED and SHOULD be limited to clients unable
> to directly utilize the HTTP Basic authentication scheme (or other
> password-based HTTP authentication schemes).

And considering [section 4.4](https://datatracker.ietf.org/doc/html/rfc6749#section-4.4), the request and response should look as follows. There is no statement saying that request should not include additional params in the body.

- Request:

  ```
  POST /token HTTP/1.1
  Host: server.example.com
  Authorization: Basic czZCaGRSa3F0MzpnWDFmQmF0M2JW
  Content-Type: application/x-www-form-urlencoded

  grant_type=client_credentials
  ```

- Response:

  ```
  HTTP/1.1 200 OK
  Content-Type: application/json;charset=UTF-8
  Cache-Control: no-store
  Pragma: no-cache

  {
    "access_token":"2YotnFZFEjr1zCsicMWpAA",
    "token_type":"example",
    "expires_in":3600,
    "example_parameter":"example_value"
  }
  ```

<br/>
