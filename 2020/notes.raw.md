# .NET Conf 2020

## Keynote - Welcome to .NET 5  -  Scott Hunter (note, no "Core")
### Highlights
- Blazor now uses core BCL instead of mono
- Full swagger support (OpenAPI)
- ClickOnce is back (and better)
- Windows ARM64 support
- Self-contained, single exes
### Developers love .NET "Core"
- #1 favorite for 2019/2020, Top 30 highest velocity OSS, top 5 in GH, one of the fastest frameworks
- dotnetthanks.azureapps
- large perf gains over 3.1
- grpc faster than go, c++, and java
#### Demo
- C# 9 has records which provide single keyword DTOs
### Xamarin.Forms 5
- later this year
- Dev iOS apps on Windows with an iPhone
#### Demo
- Hot reload 2.0 is so much faster
### VS2019 16.8
- out today
- .NET 5 and roslyn analyzers included
- New git experience
- Linux debugging
- Publish direct to GH Actions
#### Demo - Codespaces
- .devinit.json sets up all the stuff, very packer-like
- Remote test execution coming
### Blazor
- running on .net 5 core instead of mono, has access to the full thing now
- beginning of ONE .net (Xamarin to move too)
#### Demo
- Server + WASM
- 2-3x faster
- Can prerender so startup is very fast
- Now supports data windowing virtualization
- Razor components can include their own css without any effort
- Live refresh ("dotnet watch" from command line, too)
### Cloud native investments
- OpenAPI (swagger) built in
- client gen
- grpc contract-based apis (WCF)
- smaller container images, single file
- microservice in about 10 lines of code
- YARP
- Azure App Service supports .net 5 today (must config in portal first)
#### Demo
- OpenAPI via checkbox (Swashbuckle)
- Start webapi app goes to swagger ui
- integration with HttpRepl
### Project Tye
- in preview, shipping in .net 6
- service discovery
- dependencies without docker files (not running on your machine)
- run and debug locally using containers and kubernetes
- local dashboard for metrics, logging, debugging
- easy publishing to azure
#### Demo
- "tye run" brings up everything in the right order, etc.
### One .NET vision
- One sdk, one bcl, unified toolchain
- blazor today
- xamarin in .net 6
### coming
- MAUI
- Cross-platform web ui
- 6 is LTS Nov 2021
- intent is that you can easily migrate from non-lts to lts

## .NET Foundation "State of the Foundation"  -  Claire Novotny   Layla Porter  
- aka.ms/dotnet5-CodeMag
- aka.ms/mslearn-dotnet
- aka.ms/dotnetskills - challenges until 11/29

## What’s New in C#?  -  Mads Torgersen   Dustin Campbell  
- main() and namespace declaration can be removed in console apps
- init: property is settable until end of object initializer
    - `public double Gpa { get; init; } = 4.0;`
### Records
- non-destructive mutation (new copies for updated objects): records
    - `record Person { prop... }`
    - shallow copy-mutate: `var otherPerson = person with { LastName = "Hanselman" };`
- shallow equality (like struct value equality)
- copy/equality are based on the runtime type (not base record)
- constructor will auto-create properties with parameter names
- C# 10 will "convert" anonymous types to anonymous records
- if you need an object graph, use classes or records (because need references for graph) vs. structs
- once you have a constructor, they support deconstruction 
- everything is just classes under the hood so they generally work wherever classes could be used
### Patterns
- `and or not` between switch patterns

## A talk for trailblazers: Blazor in .NET 5  -  Steve Sanderson   Safia Abdalla  
### Improve dev experience
- CSS isolation: `Index.razor.css`
    - no need to declare globally unique class names
    - even element selectors
- Packages can add their own css/js
    - ex: Monaco code editor
- Better debugging
- InputFile component for file uploading
- Virtualization:  `<Virtualize Items="Data" Context="entry">`
- Azure static web apps integration
### Improve perf on WASM
- 2-4x faster in typical scenarios
- Changes made to Chromium as well (~2x speed improvement)
- Protected local storage
- Browser compatibility attributes for your API methods
- Render modes
    - WebAssembly Prerendered: static html
    - WebAssembly: blazor in mvc
- Lazy loading dependent assemblies
### Fill feature gaps

## Porting Projects to .NET 5  -  Immo Landwerth   Phillip Carter  
- AppDomains -> AssemblyLoadContext
- Remoting -> named pipes, grpc
- WebForms -> Blazor
- WCF Server -> grpc, oss: CoreWCF
- WF -> oss: CoreWF
- TFMs:  `net5.0` (portable) and `net5.0-windows` (`net6.0-android` etc coming in 6)
- Target netstandard2.0 for both .NET Framework and all other platforms
### Understand goals
- Only port projects that you need to innovate in
- Maintenance-only projects can stay on Framework
- Don't make one big port; you gotta keep shipping software
- What would porting give you?
### Inventory
- `API Port` to get an inventory before
- Drop legacy stuff before
- Look at dependencies to see if they support new
### Convert Project
- First step could be to migrate project files to sdk-style but still targeting framework
### Move to .NET 5
### Move to other OS
- CI system has to support all OSes because they still need to test on the real thing
### Demo
- `dotnet tool install -g apiport`
- `dotnet tool install -g try-convert`
- `apiport analyze -f {dir of assemblies}` (tells you "how compatible")
- `tryconvert -w .` to get you started on converting long-form csproj files
    - Can't currently convert MVC or WebForms
    - Does not touch source code
    - packages.config -> package references
- https://aka.ms/net-porting-docs
### Q&A
- tryconvert runs in an msbuild context so it should always "build" vs the community migrator which is a less-conservative xsl-based transformer

## Entity Framework Core 5.0: The Next Generation for Data Access  -  Jeremy Likness   Shay Rojansky  
### Overview
- Instantiate dbcontext per connection in ASP.NET (very light)
### New/Improved
#### Debugging
- DebugView property on queries which has both the actual query and the normalized LINQ
- `.LogTo` on context config for super simple logging setup
#### Mapping
- Many-to-many first-class support (finally feature parity with EF6)
    - just collections on each poco
    - creates join table for you (when implicit)
- Table-per-type (TPT) now supported (not just table-per-hierarchy)
    - Does involve joins so should prefer TPH in most cases (perf)
### New docs
- https://aka.ms/efdocs
### Q&A
- full record support is coming (not well supported now)


## Modern Web Development with Blazor & .NET 5  -  Dan Roth   Javier Calvarro Nelson
- `<component>` tag helper to include a blazor component in an asp.net mvc page
- No httpcontext on client so you pass anything like that as parameters to components
- Change `component` render-mode to ServerPrerendered and pre-get all data to send it to the component (data must be serializable)
- Change `component` render-mode to WebAssembly to run in WASM (need API to call from client)
- Change `component` render-mode to WebAssemblyPrerendered to use server first and then client

## Developing and Deploying Microservices with 'Tye'   -  David Fowler   Glenn Condron  

## Get to know the .NET 5.0 SDK  -  Kathleen Dollard   Rainer Sigwald  
- Tooling moves faster than the runtime (4x per year vs 2x year)
- Solution filters
- Change waves
- Binary log files?
- Structured log viewer

## High-performance Services with gRPC: What's new in .NET 5  -  James Newton-King
### What
- Largest RPC mindshare
- Cloud Native Computing Foundation project
- HTTP2/Protobuf
- Platform independent
- Contract first vs. REST/HTTP which are code/content first
- grpc content is for computers; rest is for humans
### What's new
- gRPC-Web browser support
    - grpc-web server middleware
    - grpc-web blazor client
- new grpc hosts on Windows: http.sys and iis (newer OS versions only--insider?)
- Can use IPC
- .NET 5 aggressive trimming
### Perf
- HTTP/2 server allocations reduced by 92% (Kestral)
- HPack response compression
- Protobuf serializer uses Span<T> (no allocations)
- requests per second:  Server: 65%, client 220% faster
### Docs
- https://aka.ms/grpcdocs
- https://aka.ms/grpcexamples
### Q&A
- Protobuf.NET-grpc:  community code-first; good for c#-only; using contract first is best for cross-platform

## GitHub + Visual Studio ❤ .NET  -  Vix Rian   Andy Sterland  
### CodeSpaces - Preview
#### devinit
- base image (Win10, VS, from MS) + `.devcontainer.json` + `.devinit.json`
- don't depend on base image; anything custom needs to be in repo
- devinit is a metatool (task runner?) to install/setup your dependencies
- runners available for sdks, msi, chocolatey, dotnet tools, etc
- `postCreateCommand` in `.devcontainer.json` that executes `powershell...devinit init`
- This is for Windows setups; existing container support is fine for smaller 
- https://aka.ms/devinit/docs
### Summary
- https://aka.ms/vs-preview
- Sign up for beta: https://aka.ms/vscs-github
- aka.ms/GithubActions-Azure
### Q&A
- Currently only console and asp.net; planned support for desktop/mobile
- Interested in on-prem requirements; lots of complexity
- Win image is not available (license key) but he will look into sharing the build script

## Effectively Diagnose and Debug .NET Apps in Visual Studio  -  Mark Downie  
### Debugging .NET with WSL
- Sweet spot between prod realism and productivity
- Speed, easy install
- VS already has remote debugging and container tools if you want realism
### Tips and Tricks
- Use right click, step into to choose which thing to step into (allows skip of properties)
- Parallel Stacks is a visual representation of what's going on
### Perf Tool
- Debug | Profile Performance

## What’s New in Visual Studio 2019 and beyond  -  Caty Caldwell  
### Customizing env
#### Themes
- Ctrl+Q "manage extensions" then search for theme, install vsix
- Ctrl+Q "themes" -> change env color themes
- She uses One Dark Pro
#### .NET Core Templates
- Project | export template
- Choose a project or item to export for later reuse
- Can modify metadata tags (manually?) to make it easier to find
- Shows up in your create new project dialog
#### Solution filters ⭐
- On sln open, "Do not load projects" checkbox
- Select projects and then right click, reload project
- Right click solution, hide unloaded projects
- Right click solution, save as solution filter
#### Configurable file nesting
- Icon in solution explorer to enable
- Right click at the level you want to start nesting (sln/proj)
- json file with rules to nest similarly-named files (different extensions) under each other
#### Web Live View

## Improve Your Productivity with Roslyn Analyzers  -  Mika Dumont   Kendra Havens  

## HTTP API Development with .NET, Azure, and OpenAPI: Paper Cuts Begone!  -  Brady Gaster  
### OpenAPI/Swagger
- Can do anything you want to modify the model/api docs:  like pulling info from xml doc comments!!! 
- Use Name attribute to get good compatibility with various openapi tools
- F5 goes to swagger ui
### REPL
- microsoft.dotnet-httprepl
- Set that up through browse
- You can then set it as your "browser"
- if you can navigate it like a directory structure, it's probably an okay api structure
### Publish openapi doc to Azure API Mgmt
- Can then export to PowerApps (simple apps)

## Collecting ASP.NET Core Performance Traces in a Kubernetes Cluster  -  Mike Rousos  
### Tools
#### CLI tools - no elevation, no env vars
- dotnet-trace: collect managed perf
    - Installed by SDK
    - requires access to /tmp directory
- dotnet-dump: includes native stuff which means you have to analyze on same platform
- dotnet-gcdump: only gc, can be analyzed cross platform
- dotnet-counters: perf counters, maybe run this first to get a feel for what's wrong
- dotnet-monitor (preview): sets up http endpoints in kubernetes to request stuff above
#### Other options - elevated perms, may not work with containers
- PerfCollect: managed and native
    - Installed via downloaded script
    - requires SYS_ADMIN/sudo
    - Requires env vars
- CreateDump: managed and native calls stacks
    - COMPlus_DbgEnableMiniDump: env var to auto create dump when exception occurs
    - requires sys_ptrace or sudo
### Container challenges
- If installing the tools ahead of time (via SDK), will increase container size by 10MB apiece (gcdump is 50MB)
- In alpha: ephemeral containers in kubernetes to add debug containers (sidecar) as needed.
- Search docs.microsoft.com for debugging linux

## Secretless Development from Local to Cloud with the New Azure SDKs, Project Tye, and Kubernetes  -  Jon Gallant  
### Azure SDK
- aka.ms/azsdk
- aka.ms/azsdk/intro
####
### Project Tye
### Azure Kubernetes

## 03:00** Getting Real-time Insights from your Serverless Solution  -  Eduard Keilholz  

## 04:30** Migrate & Modernize ASP.NET Applications with Azure App Service and .NET 5  -  Gaurav Seth   Byron Tardif  

## 02:00** Introducing the MVVM Toolkit, a .NET Standard Library in the Windows Community Toolkit  -  Michael A. Hawker   Sergio Pedri  

## 06:30** Components in Blazor  -  Poornima Nayar  

## 09:00 Analyzing Memory Dumps of .NET Applications  -  Giovanni Bassi  
- bit.ly/windbgpreview - update of windbg, easier to use
- dotnet-dump can be analyzed in windbg
- symbols take a while to download, cache locally (takes a lot of space); new symbols for every version

## 09:30 Enhancing Test Readability with Extension Methods and Fluent Interfaces  -  Nico Paez  
### Importance of tests
- CD/CI makes tests first class citizens
- Tests are really your documentation: should be clear (update code, update tests)
- If TDD, tests are a design tool
- If test code/setup is long, may be a design smell in app
### Patterns
- Object Mother Pattern: factory for generating your app objects for tests
- Builder Pattern
- Fluent Interface
### Tools
- https://fluentassertions.com
- Extension methods to make more readable

## 10:00 Application State in Blazor Apps  -  Carl Franklin  
- https://blazortrain.com - to see demo apps developed
### Instance Scopes
- Per-user instance: like Session in Web Forms
    - Services.AddScoped
- Per-application instance: like Application in Web Forms (singletons); blazor server only (since client-side would be one user)
    - Services.AddSingleton<>()
- Class instances: transient
### Three ways
- Cascading component
    - easiest to implement
    - Does not allow notifications
- Scoped service
    - Inject into components
    - Useful if you need to raise notification events
    - Requires event handling, IDisposable
- Hybrid
    - Scoped Svc for handling change events
    - Access via Cascading Component
    - Use this option if you need to persist state

## 10:30 2 years, 200 applications: A .NET Core Migration at Enterprise Scale  -  Lizzy Gallagher  

## 11:00 Blazor Stability Testing Tools for Bullet Proof Applications  -  Ed Charbeneau  
- Unit, Integration: xUnit, bUnit
- System Test: selenium
- bUnit is blazor component-specific
    - C# or Razor syntax
    - semantic HTML comparer (ignore whitepspace, class attrib order, etc)
    - Interact, inspect, triggering event handlers

## 11:30 Robust Connected Applications with Polly, the .NET Resilience Framework  -  Bryan Hogan  
- Testing: no-op policy; mocking polly exceptions; Simmy (sp?)

## 12:00 From Web Forms to Blazor - Introducing the Blazor Web Forms Components  -  Jeff Fritz  
- http://bit.ly/blazorwebformscomponents
- Web Forms -> MVC: no components; straight html; more testable
    - WF + MVC == FrankenApp
- WF -> Angular/Vue/React: similar component-driven; C# -> JS _everything_; not 1:1 code/arch
- WF -> Blazor: component-driven; oss components; bUnit; C# and libs; 1:1 code/arch with your WF app
- Issues
    - `<% %>` (bee sting) -> @notation
    - ViewState -> state managed on server
    - Postback - signalr channel
    - MasterPages -> LayoutComponents
    - IIS -> Kestral, multiplatform
### Migration Process
- Move business logic out of aspx/ascx into class libraries.  Both WF and B can then use it.
- Create a new Blazor project
    - Ref class libs
    - Migrate static files
    - Migrate config
- Rewrite aspx/ascx as .razor files
- https://aka.ms/blazor-ebook
### CodeFactory https://codefactory.software
- Pattern automation tool that uses your src code like a data model
- Build templates that can be automated and attached to VS
- Templates available for refactoring, migrating, and scaffolding
    - Template available aspx -> .razor

## 15:00** Writing Event Based Microservices using Steeltoe  -  David Tillman  

## 15:30 Build native and hybrid mobile apps with Mobile Blazor Bindings  -  Eilon Lipton  
- Host all or part of your application as web page
- Author native UI using Blazor syntax
- Blazor Web -> UI library
    - Host in Blazor Web
    - Or host in Blazor Hybrid (mobile, desktop)
    - Not an iframe--hosted in the app

## 16:30 Lessons Learned from Building the YARP Proxy on .NET  -  Sam Spencer  
- https://github.com/microsoft/reverse-proxy


# Misc
- Cool pwsh git prompt: oh my posh (search for hanselman pretty prompt)
- Zoomit from sysinternals:  freeze screen, zoom in, and annotate
- AZMask in extension stores: will blur your azure account ids, etc.
- Dependabot (keeps dependencies up to date)
- dotnet-oudated global tool to see locally what dependencies are outdated
- tinyurl.com/codednc2020 - free 12 month subscription to Code Mag
