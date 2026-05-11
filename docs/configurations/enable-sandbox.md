# Enable Sandbox

Developer Studio offers two ways to test services defined by OpenAPI specification in Developer Studio. One way is to connect Developer Studio to the tenant's own sandbox server. The other way to test an endpoint is to setup a mock server with Developer Studio. We use the [Stoplight Prism](https://meta.stoplight.io/docs/prism/ZG9jOjYx-overview) Mock server.

## Tenant Sandbox

Developer Studio can connect to a live tenant Sandbox server. The connection requirements depend on the authentication scheme used by the tenant.

### HMAC

To authenticate using the [HMAC](https://en.wikipedia.org/wiki/HMAC) authentication scheme, Developer Studio needs:

```
serverUrl:"https://base-url-to-be-pre-pended-to-an-endpoint"
authenticationScheme:"HMAC"
apiKey:"2MWVAWF2xZz0eNQUK0NVhwpWYkr7gehG"
secret:"some secret"
selfSignedCert:false
```

Developer Studio creates an HMAC signature as follows:

```
apiKey + clientRequestId + timestamp + request body string
```

The hash of this data is created by using the SHA256 hashing function with the Tenant's secret as the hash key.
The base64, string representation of the hash is the HMAC signature.
The following headers are added to the API request sent to the sandbox server:
- **Api-Key**: API Key provided by tenant
- **Timestamp**: timestamp of the creation of the HMAC signature
- **Client-Request-Id**: random UUID
- **Auth-Token-Type**: "HMAC"
- **Authorization**: HMAC signature

### HMAC512
SHA512-based HMAC authentication is the same as `HMAC` except that it uses SHA512 as the hashing function.

### BASIC

In the case of the [BASIC](https://swagger.io/docs/specification/v3_0/authentication/basic-authentication/) authentication scheme, Developer Studio needs:

```
serverUrl:"https://base-url-to-be-pre-pended-to-an-endpoint"
authenticationScheme:"BASIC"
username:"username"
password:"password"
selfSignedCert: false
```

We will do the base64 encoding of the authorization token ('username:password'). When a sandbox request is sent from Developer Studio to the provided endpoint URL, the header will include `Authorization: Basic <encoded>username:password</encoded>`

### BEARER

In the case of the `BEARER` authentication scheme, Developer Studio needs:

```
serverUrl:"https://base-url-to-be-pre-pended-to-an-endpoint"
authenticationScheme:"BEARER"
password:"password"
selfSignedCert: false
```

The following headers are added to the API request sent to the sandbox server:
- **Timestamp**: timestamp of the creation of the HMAC signature
- **Client-Request-Id**: random UUID
- **Authorization: Bearer `password`**

If you want users to create their own API credentials instead of using the same API key and secret, users can now also generate their own API credentials on Dev Studio using 'Workspaces'. Please refer our documentation on [Enabling Workspaces](?path=docs/configurations/enable-workspaces.md).

To request an integration with your sandbox server, please create a [GitHub Issue](https://github.com/Fiserv/Support/issues)
 
## Stoplight Prism Mock Server

There are couple of steps to follow for the prism mock server to work.

1. Add example request and response in your openapi spec file so that prism **mock** server can validate your request payload and then return the correct **mock** response depending on that example. Example name in request & response must be the same and unique. There could be multiple examples.

Below is a sample of how to add examples in your spec file and how examples gets mapped on Developer Studio UI.

![api example](assets/images/api-example.png "api example")

2. To install and run Stoplight Prism locally refere to the following command

`npm install --registry=https://nexus.onefiserv.net/repository/npm-registry @stoplight/prism-cli`

3. We encourage you to test the openAPI spec in [Swagger Editor](https://editor.swagger.io/) and locally, before pushing the changes to GitHub

`npx prism mock <your yaml file name>`

4. Once prism has started, all the endpoints will be listed from the yaml file provided. Postman could be used to send a request and receive a response in order to validate your API spec contains all the information prism needs to return a mock response. 

When sending a POST request, the body of the request should be copied from the request body example on the API Explorer `Run Request` page. Sample `Run Request` body:

![example 'Run Request' body](assets/images/example-run-request-body.png)

To specify a prefered example for a particular endpoint use **Prefer** header with value `example=EndPointSample`

![start prism locally](assets/images/prism-postman-run.png)

4. Finally once you are done updating the spec files please let us know we would need to setup up an actual mock server.
5. To enable the Run Button, `product.feature - sandBox` has to be set in **config/tenant.json** file:

    ```
          "feature":[
            {
              "name": "sandBox",
              "value": true
            },
            ...
          ]
    ```
6. To dictate whether you want to allow the user to change the parameters to be sent in the request,  `editParameterAPIExplorer` has to be set in **config/tenant.json - product.feature**:

    ```
          "feature":[
            {
              "name": "editParameterAPIExplorer",
              "value": true
            },
            ...
          ]
    ```
7. To enable/disable our automatic OpenAPI and postman collection generation + download buttons,  `downloadPostman` can to be set in **config/tenant.json - product.feature**:

    ```
          "feature":[
            {
              "name": "downloadPostman",
              "value": true
            },
            ...
          ]
    ```

![tenant sandbox config](assets/images/tenant-sandbox-config.png "tenant sandbox options")
