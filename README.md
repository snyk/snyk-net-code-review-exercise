# .NET npm dependency server

A web server that provides a basic HTTP api for querying the dependency
tree of an [npm](https://npmjs.org) package.

## Prerequisites

* [.NET 5](https://dotnet.microsoft.com/download/dotnet/5.0)

## Getting Started

To install dependencies and start the server in development mode:

```sh
cd Snyk.Exercise.WebApi
dotnet watch run
```

The server will now be running on an available port (defaulting to 5001 for HTTPS, 5000 for HTTP) and
will restart on changes to the src files.

Then we can try the `/package` endpoint. Here is an example that uses `curl` and
`jq`, but feel free to use any client.

```sh
curl -s https://localhost:5001/package/react/16.13.0 | jq .
```

Most of the code is boilerplate; the logic for the `/package` endpoint can be
found in [Controllers/PackageController.cs](Snyk.Exercise.WebApi/Controllers/PackageController.cs), and some basic tests in
[PackageControllerTest.cs](Snyk.Exercise.WebApi.Test/PackageControllerTest.cs)

You can run the tests with:

```sh
dotnet test

# Or in watch mode
cd Snyk.Exercise.WebApi.Test
dotnet watch test
```
