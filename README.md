# bs-compression
Bucklescript Bindings for [compression](https://github.com/expressjs/compression) express middleware.

This package can be used only with `bs-express`. You need to add `bs-express` as a dependency in your project.

# Usage 

For instance, here is the code to serve static files from `public` folder and compress them.
Remark: The compression middleware should be first.
```reason
let app = express();
App.useOnPathWithMany(
  app,
  ~path="/public",
  [|
  Compression.compression(),
  {
    let options = Static.defaultOptions();
    Static.make("public", options) |> Static.asMiddleware
  }
  |]
);
```
