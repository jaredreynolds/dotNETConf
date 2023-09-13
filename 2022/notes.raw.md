# [.NET Conf 2022](https://www.dotnetconf.net/)
- [YouTube playlist](https://www.youtube.com/playlist?list=PLdo4fOcmZ0oVFtp9MDEBNbA2sSqYvXSXO)
- [Slides/code](https://github.com/dotnet-presentations/dotNETConf/tree/master/2021/MainEvent/Technical)

## Day 1 - 2022-11-08

### Day 1 - 08:00 Keynote - Welcome to .NET 7
_Gaurav Seth, Scott Hunter, Safia Abdalla, Julia Kasper, David Fowler_
#keynote

- Top performer for gRPC
- Simpler minimal API
  - Route groups
  - "Two" lines for Az auth
- Demo 1
  - routes.MapGroup() to create a group of routes with a common URI base
  - rate limiting .AddRateLimiter
  - Swagger
    - Auth button
    - `dotnet user-jwts` tool to create tokens
- Demo 2
    - Az API management
    - Az Power Apps
- `return TypedResults.Ok($"blah {id})`
- Dev Tunnels
    - Create a publicly accessible endpoint to their local machine
- Upgrade via YARP to do it piecemeal
- .NET Upgrade Assistant
- Cloud Native
    - App of the future
    - 60% of devs use containers
    - Chiseled Ubuntu containers ~50% size
        - secure, no shell, no root, no package manager
        - quicker to start
    - .NET updates go directly to Conical builds, avoiding zero days
- ARM64 perf same or better than X64
- Containers
    - `dotnet publish` directly to container
    - Docker, containerd, podman, etc.
- Container Demo
    - No external tools, built in to .NET SDK
    - Microsoft.NET.Build.Containers (temporary workaround)
    - Can build, tag, and publish to registries as part of build
    - Full Docker support now, more coming
    - No Dockerfile required?!
    - It builds the GH Actions for you too!
- Az App Insights Demo
    - `.AddOpenTelemetryMetrics()`
    - Sidecar `dotnet monitor` to see what is going wrong
    - Send core dumps to "S3"
    - Analyze dump in VS
- New way to run containers:  Azure Container Apps - managed kubernetes
- Blazor for reach; MAUI for depth; or hybrid in the middle
- VS 17.4 - .NET 7 and C# 11, full ARM64 support, deep cloud dev tools

### State of ASP.NET Core
_Daniel Roth_
#web #minikeynote

- ASP.NET Core - 11x faster the node
- Faster HTTP/2, gRPC 8x faster
- Optimized for more cores - 5x faster for 80 core VMs
- HTTP/3
- WebSockets over HTTP/2
- WebTransport (experimental)
- ARM64 support for IIS
- Endpoint groups
- Endpoint filters for AOP
- Simplified auth
- Demo
    - Wait, classes in top-level code?!
    - `TypedResults`, explicit, easier to test, better Swagger
    - Return `Task<Results<Ok<Todo>, NotFound>>` - aggregate return type for Swagger
    - `MapGroup().RequireAuthorization()`
    - Still have a bunch of code for Authorize button
- Blazor
    - Custom elements: Blazor components in JS apps
- Incrementally upgrade to ASP.NET Core
    - YARP proxying to old app

### What's new for Blazor in .NET 7
_Steve Sanderson_
#web

- `<EditForm>` - not new, but new to me
- `NavigationLock` to prompt the user before losing changes on nav

### Making the Most of Minimal APIs in .NET 7
_Safia Abdalla, Stephen Halter_
#web

- `.AddEndpointFilterFactory()` - gets access to context for DI services, etc
    - Can be called on individual endpoints or on a route group
- Route groups don't yet support middleware
- `.AddAuthorizationBuilder()` to add policies
- Swashbuckler config .InferSecuritySchemes()
- `.EnableOpenApiWithAuthentication()`
- dotnet userjwts is customizable, including 
- XML output
    - IEndpointMetadataProvider - reflection for your route handler

### Building modern high-performance services with ASP.NET Core and .NET 7
_Sebastien Ros_
#web

- HTTP/2 is drastically faster 3x-40x; use .NET 7 if you are doing HTTP/2
- HTTP/2 and 1 are now the default protocols (no config required)
- HTTP/3
    - QUIC, UDP instead of TCP
    - Experimental, supported in Chrome, Edge, Firefox, Opera (Safari is opt-in)
    - Perf improvements
    - WebTransport
        - Multiple indepentent streams on one connection, so dropped frames on one don't affect the others
    - Rate Limiting
        - Can limit based on user (e.g., subscription levels)
        - Lease
            - Fixed
            - Sliding
            - Concurrency limit - probably good to enable globally
            - Token bucket limit
            - Partitions limits per custom values (user, IP, etc.)
    - Output caching
        - Replaces other middleware
        - Extensible cache stores (memory, disk, etc.)
        - Invalidate tagged cache entries
        - UseOutputCache after limit vs before limit

### State of Azure + .NET
_Scott Hunter_
#cloud #minikeynote

- Use Dapr to make your code portable - works in all clouds, 107+ backends
- .NET 7 is available everywhere
- Use Polly:  https://learn.microsoft.com/en-us/dotnet/architecture/microservices/implement-resilient-applications/implement-http-call-retries-exponential-backoff-polly
- Dapr for .NET devs:  https://learn.microsoft.com/en-us/dotnet/architecture/dapr-for-net-developers

### The Whirlwind Tour of Building .NET Apps in Azure
Matt Soucoup
#cloud

- https://aka.ms/dotnetconf/whirlwind

### Building Serverless Applications with .NET 7 and Azure functions
_Melony Qin, Fabio Cavalcante_
#cloud

- Isolated model
    - Worker process
        - https://aka.ms/af-dotnet-isolated-guide
        - Decoupled from host .net versions, can now run whatever .net version
    - Other improvements to get closer to in-proc experience
        - Better perf
        - Durable fns (preview)
        - SDK type bindings
        - Enhanced http trigger
        - https://aka.ms/af-dotnetIsolated-enhancement
    - Migration Guides to Azure Functions 4.0
        - from v3: https://aka.ms/v3-af-dotnet-migration
        - from v1: https://aka.ms/v1-af-dotnet-migration
    - Eventually, it will be isolated only, depending on parity

### Azure Container Apps with .NET
_Mike Morton, Anthony Chu_
#cloud

- Free level
- Dapr support builtin
    - Integrates with App Insights (really cool App Map)
- https://aka.ms/containerapps
- In the end, very comparable to Az Fns, including idle pricing
- Vs. AKS - CA is Managed AKS; ability to switch between them because they are just containers
- Dapr enables being able to run your app locally

### State of .NET MAUI
_David Ortinau, Maddy Montaquila_
#client #minikeynote

### What's new in .NET MAUI and Desktop Apps
_Shane Neuville_
#client

### Performance Improvements in .NET MAUI (.NET 7 edition)
_Jonathan Peppers_
#client

### Create native desktop & mobile apps using web skills in Blazor Hybrid
_Eilon Lipton, James Montemagno_
#client

### How Halo, Dynamics 365, and Mesh scale to millions with Orleans and you can too!
_Brady Gaster, Reuben Bond_
#devstory

- Version bumped from 3 to 7 to reflect its close affiliation with .NET (perhaps part of .NET someday)
- https://learn.microsoft.com/dotnet/orleans

### What's New in C# 11
_Mads Torgersen, Dustin Campbell_
#deeperdotnet

- `required` properties - no more squiggles if no ctor; also applies to attributes
    - [SetsRequired] on ctor to override
- `where T : INumber<T>` composed of many other interfaces for all the maths
- static properties on type params (`T.Zero`)
- static interface members (including virtual, abstract, and checked)
- IParsable<T> - Parse and TryParse static methods with string parameter, TSelf
- Pattern matching
    - List patterns
        ```
        values switch {
            [] => T.Zero,
            [var first] => first, // not needed
            [var first, .. var rest] => first + AddAll(rest)
        }
        ```
- raw string literals - no escapes """<element attr="">""" (or any number )
    - can be multiline but endfix must be on a separate line; indent postfix to trim the indenting!!
    - interpolation too

### Performance Improvements in .NET 7
_Stephen Toub_
#deeperdotnet

- Lesson 1: Find Ways to Have Your Cake and Eat It, Too
    - Tiered compilation in .NET Core 3.0 - tier 0 JIT compilation has less optimization but very fast; then it can watch how it is used and recompile with more optimizations
        - disabled for methods with `for` loops
    - .NET 7 now can do the loops
    - DOTNET_JitDisasmSummary=1 to see what it's doing
    - DOTNET_JitDisasm="Main" to see everything about Main
- Lesson 2: Don't Make Everyone Duplicate Efforts
    - Reflection invoke has expensive overhead
        - worked around this with reflection emit
        - now it's built in
- Lesson 3: CS research is on-going
    - Go back on previous 
    - RegExOptions.NonBacktracking - hugely faster on some difficult regexs, can be slower but is consistent
- Lesson 4: Built-in helpers are your friends
    - "index of" perf improvement makes everything else faster
- Lesson 5: Work-arounds Should be Revisisted
- Lesson 6: There's Always More Opportunity to Optimize
    - More methods on RegEx to do specific things, including Spans
- Lesson 7: Be ThoughtFul About Your Defaults
    - Usually pick defaults for the average case
    - Need to revisit those decisions because of other optimizations
    - Brotli compression default time was horrid; dropped default down so it is hugely faster, but slightly less compression
- 20% of perf improvements were from outside the team (i.e., open source)

### Let's design a new C# language feature!
_Jared Parsons_
#deeperdotnet

- The problem: code generator for Regex produces "private" classes that are "public"
- The proposed solution: allow `private` classes to be local-only to the file
- Is `private` the best word?
    - several iterations came down to `file`
- How do other languages do it?
- What are the core properties?
- Can we generalize this?
- Is the cost proportionate to the benefit?

### Let's design a new C# language feature!
_Jared Parsons_
#deeperdotnet

### .NET ❤️’s WebAssembly in .NET 7
_Daniel Roth_
#blazor

- Better debugging and perf
- Experimental multithreading! using web workers

### Build an Audio Browser app with Blazor
_Steve Sanderson_
#blazor

- https://github.com/SteveSandersonMS/AudioBrowser

### Testing Blazor Applications with Playwright
_Debbie O'Brien, Max Schmitt_
#blazor

- Writes all your selectors for you
- Runs webkit on Windows (in addition to FF and Chromium)

### GitHub Universe + .NET Conf Epic Crossover
_Scott Hanselman_
#github

- 60 free hours of GitHub Codespaces
- Private CVE reporting available 

### Microsoft Dev Box and Azure Deployment Environments for .NET Developers
_Anthony Cangialosi_
#github



### High-performance services with gRPC: What's new in .NET 7
_James Newton-King_
#modernization

- Testing
    - Postman can now do gRPC
    - Use GrpcReflection pkg to set up the server to serve proto
    - gRPC Web UI - open source
    - grpcurl - command line
- Perf improvements
- New
    - gRPC JSON transcoding 
        - both gRPC and JSON/REST at the same time
        - Microsoft.AspNetCore.Grpc.JsonTranscoding
        - Add swagger with Microsoft.AspNetCore.Grpc.Swagger
    - Fully supported on Azure App Service
        - App Service now uses YARP
- https://aka.ms/grpcdocs



### CSS Techniques for Blazor Developers
_Ed Charbeneau_

- Install Dart Sass via `[choco|brew] install sass` then `sass ./input.scss ./output.css`
    - alt `npm nstall -g sass` then `npx sass ...  ` - significantly slower
- No webpack, no WebCompiler extension (no longer supported)
- MSBuild
    ```
    <Target Name="BuildCssDev" Condition-"'$(Configuration)' == 'Debug'" AfterTargets="Build">
        <Exec Command="sass ./Theme/app.scss ./wwwroot/app.css" />
    </Target>
    <Target Name="BuildCssProd" Condition-"'$(Configuration)' == 'Release'" BeforeTargets="Build">
        <Exec Command="sass ./Theme/app.scss ./wwwroot/app.css" />
    </Target>
    ```
    - For hot reload, use sass -watch
- His pkg:  BlazorComponentUtilities
    - CssBuilder
- CSS Custom Property == variable
    ```
    :root {
        --public-color: blue;
    }
    .component-scope {
        --private-color: var(--public-color, white);
    }
    .element {
        color: var(--private-color)
    }
    <div class="element" style="--private-color: orange;">
    ```
    white is default
- Tailwind free/commercial ($ components/templates)
- Bootstrap free ($ themes)
    - switching to css vars in v5
- Telerik UI for Blazor $
- Resources
    - EdCharbeneau.com



### 20:30 Migrate Your Legacy ASP.NET Projects to ASP.NET Core Incrementally with YARP
_Jonathan "J." Tower_

- MS Project Migrations VS extension

### 21:00 MVVM is easier than ever before with Source Generators, .NET 7, and the MVVM Toolkit
_Sergio Pedri_


### 23:30 Human-readable Razor views with ASP.NET 7 Tag Helpers
_Dino Esposito_

- `TagHelper`
- `HtmlTargetElementAttribute`
- Write the HTML in the Process method: `output.Content.AppendHtml()`
    - 
    ```
    output.TagName = "div"
    output.Attributes.Clear();
    ...SetAttribute()
    ShowOutput??
    ```
- Enum values must match exactly
- Use context.Items to store things you want to share with child objects
- Not easy to debug; all changes require a rebuild


### 01:30 Authorization in a Distributed / Microservice System
_Halil İbrahim Kalkan_

- Create an authorization library that each microservice uses
    - pro
        - decouple authorization logic from the microservice library
        - application data is available for "row level" authorization
        - custom authorization logic is possible
    - con
        - can't support microservices on different platforms
- In UI, get a list of all the user's permissions so you can customize the UI without having to ask the authorization service each time
    - User permissions UI also needs all of them
- Store all permissions in a central database, connected via authorization library
- Calculate permissions in a central permission management service
    - Ideal for on/off style permissions with minimal dependencies to microservice internals
- Use unique permission names (localized in UI)
- DB stores groups, definitions, and grants
- Filtering with permissions
    - let the db do it
- For custom and resource-based permissions, UIs should get that info from the related microservice


### 03:30 Using Durable Azure Functions in .NET 7
_Niels Filter_

- Chained workflows - await single
- Fan out - await all
- Events & timers - await any for an event with timeout

### 04:00 Performance tricks I learned from contributing to the Azure .NET SDK
_Daniel Marbach_

- Avoid excessive allocations to reduce the GC overhead - think twice before using LINQ or unnecessary enumeration on the hot path
- Always measure before and after optimizations - Another plug for benchmark.net
- LINQ to collection-based operations
    - Use Array.Empty<T> to represent empty arrays
    - Use Enumerable.Empty<T> to represent empty enumerables
    - Prevent collections from growing
    - Use concrete collection types
    - Leverage pattern matching or Enumerable.TryGetNonEnumeratedCount
    - Wait with instantiating collections until really needed
    - However, non-materialized collections probably make things slower
- Avoid excessive allocations to reduce the GC overhead
    - Be aware of closure allocations
        - Use static lambdas and overloads that allow passing typed state (not object - boxing)
        - How to detect?
            - Use memory profilers and watch for excessive *__DisplayClass* or variants of Action* and Func*
            - Use tools like Heap Allocation Viewer (Rider) or Heap Allocation Analyzer (VS)
    - Pool an re-use buffers (and larger objects)
        - rent from ArrayPool - may be slower but less memory...just depends on use case
    - For _small_ local buffers, consider using the stack - faster and still no allocations
        - `Span<byte> guidBytes = stackalloc byte[16];`
        - Read stackalloc docs before you do this
    - Be aware of parameter overloads [not covered]
    - Where possible and feasible, use value types but pay attention to unnecessary boxing [not covered]
    - Move allocations away from the hot-path where possible [not covered]
- Avoid unnecessary copying of memory [not covered]
    - Watch out for immutable/readonly data that is copied
    - Look for Stream and Byte-Array usages that are copied or manipulated without using Span or Memory
    - Replace existing data manipulation methods with newer Span- and Memory-based variants
- At scale, implementation details matter
    - Tweak expensive IO operations first
    - Pay close attention to the context of the code
    - Apply the principles where they matter
    - Everywhere else, favor readability
- github.com/danielmarbach/PerformanceTricksAzureSDK


### 06:00 ASP.NET Basics for Experts
_Layla Porter_

- Add `public partial class Program { }` to Program.cs to be able to test it

### 06:30 .NET Configuration In Depth
_Chris Ayers_

- .ValidateDataAnnotations, .Validate after BindConfiguration

### 07:00 Networking in .NET 7.0
_Karel Zikmund_

- HTTP/3
    - better for unreliable connections, not server to server
    - Multipath increase bandwidth or decrease latenency
    - Roughly on par with HTTP/2 for perf, better in 8.0
    - QUIC - API shape is still in preview <EnablePreviewFeatures>
    - To use
        - Client: `HttpRequestMessage.Version = HttpVersion.Version30`
        - Kestral: ListenOptions.Protocols
    - 8.0
        - mac and mobile support
        - gRPC
- HTTP/2 WebSockets
    - Same just over HTTP/2, reuses connections for better perf
    - `SocketsHttpHandler`, `ClientWebSocket.Options.HttpVersion`
    - server:  connect, not get, not in 7 but can add the code yourself (3 lines)
    - 8: WebTransport (WS done right)


### 08:00 Building .NET apps on WSL
_Scott Hanselman_
#linux

- <PublishAot>true</PublishAot> for native compilation
- `$Env:DOCKER_HOST='npipe:////./pipe/podman-machine-default'` to use podman for publishing to it

### 08:30 Using .NET with Chiseled Ubuntu Containers
_Richard Lander, Valentin Viennot_
#linux

- Prod should be a chiseled slice of dev
- Package slices grab just the pieces of the packages that are needed; ecosystem needs to be enlarged and process needs to mature
- reduce attack surface, non-root user
- `-chiseled` images are currently only in nightlies
- Published port is 8080, because 80 is a root port


### 09:30 Leveling up data: Upgrade from EF6 to EF7 and blast off!
Arthur Vickers, Shay Rojansky
#data

- ExecuteUpdateAsync and ExecuteDeleteAsync can now be used to just do those actions on the server--you don't need to bring anything back to the client
- JSON support in SQL is good; basics work in PostgreSQL and MySQL (will be parity in v8)


### 12:30 Clean Architecture with ASP.NET Core 7
_Steve Smith_

- Clean architecture
    - Onion, Hexagonal, Ports & Adapters
    - A domain-centric approach to organizing dependencies
    - Dependance on infrastructure concerns is minimized; keeping focus on domain logic
- For certain types
    - Practicing DDD and want focus on domain model, not infrastructure
    - Complex business logic warrants highly testable architecture (not just CRUD)
    - Want architecture to help enforce policies, rather than relying on contributors to consistently do the right thing
        - Similar to strong types or field visibility constraints
- UI, Infrastructure, and Tests depend on Domain/Core; Infra also depends on DB/etc
- Nuget: Ardalis.CleanArchitecture.Template; dotnet new clean-arch
- Specifications pattern: data access + repo without adding extra repo classes all the time
- Abstract access to system clock in Infrastructure
- RER - Request Endpoint Response pattern??
- Resources
    - eShopOnWeb sample
    - Architect Modern Apps with ASP.NET ore and Azure eBook: https://dotnet.microsoft.com/learn/web/aspnet-architecture


### 13:30 Azure Static Web Apps with Blazor and .NET
_Melissa Houghton_

- Static Web Apps CLI
- Backend
    - Az Functions
- Backends in preview
    - Az API Management
    - Az App Service
    - Az Container Apps
- Enterprise-Grade Edge
    - SWA + Front Door + CDN
- Auth: AzAD, GH, Twitter, custom
- Link to backend is on standard (non-free) plan
- MudBlazor - material design components
- aka.ms/SWA-Blazor

### 14:00 Building Accessible Apps with .NET MAUI
_Rachel Kang (SHE/HER)_

- SemanticProperties.Description, .Hint, .HeadingLevel
- Extensions: .SetSemanticFocus(); SemanticScreenReader.Announce("")
- MAUI Community Toolkit: SemanticEffects (migration), SemanticOrderView (screen reader nav order)
- App theming
- FontAutoScalingEnabled - defaults to true
- Built-in accessibility: TapGestureRecognizer, checkbox on iOS renders as switch
- Customization via Handlers (sit between native views/controls and virtual view/controls)
- Built to match Microsoft's Accessibility Standards
- Accessibility Insights (Win and Android)
