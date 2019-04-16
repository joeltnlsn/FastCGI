# FastCGI for .NET

| Windows/.NET | Linux/Mono |
| ------------ | ---------- |
| wtf is this | I don't know how this build system works just build it yourself|

This is a modified and maintained version of FastCGI by whatever dude originally made it.

This is an implementation of [FastCGI](http://www.fastcgi.com/devkit/doc/fcgi-spec.html) for .NET, written in C#. It implements the parts of the protocol that are necessary to build a simple web application using .NET.

This means that you can write web applications in C# that serve dynamic content.

## License and contributing

This software is distributed under the terms of the MIT license. You can use it for your own projects for free under the conditions specified in LICENSE.txt.

If you have questions, feel free to contact me. Actually, I changed my mind. Don't.

If you think you found a bug, you can open an Issue on Github. If you make changes to this library, I would be happy about a pull request.

## Documentation

the code is undocumented and uncommented so you'll have to guess or read the source and fully understand it.


Lukas has probably documented it somewhere though, so check out the original repo.

## Nuget
This verion is not on nugget or whatever.
## Basic usage

The most common usage scenario is to use this library together with a web server like Apache and nginx. The web server will serve static content and forward HTTP requests for dynamic content to your application.

Have a look at the FastCGI.FCGIApplication class for usage examples and more information.

This code example shows how to create a FastCGI application and receive requests:

```csharp
// Create a new FCGIApplication, will accept FastCGI requests
var app = new FCGIApplication();

// Handle requests by responding with a 'Hello World' message
app.OnRequestReceived += (sender, request) =>
{
    var responseString =
          "HTTP/1.1 200 OK\n"
        + "Content-Type:text/html\n"
        + "\n"
        + "Hello World!";

    request.WriteResponseASCII(responseString);
    request.Close();
};

// Start listening on port 19000
app.Run(19000);
```

## Web server configuration

For nginx, use `fastcgi_pass` to pass requests to your FastCGI application:

    location / {
        fastcgi_pass   127.0.0.1:19000; # Pass all requests to port 19000 via FastCGI.
        include fastcgi_params; # (Optional): Set several FastCGI parameters like the remote IP and other metadata.
    }

For apache, I have no idea but Lukas added a link down there so check that out.

For more details, refer to your web server documentation for configuration details:

 * [nginx documentation](http://nginx.org/en/docs/http/ngx_http_fastcgi_module.html)
 * [Apache documentation](http://httpd.apache.org/mod_fcgid/mod/mod_fcgid.html)
