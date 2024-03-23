 Conversational web apps
In this chapter, we introduce the student to the concept of conversational web 
applications. 
1.1 HTTP
HTTP is a communication protocol that allows computers (clients and servers) to 
communicate over the web. One important feature about HTTP is that it is stateless. 
This means, the protocol doesn’t sustain or maintain a conversation taking place 
between a client an a server. Every connection between a client and a server is seen 
as a new connection, previous states are forgotten.
A connection between a client and a server is established as follows:
▪ The client (browser) sends basic information about itself (browser name, 
communication protocol being used, acceptable data types that the browser 
can work with, etc.) to the server. 
▪ The server responds in kind by sending information about itself to the client 
(cookies). 
▪ A connection is established between the two computers. This is called 
handshaking.
▪ A client then sends an actual request to the server.
▪ The server services the request and sends a response.
▪ The connection is disconnected.
When a client attempts to send a subsequent request, it will not be remembered by 
the server. It will be seen as a new connection. Handshaking takes place, a new 
connection is established, communication (request/response) takes place.
The statelessness of HTTP is a flaw that makes it difficult to create conversational web 
applications. Conversational web apps need communication that is sustained a client 
and the server. The server needs to remember previous conversations it had with the 
same client in order to accomplish a task. A classical example is the online shopping 
web applications. When a client adds an item to the buying cart, subsequent requests
from the same client must not be seen or treated as coming from a new connection. 
They must be recognized as requests coming from the same connection established 
2
earlier. If a user wants to add another item, that item must find its place in the cart, 
added on top of the previous item. 
But the challenge is the statelessness of HTTP. The question is “How to we make 
HTTP stateful?”
1.1.1 How to make HTTP stateful?
Stateful simply means to remember previous states. HTTP is stateless, it only recalls 
the current state. To counter this weakness of HTTP, we use sessions and url
encoding to make HTTP stateful.
1.1.2 Using sessions
When a client performs a handshake with a server, the server establishes a session 
with the client and sends to the client a session ID. The session ID is used to identify 
the client every time a request is made to the server. As a result, every time these two 
communicate, they exchange the session ID. Session IDs are shared between 
computers using cookies. Cookies are just objects that contain information about each 
computer involved in the exchange of messages.
JEE provides us with a class called HttpSession which is used to create a session 
between the server and the client. An example will be done that shows the 
implementation of sessions in a web development environment.
1.1.3 Using url encoding
URL encoding is another technique used to establish a session between computers. 
Through encoding, the session ID is appended to the URL every time the server and 
client communicate. It is extracted and contrasted to the stored session in each 
computer. If a match exist, it means the two computers have communicated before, 
the request is not from a new connection. An example will be done to demonstrate this 
technique.
 
3
1.2 Example 1
In this example we create a basic web application that uses sessions. The applications 
holds social conversation with a user.
