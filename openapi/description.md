# Introduction
This is the API reference documentation of Rethings Management.

# Authentication
When you signin, Rethings backend starts session for you. 

Rethings supports two forms of authentication -  Cookie and Access Token. 
- [Cookie](#section/Authentication/UserToken): session ID is stored in a cookie. Primarily
used for web-based management dashboard.
- [Access Token](#section/Authentication/UserToken): used for requests made from a first-party
management mobile application.


<!-- ReDoc-Inject: <security-definitions> -->

# Users

A user represents a person that can log in to Rethings.

Rethings makes use of external party identity provider. All endpoint authentications hereon are based 
on signed JWT.

### How would Rethings map the User to the resources they own?
We pull the `sub` claim from JWT. This claim serves as the identifier of the User.
