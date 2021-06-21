# Create Web API

## Resources

- [Where it all started, Roy Fielding's dissertation](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm)
> “The key abstraction of information in REST is a resource. Any information that can be named can be a resource: a document or image, a temporal service (e.g. "today's weather in Los Angeles"), a collection of other resources, a non-virtual object (e.g. a person), and so on. In other words, any concept that might be the target of an author's hypertext reference must fit within the definition of a resource. A resource is a conceptual mapping to a set of entities, not the entity that corresponds to the mapping at any particular point in time.” - Roy Fielding
- [Rest API Guidelines from Microsoft](https://github.com/microsoft/api-guidelines)
- [Richardson Maturity Model](https://www.martinfowler.com/articles/richardsonMaturityModel.html)
- [Nouns vs Verbs](https://cloud.google.com/blog/products/api-management/restful-api-design-nouns-are-good-verbs-are-bad)
- [Curated list of Public APIs to play with](https://github.com/public-apis/public-apis)

### Check out request based on DogFacts

Use Postman to navigate to:

https://dog-facts-api.herokuapp.com/api/v1/resources/dogs?number=1

## Example

A good example of a well designed [REST API is GitHub](https://docs.github.com/en/rest)

## HTTP Verbs

Simplified list of HTTP Verbs

| **HTTP METHOD** | **CRUD**              | **ENTIRE COLLECTION (E.G. /USERS)**                                                                      | **SPECIFIC ITEM (E.G. /USERS/123)**                                            |
|-----------------|-----------------------|----------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------|
| POST            | Create                | 201 (Created), ‘Location’ header with link to /users/{id} containing new ID.                             | Avoid using POST on single resource                                            |
| GET             | Read                  | 200 (OK), list of users. Use pagination, sorting and filtering to navigate big lists.                    | 200 (OK), single user. 404 (Not Found), if ID not found or invalid.            |
| PUT             | Update/Replace        | 405 (Method not allowed), unless you want to update every resource in the entire collection of resource. | 200 (OK) or 204 (No Content). Use 404 (Not Found), if ID not found or invalid. |
| PATCH           | Partial Update/Modify | 405 (Method not allowed), unless you want to modify the collection itself.                               | 200 (OK) or 204 (No Content). Use 404 (Not Found), if ID not found or invalid. |
| DELETE          | Delete                | 405 (Method not allowed), unless you want to delete the whole collection — use with caution.             | 200 (OK). 404 (Not Found), if ID not found or invalid.                         |

## HTTP Status Codes

| **S.N.** | **Code and Description**                                                                 |
|----------|------------------------------------------------------------------------------------------|
| 1        | 1xx: Informational It means the request has been received and the process is continuing. |
| 2        | 2xx: Success It means  the action was successfully received, understood, and accepted.   |
| 3        | 3xx: Redirection It means further action must be taken in order to complete the request. |
| 4        | 4xx: Client Error It means the request contains incorrect syntax or cannot be fulfilled. |
| 5        | 5xx: Server Error It means the server failed to fulfill an apparently valid request.     |


| **Message**             | **Description**                                                                                                                                   |
|-------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| 100 Continue            | Only a part of the request has been received by the server, but as long as it has not been rejected, the client should continue with the request. |
| 101 Switching Protocols | The server switches protocol.                                                                                                                     |

| **Message**                       | **Description**                                                                                                                                                                                                |
|-----------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 200 OK                            | The request is OK.                                                                                                                                                                                             |
| 201 Created                       | The request is complete, and a new resource is created .                                                                                                                                                       |
| 202 Accepted                      | The request is accepted for processing, but the processing is not complete.                                                                                                                                    |
| 203 Non-authoritative Information | The information in the entity header is from a local or third-party copy, not from the original server.                                                                                                        |
| 204 No Content                    | A status code and a header are given in the response, but there is no entity-body in the reply.                                                                                                                |
| 205 Reset Content                 | The browser should clear the form used for this transaction for additional input.                                                                                                                              |
| 206 Partial Content               | The server is returning partial data of the size requested. Used in response to a request specifying a Range header. The server must specify the range included in the response with the Content-Range header. |


| **Message**            | **Description**                                                                                                                          |
|------------------------|------------------------------------------------------------------------------------------------------------------------------------------|
| 300 Multiple Choices   | A link list. The user can select a link and go to that location. Maximum five addresses  .                                               |
| 301 Moved Permanently  | The requested page has moved to a new url .                                                                                              |
| 302 Found              | The requested page has moved temporarily to a new url .                                                                                  |
| 303 See Other          | The requested page can be found under a different url .                                                                                  |
| 304 Not Modified       | This is the response code to an If-Modified-Since or If-None-Match header, where the URL has not been modified since the specified date. |
| 305 Use Proxy          | The requested URL must be accessed through the proxy mentioned in the Location header.                                                   |
| 306 Unused             | This code was used in a previous version. It is no longer used, but the code is reserved.                                                |
| 307 Temporary Redirect | The requested page has moved temporarily to a new url.                                                                                   |

| **Message**                         | **Description**                                                                                                                                                  |
|-------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 400 Bad Request                     | The server did not understand the request.                                                                                                                       |
| 401 Unauthorized                    | The requested page needs a username and a password.                                                                                                              |
| 402 Payment Required                | You can not use this code yet.                                                                                                                                   |
| 403 Forbidden                       | Access is forbidden to the requested page.                                                                                                                       |
| 404 Not Found                       | The server can not find the requested page.                                                                                                                      |
| 405 Method Not Allowed              | The method specified in the request is not allowed.                                                                                                              |
| 406 Not Acceptable                  | The server can only generate a response that is not accepted by the client.                                                                                      |
| 407 Proxy Authentication Required   | You must authenticate with a proxy server before this request can be served.                                                                                     |
| 408 Request Timeout                 | The request took longer than the server was prepared to wait.                                                                                                    |
| 409 Conflict                        | The request could not be completed because of a conflict.                                                                                                        |
| 410 Gone                            | The requested page is no longer available .                                                                                                                      |
| 411 Length Required                 | The "Content-Length" is not defined. The server will not accept the request without it .                                                                         |
| 412 Precondition Failed             | The pre condition given in the request evaluated to false by the server.                                                                                         |
| 413 Request Entity Too Large        | The server will not accept the request, because the request entity is too large.                                                                                 |
| 414 Request-url Too Long            | The server will not accept the request, because the url is too long. Occurs when you convert a "post" request to a "get" request with a long query information . |
| 415 Unsupported Media Type          | The server will not accept the request, because the mediatype is not supported .                                                                                 |
| 416 Requested Range Not Satisfiable | The requested byte range is not available and is out of bounds.                                                                                                  |
| 417 Expectation Failed              | The expectation given in an Expect request-header field could not be met by this server.                                                                         |

| **Message**                    | **Description**                                                                                  |
|--------------------------------|--------------------------------------------------------------------------------------------------|
| 500 Internal Server Error      | The request was not completed. The server met an unexpected condition.                           |
| 501 Not Implemented            | The request was not completed. The server did not support the functionality required.            |
| 502 Bad Gateway                | The request was not completed. The server received an invalid response from the upstream server. |
| 503 Service Unavailable        | The request was not completed. The server is temporarily overloading or down.                    |
| 504 Gateway Timeout            | The gateway has timed out.                                                                       |
| 505 HTTP Version Not Supported | The server does not support the "http protocol" version.                                         |



### Choose App Service SKU plan

![App Service SKU](https://github.com/Piotr1215/azure-architect-exams-resources/blob/master/App-Plan-SKU.png?raw=true)

### API Demo

This is a sample web API generated by using `dotnet new webapi` with default language as C#

To test the API call, please install [REST API Test Client](https://marketplace.visualstudio.com/items?itemName=humao.rest-client) extension and execute call from the [test-api file](test-api.rest)

### CI/CD

For this demo there is CI/CD process setup.