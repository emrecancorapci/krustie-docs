# Request

The `Request` struct represents an incoming HTTP request. It contains information about the request, such as the request method, path, query string, parameters, headers, and body.

*Request* cannot be accessed directly or modified anywhere in the code. It can only be accessed through the handler or middleware function with an immutable reference via methods.

## Methods

### `get_body() -> RequestBody`

Returns the body of the request as a `RequestBody` enum. The `RequestBody` enum represents the different types of request bodies that can be received.

````rust
use krustie::{Request, Response, RequestBody};

fn handler(req: &Request, res: &mut Response) {
    match req.get_body() {
        RequestBody::Binary(bin) => {
            println!("Received binary body: {:?}", bin);
        }
        RequestBody::Text(text) => {
            println!("Received text body: {}", text);
        }
        RequestBody::Json(json) => {
            println!("Received JSON body: {:?}", json);
        }
        RequestBody::None => {
            println!("Received an empty body.");
        }
    }
}
````

#### `RequestBody` enum

- `Text(String)`: Represents a text body.
- `Binary(Vec<u8>)`: Represents a binary body.
- `Json(JsonValue)`: Represents a JSON body.
- `None`: Represents an empty body.

> *`JsonValue` is the `Value` enum from the `serde_json` crate.*

### `get_query_param(key: &str) -> Option<&str>`

Returns the value of the query parameter with the specified name.

````rust
use krustie::{Request, Response};

fn handler(req: &Request, res: &mut Response) {
    if let Some(name) = req.get_query_param("name") {
        println!("Received query parameter: {}", name);
    }
}
````

| Request URL | Function Call | Returns |
| -- | -- | -- |
| `/hello?name=marvin` | `get_query_param("name")` | `Some("marvin")` |
| `/hello?planet=earth` | `get_query_param("name")` | `None` |

### `get_param(key: &str) -> Option<&str>`

Returns the value of the parameter with the specified name.

````rust
use krustie::{Request, Response};

fn handler(req: &Request, res: &mut Response) {
    if let Some(id) = req.get_param("id") {
        println!("Received parameter: {}", id);
    }
}
````

#### For `/hello/:name` Route

| Request URL | Function Call | Returns |
| -- | -- | -- |
| `/hello/marvin` | `get_param("name")` | `Some("marvin")` |
| `/hello/mars` | `get_param("planet")` | `None` |

## All Methods

| Method | Return Type | Description |
|--|--|--|
| `get_body()` | `RequestBody` | Returns the body of the request. |
| `get_header(key: &str)` | `Option<&str>` | Returns the value of the specified header. |
| `get_headers()` | `&HashMap<String, String>` | Returns a reference to the request headers. |
| `get_method()` | `&HttpMethod` | Returns the request method. |
| `get_param(key: &str)` | `Option<&str>` | Returns the value of the parameter with the specified name. |
| `get_params()` | `&HashMap<String, String>` | Returns a map of all parameters. |
| `get_path()` | `&str` | Returns the request path. |
| `get_path_array()` | `Vec<String>` | Returns the request path as an array of segments. |
| `get_peer_addr()` | `&SocketAddr` | Returns the address of the peer that sent the request. |
| `get_query_param(key: &str)` | `Option<&str>` | Returns the value of the query parameter with the specified name. |
| `get_query_params()` | `HashMap<String, String>` | Returns a map of all query parameters. |

> You can find more information about the `Request` struct in the [API documentation](https://docs.rs/krustie/latest/krustie/request/struct.Request.html).
