# Introduction
This is the API reference documentation of Rethings IoT Platform

# Authentication
As it stands, Rethings does not have built-in authentication for [Consumers](#section/Consumers). 
Instead, you may opt to use your own SSO or another third party solutions such as [Auth0](https://auth0.com/) 
for your end users.

Rethings supports two forms of authentication -  Secret API Key and JSON Web Tokens. 
- [JWT](#section/Authentication/ConsumerJWT): short lifetime tokens for Consumers that can be assigned with 
a specific expiration time.
- [Secret API Key](#section/Authentication/SecretApiKey): used for requests made from the server side
on behalf of a Consumer. Never share these keys. Keep them guarded and secure.


<!-- ReDoc-Inject: <security-definitions> -->

# Consumers

A consumer represents a person that ultimately uses the products and apps built with Rethings.

Natively, Rethings does not support authentication of consumers. Hence, you must use
an external provider for your consumers (i.e. Auth0).

Our API supports signed JSON Web Tokens as a form of authentication.

### How would Rethings map the Consumer to the resources they own?
We pull the `sub` claim from JWT. This claim serves as the identifier of the Consumer.

### How would Rethings verify a legitimate JWT?
When you create an App with Rethings, you are required to put in your public key. This public
key is used to verify the authenticity of the JWT. (See [ConsumerJWT](#section/Authentication/ConsumerJWT))


# MQTT
At the core of Rethings is our MQTT service. Devices communicate with Consumers 
through MQTT pub-sub mechanism.

Credentials can be either `username` or `x509`. A client ID will be provided along
with the other details of the credentials. For `username` based credentials, password 
must be empty.

#### What's with the empty password ?
We believe that password only makes sense if it can be _remembered_. It will not make much
sense if it will be flashed to storage or hardcoded. 


| Server | Port | Scheme |
|---|---|---|
| mq.rethings.io | 8883 | mqtts |
| mq.rethings.io | 15673 | wss |


