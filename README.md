# Auth0 Nginx Plus Proxy Example
This exmaple involves using OIDC/OAuth2 to log in against the Nginx Plus that protects a App that is not able to provide OIDC/OAuth2 Standard support - the downstream app only understands Basic HTTP Authorization Headers.
To supply the App with Authorization Headers the Nginx will do the Login Flow against Auth0. After the User succesfully Logged in the Header will be set at the Nginx and the Proxy will pass the Browser Request to the protected app.

To make this example run first create a SPA Application in Auth0. Afterwards Update Auth0 config in `etc/nginx/conf.d/openid_connect_configuration.conf`.

Run `docker-compose build`
and `docker-compose up -d` 

A Example App protected by a Basic Authorization Header is spawned at localhost:3030 by default. This app can be accessed by the credentials admin:password and will print the headers to the UI.
This app would typically only be reachable through the proxy, in this case it can be reached directly to test.

Protected App: `http://localhost:3030`  
Proxy handling Auth on `http://localhost:8080` 
