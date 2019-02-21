# Hypertext Transfer Protocol (HTTP)
HTTP is an asymmetric **request–response protocol** in the client–server computing model.

_Example 1: A web browser is the client and an application running on a computer hosting a comic 
website may be the server._ 

![](imgs/http-exchange-overview.png)

Let's focus on the steps (2) and (4). HTTP client and server communicate by sending text messages. 
The client sends a request message to the server.  The server, in turn, returns a response message.

# The client sends a request message. (HTTP Request)
The image above describe the taxonomy of a http request message.
![](imgs/http-request-message.png)

The _request message header_ corresponds to the **metadata** of the message that the 
server needs to know in order to locate the resource or actions required by the client.

## HTTP verbs 
The request line message specifies the HTTP verb. The purpose of the HTTP verb is to 
indicate the desired action to be performed on the identified resource.
There exists [9](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol#Request_methods), however in web 
development the most used are:

| Method  |                        Description                                                                                                                                                                                                                               |     Safe    | Idempotent |
| ------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------- | ---------- |
| OPTIONS | The OPTIONS method returns the HTTP methods that the server supports for the specified URL.                                                                                                                                                                      |     Yes     |     Yes    |
| GET     | Requests using GET should only retrieve data and should have no other effect.                                                                                                                                                                                    |     Yes     |     Yes    |
| POST    | The POST method requests that the server accept the entity enclosed in the request as a new subordinate of the web resource identified by the URI.                                                                                                               |      No     |     No     |
| PUT     | The PUT method requests that the enclosed entity be stored under the supplied URI. If the URI refers to an already existing resource, it is modified; if the URI does not point to an existing resource, then the server can create the resource with that URI.  |      No     |     Yes    |
| DELETE  | The DELETE method deletes the specified resource.                                                                                                                                                                                                                |      No     |     Yes    |

To know the rest of the HTTP verbs and further details refer to the bibliography at the end of the page.

## HTTP headers
The Request headers define the operating parameters of an HTTP transaction.
There exists a [long list](https://en.wikipedia.org/wiki/List_of_HTTP_header_fields#Request_fields) of standard request headers

In the example, the header `Accept: image/gif, image/jpeg, */*` indicates that the media type _**acceptable**_ for the response which must match the specified format. In other words, the browser is waiting for an `gif` or `jpeg` image.

**Each header has its own purpose, please refer to the [list](https://en.wikipedia.org/wiki/List_of_HTTP_header_fields#Request_fields).**

## HTTP Message Body
HTTP Message Body is the data bytes transmitted in an HTTP transaction message. It's optional 

In the example, the GET method sends its query `bookId=12345&author=Tan+Ah+Teck` on the message body.

# Server returns a response message. (HTTP Response)
The image above represents the format of an HTTP response message:
![](imgs/http-response-message.png)

## Status Line
The first line of a Response message is the Status-Line, consisting of the protocol version followed by a numeric status code and its associated textual phrase.

In our example,
* Protocol Version :  `HTTP/1.1`
* Status Code      :  `200`     
* Reason Phrase    :  `OK`

### Status Code and Reason Phrase
The Status-Code element is a 3-digit integer result code of the attempt to understand and satisfy the request. The Reason-Phrase is intended to give a short textual description of the Status-Code.

The first digit of the Status-Code defines the class of response:

    - 1xx: Informational - Request received, continuing process
    - 2xx: Success - The action was successfully received, understood, and accepted
    - 3xx: Redirection - Further action must be taken in order to complete the request
    - 4xx: Client Error - The request contains bad syntax or cannot be fulfilled
    - 5xx: Server Error - The server failed to fulfill an apparently valid request
    
Please refer to the [complete list](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes) to understand the meaning of each code.

A few commons are:

    - 200 OK
    - 201 Created
    - 403 Forbidden
    - 404 Not Found
    - 500 Internal Server Error

## HTTP headers
The Response headers have the same goal of the request headers.
In our example, the header `Content-type` indicates the media type of the message body, which in this case 
is `text/html`. With this information the browser knows that it needs to interpret the HTML code.

Here the list of the [commons examples](https://en.wikipedia.org/wiki/Media_type#Common_examples) of possible values for the header `Content-type` or `Accept`.

## HTTP Message Body
The response body contains the requested document. The browser will format and display the document according to its
 [media type]((https://en.wikipedia.org/wiki/Media_type#Common_examples)) (e.g., Plain-text, HTML, JPEG, GIF, and etc.) and other information obtained from the response headers.

In our example, the browser receives the HTML code `<h1>My Home Page</h1>`, and after the analysis of the `Content-type` header, what it will display?

# References
* [Wikipedia](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol)
* [HTTP Basics](https://www.ntu.edu.sg/home/ehchua/programming/webprogramming/HTTP_Basics.html)
* [Hypertext Transfer Protocol -- HTTP/1.1 . Response](https://www.w3.org/Protocols/rfc2616/rfc2616-sec6.html)