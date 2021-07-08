## Service-to-Service OAuth2 Auth Server

This sample supports OAuth2 Client Credentials Flow, relevant for service to service comm.

<br/>

### Usage

Create a credential:

```shell
$ curl http://localhost:9096/credentials
{"CLIENT_ID":"55899ac6","CLIENT_SECRET":"1e1cd8f5"}
$
```

Authenticate to get an access token:

```shell
$ curl http://localhost:9096/token\?grant_type\=client_credentials\&client_id\=73de4eb0\&client_secret\=ff44ccde
{
    "access_token":"eyJhbGciOiJIUzUxMiIsInR5cCI6IkpXVCJ9.eyJhdWQiOiI3M2RlNGViMCIsImV4cCI6MTYyNTc2MDE2NH0.bAsWHqwmmrk22BisWWkfDicQXnvLdkG7RVm5Y6ITWzC7fyz8fMFsYHnHwGnMWG66OyPaVgAVGLVLgzEEJtijEw",
    "expires_in":7200,
    "token_type":"Bearer"
}
$
```

<br/>
