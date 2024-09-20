# Getting Started

## Prerequisites

It is assumed that you have Rust installed on your system. If you do not have Rust installed, you can install it by following the instructions on the [official Rust website](https://www.rust-lang.org/tools/install).

## Installation

### Create a New Project

Create a new Rust project using the following command:

```sh
cargo new hello_world --bin 
```

This will create a new directory called `hello_world` with a `Cargo.toml` file and a `src` directory containing a `main.rs` file.

### Add Krustie to Your Project

To install latest Krustie use the following command in your terminal:

```sh
cargo add krustie
```

or add the following to your `Cargo.toml` file:

```toml
[dependencies]
krustie = "*"
```

## Hello World Example

Here is a simple example of how to create a basic web server using Krustie:

```rust
use krustie::{Router, Server, StatusCode};

fn main() {
    let mut server = Server::create();
    let mut main_router = Router::new();

    main_router.get(|_, res| {
        res.status(StatusCode::Ok).body_text("Hello World!");
    });

    server.use_handler(main_router);

    server.listen(8080);
}
```

The app starts a server on port `8080` and responds with `Hello World!` to any incoming *GET* request to the root path (`/`).

The **Router** object is used to define the routes and the **Server** object is used to start the server and listen for incoming requests.

## Running the Server

To run the server, use the following command:

```sh
cargo run
```

When the server is running, you can access it by opening a web browser and navigating to `http://localhost:8080`.

## Building the Server

To build the server, use the following command:

```sh
cargo build
```

This will create an executable file in the `target/debug` directory.

## Conclusion

You have successfully created a simple web server using Krustie. You can now start building more complex applications by adding routes, middleware, and controllers to your server.
