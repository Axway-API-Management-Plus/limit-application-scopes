

# Description
In certain situations it makes sense, that an application gets only a limited set of OAuth-Token-Scopes. For instance, to make restrict some API-Methods by higher-scopes, that are not available 
to all applications.
By default, the an application in API-Manager gets all Scopes of all APIs that Application is subscribed to. There is no way to restrict the scopes for an API-Administrator. 

This policy provides the option to restrict the scopes per consuming application.

## API Management Version Compatibilty
This artefact was successfully tested for the following versions:
- V7.5.3


## Install

 1. Import the Policy-Fragment: limit_application_scopes.xml into your API-Manager Group configuration
 2. In the Container: OAuth 2.0 > Access Token Service you find a policy for all support flows, like Client Credentials, JWT, Resource Owner ...
 3. For all OAuth-Flows you want to support, change the appropriate policy. Open it ...
 4. ... and change the filter issuing the token. For example: Client Credentials
 5. Open the filter: "Access Token using client credentials" change to the second tab: "Access Token", at the bottom select: "Get scopes by calling a policy" and select the imported policy: "Get scopes for application"
![Change scope generation](https://github.com/Axway-API-Management-Plus/limit-application-scopes/blob/master/images/token_generation_scopes.png)

## Usage
In the API-Manager UI please make sure, that the global API-Manager setting: "Enable OAuth scopes per application" is enabled.

![Scopes per application](https://github.com/Axway-API-Management-Plus/limit-application-scopes/blob/master/images/enable_scopes_per_application.png)

This gives you by the default the option in the API-Manager to configure additional scopes for an application.
![Application scopes](https://github.com/Axway-API-Management-Plus/limit-application-scopes/blob/master/images/application_scopes_config.png)

But when using this policy, we are leveraging these scope settings. 
When configured in that way, an application will only get the scopes configured for an application and the switch "Default" is enabled, as the policy is considering it as Enabled/Disabled instead of a default.

At runtime you will see on DEBUG the following:
````
INFO	.....	  Getting scopes for app: My great application
DEBUG	.....	  Scope: Scope1 enabled: true
DEBUG	.....	  Scope: Scope2 enabled: false
INFO	.....	  Returning scopes for application: 'Scope1'
````

## Bug and Caveats

Nothing known.

## Contributing

Please read [Contributing.md](https://github.com/Axway-API-Management/Common/blob/master/Contributing.md) for details on our code of conduct, and the process for submitting pull requests to us.


## Team

![alt text][Axwaylogo] Axway Team

[Axwaylogo]: https://github.com/Axway-API-Management/Common/blob/master/img/AxwayLogoSmall.png  "Axway logo"


## License
[Apache License 2.0](/LICENSE)

