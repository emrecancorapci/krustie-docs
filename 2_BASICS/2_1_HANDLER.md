# Handlers

```rust
fn(&Request, &mut Response)
```

Handlers are responsible for handling incoming requests and returning responses to the client. Instead of defining routes directly in the server, you can define handler functions that handle specific routes.

A handler is a function that takes a immutable `Request` and a mutable `Response` as arguments and returns nothing. To send a response to the client, you can use the `Response` object.

## Basic Structure of a Handler Function

```rust
fn get(req: &Request, res: &mut Response) {
    res.status(StatusCode::Ok).body_text("Hello World!");
}
```

The ***Request*** object contains information about the incoming request, such as the request method, path, query string, parameters, headers and body.

The ***Response*** object is used to set the response status code, headers, and body.
