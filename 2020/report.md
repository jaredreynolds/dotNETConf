# [.NET Conf 2020](https://www.dotnetconf.net/)
- [YouTube playlist](https://www.youtube.com/playlist?list=PLdo4fOcmZ0oVWop1HEOml2OdqbDs6IlcI)
- Slide decks provided by presenters will hopefully show up in the GitHub [repo](https://github.com/dotnet-presentations/dotNETConf/tree/master/2020/MainEvent/Technical).

## My Top Takeaways
- We need to officially decide if moving to .NET 5/6 makes any business sense.
- We should invest time into making our libraries multi-targeted.  That gives us a better idea of what needs to be fixed in consumers while keeping the plane in flight.
- Blazor Web Forms Components (community OSS) could be a viable path forward for many controls/pages.  But we have a lot of code-produced and/or complex controls that would take heavy effort (e.g., grids).

## New/Hot Tech
- .NET 5.0
- C# 9.0
- VS 2019 16.8 (supports all this stuff)
    - Solution filters
- Blazor (2-3x faster for WASM)
- gRPC (big perf improvements)
- Kubernetes / Project Tye "preview"
- CodeSpaces "preview"
- Blazor Web Forms Components

## My Selected Favorite Sessions

### Keynote - Welcome to .NET 5  -  Scott Hunter
- "Core" dropped from the name.
#### Highlights
- Blazor now uses core BCL instead of mono
- Full swagger support (OpenAPI)
- ClickOnce is back (and better)
- Windows ARM64 support
- Self-contained, single exes
#### Developers love .NET "Core"
- #1 favorite platform for 2019 and 2020
- Top 30 highest velocity OSS
- Top 5 in GH
- One of the fastest frameworks; large perf gains over .NET Core 3.1
- gRPC implementation is faster than go, c++, and java
#### VS2019 16.8
- Out today
- .NET 5 and roslyn analyzers included
- New git experience
- Linux debugging
- Publish direct to GH Actions
#### Blazor
- The move to run on .NET 5 instead of mono is the beginning of ONE .NET (Xamarin to move too)
- WASM is now 2-3x faster
- Can prerender so startup is very fast
- Now supports data windowing virtualization
- Razor components can include their own css without any effort
- Live refresh ("dotnet watch" from command line, too)
#### Cloud native investments
- OpenAPI (Swagger via Swashbuckle) built in, just click checkbox
- Webapi app F5 now goes to swagger ui rather than blank page
- Integration with HttpRepl
#### Project Tye
- In preview, shipping in .net 6
- Service discovery
- Dependencies without docker files (not running on your machine)
- Run and debug locally using containers and kubernetes
- Local dashboard for metrics, logging, debugging
- Easy publishing to azure
#### Coming
- Xamarin on .NET 6 instead of mono
- MAUI - cross-platform native ui
- Blazor desktop - cross-platform web ui
- .NET 6 is LTS, Nov 2021
    - Intent is that you can easily migrate from non-lts to lts

### What’s New in C#?  -  Mads Torgersen   Dustin Campbell  
- main() and namespace declaration can be removed in console apps
- init: property is settable until end of object initializer
    ```c#
    public double Gpa { get; init; } = 4.0;

    new Class1 { Gpa = 3.3 }; // readonly afterwards
    ```
#### Records
- Single keyword, readonly DTOs (from functional programming)
- Non-destructive mutation (new copies for updated objects): records
    - `record Person { prop... }`
    - shallow copy-mutate using `with` keyword: `var otherPerson = person with { LastName = "Hanselman" };`
- Shallow equality (like struct value equality)
- Copy/equality are based on the runtime type (not base record)
- Constructor will auto-create properties with parameter names
- Everything is just classes under the hood so they generally work wherever classes could be used
#### Patterns
- `and`, `or`, `not` between switch patterns

### A talk for trailblazers: Blazor in .NET 5  -  Steve Sanderson   Safia Abdalla  
#### Improve dev experience
- CSS isolation: `Index.razor.css`
    - no need to declare globally unique class names
    - even element selectors
- Packages can add their own css/js
- Better debugging
- InputFile component for file uploading
- Virtualization:  `<Virtualize Items="Data" Context="entry">`
- Azure static web apps integration
#### Improve perf on WASM
- 2-4x faster in typical scenarios
- Changes made to Chromium as well (~2x speed improvement)
- Protected local storage
- Browser compatibility attributes for your API methods
- Render modes
    - WebAssembly Prerendered: static html
    - WebAssembly: blazor in mvc
- Lazy loading dependent assemblies

### Porting Projects to .NET 5  -  Immo Landwerth   Phillip Carter  
https://aka.ms/net-porting-docs
#### Understand goals
- Only port projects that you need to innovate in
- Maintenance-only projects can stay on Framework
- Don't make one big port; you gotta keep shipping software
- What would porting give you?
#### Inventory
- `API Port` to get an inventory before
- Drop legacy stuff before
- Look at dependencies to see if they support new
- `dotnet tool install -g apiport`
- `dotnet tool install -g try-convert`
- `apiport analyze -f {dir of assemblies}` (tells you "how compatible")
#### Convert Project
- First step could be to migrate project files to sdk-style but still targeting framework

### High-performance Services with gRPC: What's new in .NET 5  -  James Newton-King
#### What/why
- Largest RPC mindshare
- Cloud Native Computing Foundation project
- HTTP2/Protobuf
- Platform independent
- Contract-first vs. REST/HTTP which are code/content first
- gRPC content is for computers; rest is for humans
#### What's new
- gRPC-Web browser support
    - grpc-web server middleware
    - grpc-web blazor client
#### Perf
- HTTP/2 server allocations reduced by 92% (Kestral)
- HPack response compression
- Requests per second:  Server: 65%, client 220% faster
#### Docs
- https://aka.ms/grpcdocs
- https://aka.ms/grpcexamples

### GitHub + Visual Studio ❤ .NET  -  Vix Rian   Andy Sterland  
#### CodeSpaces - Preview
- base image (Win10, VS, from MS) + `.devcontainer.json` + `.devinit.json`
- don't depend on base image; anything custom needs to be in repo
- devinit is a metatool (task runner?) to install/setup your dependencies
- runners available for sdks, msi, chocolatey, dotnet tools, etc
- `postCreateCommand` in `.devcontainer.json` that executes `powershell...devinit init`
- https://aka.ms/devinit/docs
- https://aka.ms/vs-preview
- Sign up for beta: https://aka.ms/vscs-github
- https://aka.ms/GithubActions-Azure

### What’s New in Visual Studio 2019 and beyond  -  Caty Caldwell  
#### Solution filters ⭐
- On sln open, "Do not load projects" checkbox
- Select projects and then right click, reload project
- Right click solution, hide unloaded projects
- Right click solution, save as solution filter
#### Configurable file nesting
- Icon in solution explorer to enable
- Right click at the level you want to start nesting (sln/proj)
- json file with rules to nest similarly-named files (like different extensions) under each other

### HTTP API Development with .NET, Azure, and OpenAPI: Paper Cuts Begone!  -  Brady Gaster  
#### OpenAPI/Swagger
- Can do anything you want to modify the model/api docs:  like pulling info from xml doc comments!!! 
- Use Name attribute to get good compatibility with various openapi tools
- F5 goes to swagger ui
#### REPL
- microsoft.dotnet-httprepl
- Set that up through browse
- You can then set it as your "browser"
- if you can navigate it like a directory structure, it's probably an okay api structure

### From Web Forms to Blazor - Introducing the Blazor Web Forms Components  -  Jeff Fritz  
- http://bit.ly/blazorwebformscomponents
#### Migration Process
- Move business logic out of aspx/ascx into class libraries.  Both Web Forms and Blazor can then use it.
- Create a new Blazor project
    - Ref class libs
    - Migrate static files
    - Migrate config
- Rewrite aspx/ascx as .razor files
- https://aka.ms/blazor-ebook
#### CodeFactory https://codefactory.software
- Pattern automation tool that uses your src code like a data model
- Build templates that can be automated and attached to VS
- Templates available for refactoring, migrating, and scaffolding
    - Template available aspx -> .razor
