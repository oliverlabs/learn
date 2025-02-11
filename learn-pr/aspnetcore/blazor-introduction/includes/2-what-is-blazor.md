Blazor is a user interface framework for .NET that you can use to build applications. Let's take a tour of the capabilities of Blazor, along with the pros and cons of how you can configure it, to help you decide whether Blazor should be used in your next application.

## What is .NET?

.NET is a complete ecosystem for developing and deploying applications for desktops, mobile devices, the cloud, and IoT devices. Developers use programming languages likes Visual Basic, C#, and F# to build with .NET. You can use .NET tools on the command line, or in applications like Visual Studio or Visual Studio Code, to compile your code into a running application.

## What is Razor?

Razor is a format for generating text-based content, like HTML. Razor files have a `cshtml` or a `razor` file extension, and contain a mix of C# code along with HTML.

## What is Blazor?

Blazor is a user interface framework built on .NET and Razor. Blazor applications can run on a server as part of an ASP.NET application, or can be deployed to run in the browser on a user's machine similar to a single-page-application.

![Diagram of sample Blazor Application Architecture.](../media/intro-architecture.jpg)

## What is Blazor Server?

Blazor Server is an implementation of the Blazor user interface framework as part of the ASP.NET Core web development framework, deployed to a web server. Developing an application with Blazor Server generates HTML on a web server as it is requested by web site visitors, typically using a web browser. That HTML is then delivered to the visitor's browser, and a two-way communication pipeline is maintained using ASP.NET Core SignalR, preferably using a Web Sockets connection.

Users that click buttons, navigate, and perform other interactions with a Blazor Server application have their actions transmitted on the SignalR connection, and the server responds with user interface updates using the same connection. The Blazor Server framework automatically updates the browser with the content generated on the web server.

## What is Blazor WebAssembly?

Blazor WebAssembly, sometimes shortened to Blazor WASM, is an implementation of the Blazor user interface framework that runs on the HTML5 standard WebAssembly runtime present in all modern browsers. The binary output of your application, the DLL files, are transmitted to the browser and run with a version of .NET that has been optimized to work with the WebAssembly runtime, regardless of the underlying operating system of the device browsing to the website.

Since WebAssembly is a technology that runs entirely in the browser, it's possible to deploy this model of Blazor application using files that a web server doesn't parse or interact with. This type of *static* approach reduces the requirements for a web server and shifts all processing for the application to the user's machine.

Advanced processing and logic can take place in the browser. When the application needs data or to interact with other services, it can use standard web technologies to communicate with HTTP services.

## How to build an application with Blazor

Blazor applications are written with a text editor and built with the .NET tools. You'll choose where you'd like your Blazor application to run. The application can run on the server or in the browser with WebAssembly. Start with a template for the project type that matches where you want your application to run. You'll then write pages using Razor that users can interact with and navigate between. Blazor provides a bridge to allow users to build user interface elements that interoperate with JavaScript. You can integrate with other services, like a database or web service, to provide extra business value. You can also reference libraries or bundles of features using NuGet packages, the .NET packaging format.

Once you've completed writing the code for your application, you can build it with the .NET compiler tools and publish the resulting application to a web server for your users to access.

### What are Pages?

In Blazor, you'll build a *Page* with Razor that presents a screen of content in the browser. A *Page* typically maps directly to a web address to which a user would navigate in your application.

### What are Components?

Pages would be more difficult to build if you had to rewrite every line of HTML without any reuse between pages. A Razor *Component* is a self-contained portion of user interface with processing logic to enable dynamic behavior, and can be referenced and used in other components or pages.
