# Client-Server-Architecture

### Implementing a client-server-architecture with mysql

A `client-server architecture` is a computing model that divides tasks between two types of specialized software: clients and servers. 

 In this architecture, clients request services or resources such as files (text, audio, video, etc.), databases, or applications from servers and these server fulfill the clients requests by returning an intended response (delivering the service or resource) back to the client.

 ### Components of a Client-Server-Architecture
***`Client`:*** A client is a piece of software or a device that initiates (sends) requests to the server. A client could be a web browser, a mobile app, or any other software that needs access to resources that resides in a server. Clients are typically lightweight and are responsible for getting and presenting data to users in a user-friendly format.

*N/B: A client is not only limmited to a physical hardware device. A client can also be a piece of software that makes request to a server.*

***`Server`:*** A server is a specialized hardware computer or software that delivers intended request (resources or services) to clients upon request. Servers are powerfully machines designed and optimized for handling multiple client requests simultaneously. Servers store and manage data, perform computations, and ensures prompt delivery of tasks requested by clients.

***`Request-Response Model`:*** Communication between clients and servers in a client-server architecture typically follows a request-response model inwhich clients send requests to servers, specifying the desired action or resource and the Servers process these requests, sending back responds with the requested data or performs the requested action. Client-server interaction is typically facilitated through protocols like HTTP, HTTPS, FTP, SMTP, etc.
