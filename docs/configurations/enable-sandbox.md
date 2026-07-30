# Enable Sandbox

Developer Studio offers two ways to test services defined by OpenAPI specification in Developer Studio. One way is to connect Developer Studio to the tenant's own sandbox server. The other way to test an endpoint is to setup a mock server with Developer Studio. We use the [Stoplight Prism](https://meta.stoplight.io/docs/prism/ZG9jOjYx-overview) Mock server.

## Tenant Sandbox

Developer Studio can connect to a live tenant Sandbox server. The connection requirements depend on the authentication scheme used by the tenant.

### HMAC

To authenticate using the [HMAC](https://en.wikipedia.org/wiki/HMAC) authentication scheme, Developer Studio needs:

```
serverUrl: "https://base-url-to-be-pre-pended-to-an-endpoint"
authenticationScheme: "HMAC"
apiKey: "API key"
secret: "API key secret"
selfSignedCert: false
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
serverUrl: "https://base-url-to-be-pre-pended-to-an-endpoint"
authenticationScheme: "BASIC"
username: authentication username
password: authentication password
selfSignedCert: false
```

We will do the base64 encoding of the authorization token ('username:password'). When a sandbox request is sent from Developer Studio to the provided endpoint URL, the header will include `Authorization: Basic <encoded>username:password</encoded>`

### BEARER

In the case of the `BEARER` authentication scheme, Developer Studio needs:

```
serverUrl: "https://base-url-to-be-pre-pended-to-an-endpoint"
authenticationScheme: "BEARER"
password: BEARER_AUTH_TOKEN
selfSignedCert: false
```

The following headers are added to the API request sent to the sandbox server:
- **Timestamp**: timestamp of the creation of the HMAC signature
- **Client-Request-Id**: random UUID
- **Authorization: Bearer BEARER_AUTH_TOKEN**

If you want users to create their own API credentials instead of using the same API key and secret, users can now also generate their own API credentials on Dev Studio using 'Workspaces'. Please refer our documentation on [Enabling Workspaces](?path=docs/configurations/enable-workspaces.md).

To request an integration with your sandbox server, please create a [GitHub Issue](https://github.com/Fiserv/Support/issues)
 
## Mock Sandbox (Postman)

Developer Studio has integrated with Postman to provide a Mock Sandbox for running API requests within the API Explorer.

1. Provide examples of API requests and responses. The Postman mock server returns the response example in the API specification that matches the request example selected in the Developer Studio API Explorer. The request and response example names must be the same and unique. There can be multiple examples.

Below is a sample of how to add examples in your spec file and how examples gets mapped on Developer Studio UI.
![api example](assets/images/request-response-examples.png "api example")

2. Provide parameter examples. When Developer Studio invokes the Postman Mock Server, it replaces parameters in the API path with appropriate values. The parameter values used by Developer Studio must match the values expected by the Postman Mock Server. Explicitly providing example parameter values in the API specification avoids a potential mismatch between values sent by Developer Studio and those expected by the Postman Mock Server. 
There are two methods for providing example values. One is to use the `example` keyword, the other is to use the `default` keyword. Below are examples of both methods.

![parameter example](assets/images/parameter-example.png "parameter example")
![parameter default](assets/images/default-parameter-example.png "parameter default")

3. We encourage you to load the openAPI spec into the [Swagger Editor](https://editor.swagger.io/) before pushing the changes to GitHub.

4. To enable the Run Button, `product.feature - sandBox` has to be set in **config/tenant.json** file:

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
