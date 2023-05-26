# Web

#### What is a JWT token?

>JWT stands for JSON Web Token, which is a compact, URL-safe means of representing claims to be transferred between two parties. It is commonly used for authentication and authorization in web applications.

>A JWT token consists of three parts separated by dots: the header, the payload, and the signature. The header contains information about the type of token and the algorithm used for the signature. The payload contains the claims, or information about the user, that are being transmitted. The signature is used to verify that the sender of the token is who they claim to be and that the message has not been tampered with.

Here's an example of a JWT token:

    eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c

>In this example, the header is eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9, the payload is eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ, and the signature is SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c.

>The header specifies that the token is a JSON Web Token and that the signature algorithm used is HMAC SHA-256. The payload contains three claims: the user ID, the user's name, and the timestamp of when the token was issued. The signature is used to verify that the token was sent by the party that claims to have issued it and that it has not been tampered with.

>JWT tokens are commonly used in web applications for authentication and authorization. When a user logs in, the server generates a JWT token and sends it to the client. The client then includes the token in each subsequent request to the server to authenticate the user and access protected resources. The server verifies the token's signature to ensure that it was issued by a trusted party and that the claims contained in the payload are valid.


#### What is a callback function?
#### What is a JWT token?
#### What is a promise?
#### What is a REST API?
#### What is a schema in XML? How to validate a schema?
#### What is AJAX and why is it used?
#### What is an HTTP code and what does 200 OK mean?
#### What is an HTTP code and what does 400 Bad Request mean?
#### What is an HTTP code and what does 403 Forbidden mean?
#### What is an HTTP code and what does 404 Not Found mean?
#### What is an HTTP code and what does 503 Service Unavailablee?
#### What is an HTTP method and when is DELETE used?
#### What is an HTTP method and when is GET used?
#### What is an HTTP method and when is PATCH used?
#### What is an HTTP method and when is POST used?
#### What is an HTTP method and when is PUT used?
#### What is DOM?
#### What is JSON? When to use?
#### What is serialization?
#### What is the difference between HTML and XML?
#### What is the difference in JavaScript between == and ===?                                                 
#### What is the difference in JavaScript between null and undefined?
#### What kind of HTTP status codes do you know?