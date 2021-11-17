# [.NET Conf 2021](https://www.dotnetconf.net/)
- [YouTube playlist](https://www.youtube.com/playlist?list=PLdo4fOcmZ0oVFtp9MDEBNbA2sSqYvXSXO)
- [Slides/code](https://github.com/dotnet-presentations/dotNETConf/tree/master/2021/MainEvent/Technical)

## Day 1 - 2021-11-09
### Day 1 - 08:00 Keynote
_Scott Hunter, Daniel Roth, Maria Naggaga, Mads Torgersen, Maddy Leger_
- C# 10
    - simplified
    - `record struct` support
    - simpler lambdas, compiler will try to figure out types so you don't always have to specify Func<>
- Shorter `dotnet new` menu
- More VS templates can now select .NET version
- Simplification/minification focus
    - 1 line console apps
    - 4 line web apps
    - app.MapGet, etc., take `delegate`s which the compiler now figures out
    - `global using` make your usings in one file, instead of all of them
    - implicit usings, common namespaces, turned on/off in the project file
    - `namespace Thing;` applies the namespace to the rest of the file, no braces/indentation
    - `record` implicitly == `record class`; `record struct` now supported
- YARP 1.0 now available, hugely scalable
- Azure .NET 6 is available today: App Service, Static Web Apps, Functions
- Azure Container Apps handle all infrastructure so you can focus on app development
    - VS 17.1 (preview) publish some app types direct to ACA
    - Uses Dapper for service-to-service location/communication
- Blazor
    - AOT compilation for much faster client-side
    - Fluent UI Components, 40+ components
    - Much smaller runtime available with analysis of your app
    - Pre-rendering stores app state in the page
- MAUI
    - Shipping early 2022
    - Next "version" of Xamarin
    - One project supports all the app types
    - Native UI on Win, Mac, iOS, Android
    - Can reference Blazor and use your web components
    - Preview 10 is now available, sxs support
    - Uses Win11 subsystem for Android (Amazon App Store so doesn't support everything)
- Encouragement to move legacy apps to .NET 6 (LTS) because of perf and usability improvements
    - Web API and MVC migrate "easily"
    - Web forms to Blazor Server (best/natural mapping) is more difficult but there is a book on it
- .NET Framework 4.8.1
- https://aka.ms/dotnet6-Code-Mag
- Sessions: https://youtube.com/dotnet

### Day 1 - 09:30 What's new in C# 10
_Mads Torgersen, Dustin Campbell_
- `with` expressions now work with regular structs, not just record structs
- `with` also works with anonymous types
- structs
    - Now support parameterless constructors
    - Now support property initializers
- Lambdas can now have attributes
- Can now assign a method to a variable

### Day 1 - 10:00 Enterprise-grade Blazor apps with .NET 6
_Daniel Roth_
- Error boundaries
    - `<ErrorBoundary>` around your component usages
- Better SVG support
- `<head>` manipulation
    - `<PageTitle>` - signals you want to modify it
    - `<HeadContent>` - add any content to head
- `SupplyParameterFromQuery` attribute to auto-inject from query string to property
- `GenerateAngular`, `GenerateReact` to create components for JS that is your same C# code
- Add WebAssembly build tools in VS for AOT, etc.

### Day 1 - 10:30 Introduction to .NET MAUI
_Maddy Leger_
- Mobile dev with .NET workload + optional .NET MAUI preview component
- Android
    - Install Windows Subsystem for Android from Microsoft Store
        - Turn on Developer Mode in settings
        - Turn on continuous if you want the app to keep running (especially good if you accidentally close the app)
        - Copy IP address and use `adb connect {ip address}`
    - Amazon App Store so no Google Play APIs
- iOS
    - Can now plug phone directly into Win machine and deploy to it from VS
- Upgrade Assistant is now stable; will eventually support Xamarin/MAUI apps

### Day 1 - 11:00 What's New in F# 6
_Kathleen Dollard, Don Syme_
- Pipeline debugging can see inputs to each stage
- async didn't match .NET async; added task-based programming, `async` -> `task`

### Day 1 - 11:30 Speed up your .NET development with Hot Reload
_Dmitry Lyalin_
- `dotnet watch` cli also supports hot reload

### Day 1 - 12:00 Testing tools for .NET and cross-platform apps
_Kendra Havens_
- `dotnet-coverage` is now managed code so it is cross-platform
- hot reload extends into test engine
- debug into Linux containers, needs remote debugging component
    - preview stuff, may be manual setup
- Playwright - new web ui testing framework (preview)
    - generates code (multiple languages) of a manual web test run
    - can take screenshots throughout
    - runs multiple browsers
- Resources
    - https://aka.ms/testexplorer
    - https://aka.ms/dotnet-coverage
    - https://aka.ms/remotetesting
    - https://aka.ms/playwright

### Day 1 - 12:30 Supercharge your Productivity with Roslyn and AI
_Mika Dumont_

### Day 1 - 13:00 Minimal APIs in .NET 6
_Stephen Halter, Safia Abdalla_

### Day 1 - 13:30 ASP.NET Core MVC & Razor Pages in .NET 6
_Daniel Roth_
- min APIs are ~2x faster than api controllers
- ~40% faster jwt auth
- MVC on Linux ~12% faster
- ~10% RPS gain in MemoryCache
- ~70% working set (memory) reduction for idle WebSocket
- grpc faster; protobuf ~20% faster
- Productivity enhancements, new razor source generator
- MVC and razor pages
    - css isolation

### Day 1 - 14:00 Next-generation Blazor components with .NET 6
_Daniel Roth, Javier Calvarro Nelson Calvarro Nelson_

### Day 1 - 14:30 What's New in EF Core 6
_Jeremy Likness, Arthur Vickers_
- Support for sql temporal tables

### Day 1 - 15:00 Upgrading from .NET Framework to .NET 6
_Cathy Sullivan, Sunanda Balasubramanian_
- .NET Upgrade Assistant has been upgraded with more scenarios (but not web forms, wcf, and remoting, which simply aren't supported in .net core)
- Can create your own extensions to add your own analysis

### Day 1 - 15:30 Build cross-platform native apps with .NET MAUI and Blazor
_Eilon Lipton_

### Day 1 - 16:00 Secure minimal APIs with .NET 6 and Microsoft Identity
_Christos Matskas_

### Day 1 - 16:30 .NET Everywhere - Windows, Linux, and Beyond
_Scott Hanselman_
- dotnet.microsoft.com/learntocode

### Day 1 - 17:00 CodeParty Day 1
_Jeffrey T. Fritz_


## Day 2 - 2021-11-10
### Day 2 - 07:00 CodeParty Day 2
_Jeffrey T. Fritz_

### Day 2 - 09:00 Warp-speed WebAssembly with Blazor in .NET 6
_Steve Sanderson_
- NativeFileReference allows linking native code into web assembly code (e.g., Sqlite, rust-based assembly)
- `RegisterAsCustomElement` (preview) to 
- Hot reloading both React and Blazor is pretty cool

### Day 2 - 09:30 6 ways to get started with .NET 6 and App Service
_Byron Tardif_
- App Service, Functions, and Static Web Apps all support .NET 6

### Day 2 - 10:00 ML.NET: Machine learning from data to production in less than 30 minutes
_Bri Achtman, Luis Quintanilla_

### Day 2 - 10:30 Full-stack .NET with Blazor WebAssembly and Azure Static Web Apps
_Anthony Chu, Simona Cotin_
- Jamstack == JavaScript, APIs, and markup; Bamstack?
- https://aka.ms/SWA-Blazor

### Day 2 - 11:00 Enhance your .NET apps with Azure Communication Services
_Chris Palmer, Mary Anne Noskowski_
- Video, voice, chat, SMS, and telephony; Microsoft Teams' api
- Interoperable with Teams

### Day 2 - 11:30 Bring More Power to your Web API's with the Power Platform
_April Dunnam_

### Day 2 - 12:00 Microsoft Teams app development with Visual Studio and .NET
_John Miller, Pierce Boggan_

### Day 2 - 12:30 Serverless .NET 6 with Azure Functions
_Anthony Chu_
- Managed identity
    - Blobs, queues, event hubs, event grid, and service bus now support identity-based connections, instead of connection strings and/or keys
    - Works locally too
- Fns can now do pubsub
- Execution models
    - In-process execution model supported for .NET 6 but later versions will be isolated process model only
    - Durable fns only in-process, until that isolated process functionality comes in 2022

### Day 2 - 13:00 Develop amazing WIndows apps using the Windows App SDK
_Andrew Clinick, Andrew Whitechapel, Dian Hartono, Eve Mwangi_

### Day 2 - 13:30 Build .NET Applications with Visual Studio Code
_Luis Quintanilla_

### Day 2 - 14:00 Modern data APIs with EF Core and GraphQL
_Jeremy Likness_
- GraphQL
    - Query lang for apis
    - Runtime to fulfill queries
    - Focused on frontend-to-backend communication
    - Strongly typed and discoverable schemas
    - Client controls shape of data
    - Real time via subscriptions
- vs. OData
    - Different use cases
    - GQL has resolvers to handle parts of the query
    - OData is generic but it is heavily used in .NET world
- Why?
    - Single endpoint to reference lots of other services
    - Discoverability
    - Avoid over-fetching data
    - Minimize round trips
    - Reduced need to worry about versioning the API because client describes projection
    - Schema-stitching for schema at scale
    - Facade to legacy services like WCF
- Nearly "just works" with EF
- Portions of request can be asynchronous...wow
- Resources
    - https://aka.ms/efdocs
    - https://chillicream.com/docs/hotchocolate
- .NET clients - they all do things a bit differently
    - GraphQL.net
    - EF Core GraphQL
    - Hot Chocolate

### Day 2 - 14:30 Diagnostics and Observability of .NET Applications
_Sourabh Shirhatti_
- Observability is a property of a system that has been designed/tested/monitored to handle unpredictable characteristics of distributed systems
- Three pillars
    - distributed traces (i.e., with a context id)
    - event logs
    - metrics
- Deep diagnostic artifacts
    - Memory dumps
    - GC dumps - graph of objects on the heap, with counts but not values
    - Profiles - ETW, etc., with high verbosity. Turning it on will impact perf.
- OpenTelemetry
    - Tools, api, and sdks that are vendor neutral
    - Some minor differences in terminology (span vs activity)
    - Implemented in BCL so library authors can participate
- .NET 6 adds propogators (send and receive transformers)
- Logging in .NET
    - `Microsoft.Extensions.Logging` - `ILogger`
        - DI aware
        - Lots of logging sinks
    - `EventSource`
        - High volume verbose logging, less structured
- Metrics in .NET
    - System.Runtime.Metrics - new api that is OpenTelemetry compliant
- `dotnet-monitor`
    - simplifies collection and observability
    - HTTP API
    - host in sidecar

### Day 2 - 15:00 High-performance services with gRPC: What's new in .NET 6
_James Newton-King_
- Perf
    - Protobuf
        - 20% faster for string serialization
        - Zero-copy ByteString api
    - grpc download speed
        - automatically detects latency, increases buffer if fast
    - Blazor AOT with grpc-web
        - 10x faster
- Transient fault handling
    - Automatically retry failed calls, configured with statuses to retry and exponential backoff
- Client-side load balancing!
    - Client to many servers
    - Discover endpoints (DNS, static, custom)
    - Load balance (pick first, round robin, custom) - circuit breaker supported with dynamic discovery updating
- HTTP/3 (preview)
    - faster, improved packet loss handling, better transitioning between networks
- Resources
    - https://aka.ms/grpcdocs
    - https://aka.ms/grpcexamples

### Day 2 - 15:30 Microservices Made Easy!
_Jessica Deen_
- Dapr has 80+ components!, to be used as needed
- Bridge to Kubernetes is used for debugging, puts local dev machine into the cluster (cloud or local)
- https://aka.ms/jldeennetconf2021
- local kurernetes via docker desktop, minikube, or kind

### Day 2 - 16:00 What's new in .NET Interactive notebooks
_Alan Yu, Julie Koesmarno_
- KQL - new lang
- variable sharing across C#, F#, PS, TSQL, and Kusto
- Renderer extensions like Data Table
- TSQL improvements
- Codespaces support

### Day 2 - 16:30 Building reliable and portable microservices with Dapr and .NET
_Paul Yuknewicz_
- https://docs.dapr.io/getting-started
- https://docs.dapr.io/developing-applications/sdks/dotnet

### Day 2 - 17:00 Not Thinking Small - My Journey to Learning .NET
_Elahn Harris_

### Day 2 - 17:30 Stories from interning on the .NET team
_Cathy Sullivan, Jessica Houghton_

### Day 2 - 18:00 Benchmarking ASP.NET Applications with .NET Crank
_Sebastien Ros_

### Day 2 - 18:30 Power Up Your Development with Power Automate and Power Apps
_Matt Soucoup_

### Day 2 - 19:00 Updates on Migrating to Azure App Service
_David Ellis_

### Day 2 - 19:30 Blazor Azure B2C Authentication and Authorization
_Michael Washington_

### Day 2 - 20:00 Accelerate .NET to Azure with GitHub Actions... Again?
_Isaac Levin_

### Day 2 - 20:30 Enterprise IoT with full .NET using Meadow on Embedded Hardware
_Adrian Stevens, bryan costanich_

### Day 2 - 21:00 .NET Internet of Things
_Melissa Houghton_

### Day 2 - 21:30 Brand New! Azure Functions OpenAPI Extension on .NET 6
_Justin Yoo_
- Add `Microsoft.Azure.Functions.Worker.Extensions.OpenApi` pkg to fn project
- Configure builder
    ```C#
    new HostBuilder()
        .ConfigureFunctionsWorkerDefaults(worker => worker.UseNewtonsoftJson())
        .ConfigureOpenApi()
        .Build();
    ```
- Add attribs to the endpoint handler: OpenApiOperation, OpenApiSecurity, OpenApiParameter, OpenApiResponseWithBody
- Adds Swagger and 3 other OpenAPI endpoints
- Add a configuration class deriving from DefaultOpenApiConfigurationOptions to manipulate defaults (title, OpenAPI schema version, etc.)
- Add a UI configuration class deriving from DefaultOpenApiCustomUIOptions to customize swagger UI (css, custom javascript, etc)
- https://aka.ms/try-azfunc-openapi
- https://aka.ms/azfunc-openapi-docs

### Day 2 - 22:00 Extreme Architecture Performance
_Oren Eini_
- LINQ is horrible for extreme performance scenarios because of allocation overhead and then GC
- They don't allow LINQ in any hot spot code
- Scenario 1: Routing
    - Identify and embrace acceptable limitations
        - Example: ascii-only routes allow throwing out extra logic for unicode
        - Example: dictionary using case-sensitive is hugely superior to case-insensitive; so just memoize the response based on the case-sensitive request path, using more memory overall but drastically reducing the behind-the-scenes logic
    - Consider sections of code that should do no allocations
- Scenario 2: Date formatting
    - dateTime.ToString() is very expensive, allocation-wise
    - They used custom code, some derived from DateTime.ToString, which only supports their one date format, 5x faster
- Scenario 3: small perf changes all the time but eventually hit a wall, so change architecture
    - 37K json file, could deserialize into 500K object
    - 40% of time writing time was just on escaping the strings for json
    - They changed to a custom binary format internally that they call Blittable, based on unmanaged memory; allows random access, pointer arithmetic access, no parsing, zero cost once loaded, self learning
    - Context will retain knowledge of parsing behavior and is reusable, making it faster over time
        - Each context has its own unmanaged memory so "GC" of its data is simply moving the pointer back to the start
    - If the thing you are coding is predictable, rolling your own can provide significant perf improvements at the cost of working with and self-managing unmanaged memory
    - Use a zero copy model
        - Buffering is complex so mmap your datafile, allowing data paging and buffering to be managed by the OS/kernel
    - Take direct ownership of memory when it makes sense (easiest)
    - Find out what's actually going on behind the scenes so you can modify your code to take advantage of it

### Day 2 - 22:30 Developing and Deploying a Static Blazor Web App with Azure Functions Backend
_Matthias Koch_
- `swa` client app to tie them together locally for dev/debugging, including auth emulation: npm `@azure/static-web-apps-cli`
- Plug for Nuke which is essentially C# make, allowing to automate all the stuff you would do to deploy and manage your SWA

### Day 2 - 23:00 Connecting gadgets to Blazor
_Jimmy Engström_
- Lib to not have to work in JS: `Blazm`

### Day 2 - 23:30 Practical tips to elevate your UX and accessibility
_Jessica Engström_
- It's _all_ UI, with UX being how you use it; can't "add" UX as an after thought
- Cognitive overload makes users frustrated and/or slow; less choices or smaller chunks (think CC# in blocks of four)
- Labels to the left of input box doubles the amount of user processing; use labels on top
- Don't just use a template; only ask for what you actually need
- Other examples: full name instead of first and last; DOB to one input instead of three, etc.
- Use multiple pages
- Keep the button to proceed on the same vertical line as the input boxes; this makes it less likely to be missed if the user is using a screen magnifier
- Use color and symbols to indicate success for each input box
- Display the error before the user submits the form; not in a long list; and show them where the error is.
- Don't be vague on validation messages (e.g., "format error").  Show the user the required format (e.g., "MM/DD/YYYY").  And don't blame the user.
- Always have an exit and ability to go back
- Use a contrasting color for input boxes
- Tell the user what they can do to correct (or wait out) a problem (e.g., no "catastrophic failure" or "null [null]")
    - Plain language, avoid technical terms
    - Actionable (buttons, links, etc. to get out of this situation)
    - Keep it short
    - Give a solution
    - Be humble - never put the blame on the user
- WebAIM (web accessibility in mind)
    - Annual analysis of top 1M web pages
    - Average of 887 elements on home page; 6% of users have a visual disability; they would have an issue ever 17 elements
    - Uses Web Accessibility Initiative (W3C's WAI)
        - Concepts work for non-web apps too
    - 97.4% of web pages had accessibility issues; most are from six categories
        - Low contrast text (avg 31 _per page_)
            - 1:1 is white on white; 21:1 is black on white
            - Red on white is 4:1
            - Blue on white is 8.6:1
            - Minimum recommendation for AA is 4.5:1 (e.g., light gray on white)
            - AAA rating is 7:1 (e.g., darker gray on white)
            - Her favorite is 15.55:1, ~ light tan on dark brown
            - Use browser tools to emulate different disabilities
            - Use contrastchecker.com
            - Use color.adobe.com
            - Lots of other tools
        - Missing alt text for images
            - 30% have issues
            - Some use unhelpful tags like "image" or ""
            - Don't be redundant: don't repeat a caption or use "image of..."
            - Be accurate
            - Be succinct
        - Missing for input labels
        - Empty links
        - Missing doc language
        - Empty buttons
- Some users may have temporary conditions which emulate disabilities so don't rule them out; you can't do it all but don't purposefully exclude something just because "none of our users would have that issue"

## Day 3 - 2021-11-11
### Day 3 - 00:00 Running .NET Workloads on IBM Z
_Ulrich Weigand_

### Day 3 - 00:30 Building A Production Ready Blazor WASM App
_Steve Peirce_
- Get rid of the "loading" screen: change `render-mode="WebAssemblyPrerendered"`
- Use persisted data first, then fetch the latest data, so there are no flashes after data comes back from server
- Register an injected record/class that is different in server and client so components can make decisions about how they render
- Write tests with Bunit
- Use `ErrorBoundary`
- Reduce download size

### Day 3 - 01:00 What’s new in bUnit for .NET 6
_Egil Hansen_

### Day 3 - 01:30 SAFE Stack: The Pit of Success for Functional Web Programming
_Isaac Abraham_

### Day 3 - 02:00 Drawn controls in .NET MAUI
_Javier Suárez Ruiz_

### Day 3 - 02:30 JavaScript frontend development with ASP.NET Core in .NET 6
_Javier Calvarro Nelson Calvarro Nelson_

### Day 3 - 03:00 OpenTelemetry with Minimal APIs in .NET 6
_Andrea Tosato, Marco Minerva_

### Day 3 - 03:30 Welcome to Maui Community Toolkit
_Pedro Jesus, Gerald Versluis_
- Porting all converters/behaviors from XCT (except stuff that is already in MAUI), but not all controls
- MAUI compat toolkit is available for MAUI development to still use XCT until MCT has it
- https://aka.ms/maui-toolkit

### Day 3 - 04:00 Blazor and GraphQL
_Poornima Nayar_
- http://bit.ly/blazor-graphql

### Day 3 - 04:30 Understanding Microservices: a guide for the monolithic developer
_Layla Porter_
- Libraries
    - Steeltoe
    - DAPR
    - Project Tye
    - YARP


### Day 3 - 05:00 Creating NFT with .NET
_Sebastián Leonardo Pérez_

### Day 3 - 05:30 30 minutes of Testing in .NET
_Michael Dera_

### Day 3 - 06:00 Modern .NET Messaging using MassTransit
_Chris Patterson_

### Day 3 - 06:30 Zero to Hero with GitHub CodeSpaces
_Rory Preddy_

### Day 3 - 07:00 Azure Percept : IoT and AI at the Edge
_Carey Payette_

### Day 3 - 07:30 Raspberry-Pi hand sanitizer controlled by Mobile Apps
_Saamer Mansoor_

### Day 3 - 08:00 Learn Live | Create a web UI with ASP.NET Core
_Jon Galloway, Maira Wenzel_

### Day 3 - 08:30 Learn Live | Build your first microservice with .NET
_Matt Soucoup, Nish Anil_
- https://aka.ms/dotnet-conf-microservice
- https://aka.ms/learn-live-microservices

### Day 3 - 09:00 Response and Adaptive Tactics for Blazor Applications
_Ed Charbeneau_
- Auth of _Blazor: A Beginner's Guide_ (free)
- Blazor hybrid runs within MAUI (see CODE mag's .net 6 issue)
- Layout frameworks (Bootstrap, tailwindsss) are becoming less useful because modern CSS can do most of it
- [Post](https://edcharbeneau.com/blazor-layout-components) for native UI devs moving to CSS
- [Telerik REPL for Blazor](https://blazorrepl.telerik.com/)
- CSS Grid
    - two dimensional
    - `display: grid`
    - `gap` solves the padding/margin issues between items
    - `grid-template-columns` uses fractional values such as `3fr 5fr` to denote 3/8 for col1, 5/8 for col2
    - `grid-auto-rows` to govern the height of rows in a repeating pattern such as `2fr 1fr` for odd rows being twice as tall as even ones
    - dev tools can show the actual grid for ui debugging
- CSS Flexbox
    - one-direction flow layout system
- `::deep` selector for top-most in component?
- Media queries
    - `BlazorPro.BlazorSize` package he wrote for detecting media size in blazor, with events, etc.

### Day 3 - 09:30 Clean Architecture with ASP.NET Core 6
_Steve Smith_
- Architecture names: Onion, Hexagonal, Ports and Adapters
- Clean architecture:  UI -> Domain/Business/Core <- Infrastructure (inc. data access) -> DB
- Rules
    1. Model all business rules and entities in the Core project (validation can be duped)
    2. All dependencies flow _toward_ the Core project (everything depends on Core)
    3. Interfaces defined in the Core
- Belongs in Core
    - Interfaces
    - Entities (things with IDs)
    - Aggregates (DDD grouping of entities)
    - Value Objects (no IDs, compare via their properties like DateTime, include validation in the ctor)
    - Domain services (if not in above)
    - Domain exceptions (rather than generic exceptions)
    - Domain Events (DDD)
    - Event Handlers (maybe some elsewhere)
    - Specifications (query logic out of repos into domain model; `Ardalis.Specification` pkg)
        - Reusable, testable
    - Validators
    - Enums
    - Custom guards (validators to make sure system is in consistent state, `Ardalis.GuardClauses` pkg)
    - [Demo code](https://github.com/ardalis/CleanArchitecture)
    - `dotnet new -i Ardalis.CleanArchitecture.Template` to install `clean-arch` solution template
    - Group things according to the aggregate with subfolders for categories (similar to our endpoints)
- Infrastructure
    - Repositories
    - DbContext classees
    - Cached repos
    - API clients
    - File system or cloud storage accessors
    - Email/sms implementations
    - System clock
    - Other services
    - Interfaces that don't use domain model (e.g., Azure-specific stuff)
    - Infrastructure modules to contain DI, etc.
- Web
    - API endpoints
    - Razor pages
    - Controllers (prefer above)
    - Views (prefer above)
    - API and view models
    - Filters
    - Model binders
    - Tag helpers
    - Composition root
        - Entry into app
        - interface IBlah is implemented by Blah
        - startup.cs or program.cs
    - Other services
    - Interfaces (UI specific for included types)
    - Endpoints
        - One file per operation with request and response subfiles (Endpoints/ProjectEndpoints/Create.cs, Create.CreateProjectRequest.cs, Create.CreateProjectResponse.cs)
- Shared Kernel (DDD)
    - Holds common types shared between DDD apps
    - Typically referenced by Core project(s)
    - Ideally distributed as NuGet pkgs
    - Base entities, value objects, domain events, specifications
    - Common interfaces, exceptions
    - Common auth
    - Common guards
    - Common libraries (DI, Logging, Validators)
    - NO infrastructure dependencies
- Resources
    - [Architect Modern Apps with ASP.NET Core and Azure eBook](https://dotnet.microsoft.com/learn/web/aspnet-architecture)


### Day 3 - 10:00 OSS NuGet Package Explorer: From WPF to WinUI and running in Browser
_Jérôme Laban_

### Day 3 - 10:30 Machine Learning for .NET developers
_Veronika Kolesnikova_

### Day 3 - 11:00 Real World Minimal APIs
_Shawn Wildermuth_
- Big gap/difference between controller APIs and minimal APIs
    - For prototypes or microservices, minimal is great
    - Controller apis for more complex things like versioning, auth, etc.
- No best practices yet
    - Minimal apis give you more control but that may not be good

### Day 3 - 11:30 A primer on FeatureManagement APIs in ASP.NET Core
_Santosh Hari_

### Day 3 - 12:00 Embedding Power BI Reports in your Blazor 6 site
_Édgar Sánchez Gordón_

### Day 3 - 12:30 Cross Platform Database Support On Overdrive
_Shaun Walker_

### Day 3 - 13:00 Using, and creating, custom project templates in Visual Studio and the dotnet CLI
_Sayed Hashimi_

### Day 3 - 13:30 Building High Performance Systems with Akka.Streams
_Aaron Stannard_

### Day 3 - 14:00 Using Source Generators for Fun (and Maybe Profit)
_Jason Bock_

### Day 3 - 14:30 Bringing Your Apps to Windows 11 on ARM
_Jeremy Sinclair_

### Day 3 - 15:00 Deploy an application for Azure Container Registry
_Rebai Hamida_

### Day 3 - 15:30 How the Community Toolkit streamlines development of Microsoft built apps and your apps alike!
_Michael Hawker, Justin Liu_

### Day 3 - 16:00 Host, deploy and scale ASP.NET Core Blazor Server
_Jose Javier Columbie_

### Day 3 - 16:30 Supercharging your cloud applications with Orleans
_Reuben Bond_
- Grains == virtual actors
- Features
    - Persistencew
    - Distributed ACID transactions
    - Virtual streams (pub/sub, events)
    - Timers & reminders
    - Observers (push notifications, streams)
    - Transport layer security
    - All the platforms, OS, cloud
    - Custom placement and directory
    - Call filters (AOP for logging, tracing, error handling)
    - .NET's DI, logging, hosting, configuration; networking built on Project Bedrock
- https://aka.ms/orleans-samples
- https://github.com/dotnet/orleans
