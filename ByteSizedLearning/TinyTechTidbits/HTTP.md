# HTTP

## Introduction

HTTP is a set of rules which govern how data is exchanged on the internet. It operates as a request-response protocol in the client-server computing model.

What is a Client? What is a Server?
<div justify-content="center">
    <figure align="center">
        <img src="../../imgs/client_server.jpg" width="75%">
    <figcaption>client-server computing model</figcaption>
    </figure>
</div>

- **Client**: In the context of HTTP, a client is what requests data. For example, when you use a web browser to visit a website, your browser acts as the client.
- **Server**: A server, on the other hand, is where the data lives. It responds to the client's request by sending the requested data back. Websites are hosted on servers.

## HTTP Requests

An HTTP request is initiated by the client and directed towards a server to perform a specific action, identified by a URL (Uniform Resource Locator). The request consists of several key components:

### **Method**

The method indicates the action the client wants the server to perform. Common HTTP methods include (non-exhaustive list):

- **GET**: Retrieve data from the server.
- **POST**: Submit data to be processed to a specified resource.
- **PUT**: Update existing resources.
- **DELETE**: Remove existing resources.
- **HEAD**: Retrieve the headers sent with a response to a GET request, without the response body.

### **URL/URI**

HTTP requests are made to servers identified by URLs. The server could be anything from a web server hosting a website, to an API endpoint providing data or services, to a cloud-based storage service managing files. The specific part of the server or the resource the request is aimed at is detailed in the URL's path and parameters. It can include a query string, which contains additional parameters for the request.

### **Headers**

HTTP headers are key-value pairs sent between clients and servers as part of HTTP requests and responses. They provide essential information about the transaction, such as details about the client or server, the content being transferred, how the content should be handled, and any conditions or parameters that should be applied to the transaction. Headers are sent with the request, but also with the response. Here are some example of headers that are commonly used:

- HTTP Version
  This specifies the HTTP version used in the request, such as HTTP/1.1 or HTTP/2. Each version has different capabilities and features.
- Host: The domain name of the server (required in HTTP/1.1).
- Content-Type: The media type of the body of the request (e.g., application/json, text/html).
- User-Agent: Information about the client making the request.
- Authorization: Credentials for authenticating the client to the server.
- Accept: The media types that the client is willing to receive from the server. 5. Body

Not all requests have a body. Bodies are primarily used with POST and PUT requests to send data to the server. The body of an HTTP request can contain data in various formats, such as JSON, XML, or plain text, depending on what the server accepts and what the request is trying to accomplish.

### HTTP request example

Here is an example of an HTTP request:

```HTTP
GET /index.html HTTP/1.1
Host: www.example.com
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64)
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Connection: keep-alive
```

- The **Host header** is required in HTTP/1.1 and specifies the domain name of the server (or IP address) and, optionally, the port number.
- The **User-Agent header** identifies the client software making the request to the server.
- The **Accept header** specifies the media types that the client is willing to receive from the server.
- The **Accept-Language header** indicates the client’s preferred languages.
-The **Connection header** specifies options that are desired for the particular connection and can signal that the connection should be kept open for further requests.
