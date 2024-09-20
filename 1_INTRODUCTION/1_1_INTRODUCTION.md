# Introduction

Krustie is a simple HTTP server library written in Rust. It is designed to be a simple and easy-to-use web server that can be used for a variety of purposes. Krustie's error-prone design makes it difficult to write incorrect code.

> Krustie is still in the early stages of development and is not yet ready for production use. The API is subject to change and there may be bugs or missing features.

## Features

- Router with support for parameter and query string parsing
- Middleware support for routers and endpoints
- JSON data parsing and serialization (using the `serde` library)

### Built-in Middlewares

- Static file serving
- Rate limiting
- Gzip compression

### Planned Features

- Templating support
- Database integration
- Authentication middleware
- Secure headers middleware
- CORS support
- Asynchronous request handling
- Session management
- Cookie parsing and serialization
- Form data parsing
- Multipart form data parsing
- Redirects
- Error handling middleware
- Logging middleware
- Websocket support
- HTTPS support
