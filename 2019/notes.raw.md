# Day 1
## Keynote

SO is converting to .NET Core 3.0
- have seen perf improvements

VS2019 is fastest adopted in history

.NET Core 3.0
- WPF and WinForms
- Side-by-side and self-contained exes
- Full stack with Blazor SPA

VS2019 16.3

Kubernetes orchestrator

gRPC - comm with strong contracts across langs/platforms, google protobuf

Worker Services - long running procs on Win and Linux, queues

Security with Identity Server

### gRPC
? VS can take json and make c# types

### C# 8
- Nullable, non-Nullable
- Async streams
- Be more productive

All Win10 apis are available
open-sourced winforms and wpf

App Center for .NET Core 3.0 Win Apps
- appcenter.ms
- metrics for desktop Apps

### WinForms with App Center
- try-convert sample tool to convert .net framework csproj to core csproj
- Add <PublishSingleFile>true</PublishSingleFile> for single exe; needs RuntimeIdentifier; use PublishTrimmed to remove unused stuff (experimental)

### Xamarin
- ios and android via c#
- Xamarin.Forms runs on everything
- announced today: XAML Hot Reload, Hot Restart

### ASP.NET Core 3.0 Blazor
- Web Assembly in preview, May 2020 release
- websocket to server to run c#
- class lib controls can carry static files that are made available to host app

### ML
- Model Builder trains on a data set for classification

### IOT

### Open Source
#### MS Contributing
- gRPC
- IdentityServer
- Swashbuckle - Swagger

### .NET 5
- 11/2020
- Electron apps using a blazor app

### Schedule
- .NET Core 3.1 will be LTS
- LTSs will be in Novembers

### Old stuff should remain on .NET Framework

## Welcome
- www.dotnetconf.net/party
- AWS has joined is now a corporate sponsor of .NET Foundation
- dotnetfoundation.org/become-a-member
- All the stuff is run in github 
- Twitter #dotNETConf #CodeParty

## Hosts
- dot.net/videos a whole bunch of videos

## C# 8 Part 1 `null` - Mads
- `if (thing is {})`
    - if thing is not null (is an object)
    - can be named `{} thing2`
    - object pattern matching { Prop: type }
- library writer:  we're in nullable adoption phase until .NET 5 so work on it now
- still a little bit preview as they see how it goes until .NET 5
- multi-targeting .NET core 3.0 for nullable and .net standard 2.0

## C# 8 Part 2 - Bill Wagner
### Async enums
- AsyncIterators `yield return`
### More patterns
- switch expressions on object and match on types with property values
- `_` generally means don't care
### Default interface members
- compiler will ensure only one can be called (no ambiguity or error)
### Indices and Ranges
- `^1` is the last element (where `^0` is length)
### Using declarations
- `using var blah` to reduce using ladders
- goes out of scope at end of enclosing scope (e.g., fn)
### Static local fn
- disables closure which can be faster
### Readonly members
- mark member fns that they don't make changes which enables compiler optimizations
### Null coalescing assn
- `??=`

## Modernizing desktop app
- VS itself will stay on .net framework
- Use Microsoft.Windows.Compatibility shim
- Early preview for winforms designer: https://aka.ms/winforms-designer

https://github.com/dotnet-presentations/dotnetconf2019

## Blazor Full Stack - Dan Roth
- Blazor client apps in May 2020
- https://blazor.net
- install blazor webassembly template (preview)
- VS 2019 16.3 or VSC with C# extension

## ASP.NET Core with Kubernetes
### HealthChecks
- You can add checks to make sure your app has all of its dependencies
### ?
- Down to 88MB on alpine
### Worker Service
- Any generic service
- One line to select Windows or systemd
- `CreateHostBuilder`
### Endpoint routing
### Configuration
- ConfigMaps and secrets

## EF Core 3.0
### LINQ overhaul
- Client eval only at top level select
- Single sql query per linq query
### C# 8 support
- async streams
- nullable ref types
### Cosmos DB provider
### Database interception
- Before/after event handlers
### Reverse engineering of views
- Key-less entities
### Microsoft.Data.SqlClient
- Latest version: encryption, Azure
### EF 6.3 on .NET Core
- No new features
### Next?
- EF Core 3.1, LTS, bug fixes, small enhancements
- vNext (under discussion): perf, many-to-many, table-per-type inheritance, sprocs, update model from db, primitive types from raw sql, property bag entities, ignore parts of model for migration

## .NET Community Roundup - Scott Hanselman, Jon Galloway
- .NET Developers Association - Eastside
- .NET Foundation 240k members
    - dues defaults to $100 but can be any amount (including none)
- https://presentations.dotnetfoundation.org
    - .NET Foundation will help you with presentation materials so you can do it yourself in user group.
- Your unique experience is worth blogging about.
- https://dot.net/videos - videos for beginners/101
- .NET Community Standups


# Day 2
## The Future of Blazor on the Client - Daniel Roth
- Blazor to have native-like capabilities on mobile, etc.
### WebAssembly in May 2020
### PWA - Progressive Web App
- Supports offline, push notifications, fast & response, possibly OS installable
- Icon in browser allows application to be installed as a PWA
- Some additional files required
- Still WA
### Blazor Hybrid for desktop
- App runs natively but uses web controls for rendering
- Not WA
- Electron instance is running in .net core so it has full access to native capabilities
- see aka.ms/blazorelectron
### Blazor Native
- Default renderer uses html but can be replaced such as one that does native controls
- aka.ms/blutter (blazor + flutter) for a concept of what's possible (not going to ship)
### Roadmap
- Server now
- WA May 2020
- PWA & Electron previews with .NET 5 (November 2020)
- Native is under investigation
### More
aka.ms/blazorworkshop
aka.ms/awesomeblazor

## Blazor and Azure Functions for Serverless Websites - Jeff Hollan
- Traditional 3 tier apps need a server always running (cost/hit) but also need to be scaled if necessary
### Serverless Web App Arch
- Get static page and code from web storage ~S3
- All JS
### WA and Blazor
- Call Azure fn for some server-side code (~DB)
- Easily scales from zero to many
- Users' machine power to render ui
### Demo
- Azure storage hosts blazor site
- Azure Fn hosts anything that you want to keep server-side
### Q&A
- Q1Y20 .net core 3 in AzFn

## DevOps for the .NET Developer - Zachary Deptawa
- Continuously deliver _value_ to users; must be a mantra in entire company
- Stages
    - plan and track
    - dev and test
    - release
    - monitor and learn
### Az has five pieces to support devops
- Azure boards
- Az pipelines
- az repos
- az test plans
- az artifacts

## Durable Functions 2.0 - Serverless Actors, Orchestrations, and Stateful Functions - Jeff Hollan
### Fn chaining
- Traditionally, fn1 -> queue -> fn2 -> queue -> fn3, etc.
### Durable
- One fn (orchestration) to call the other 3 async (activity)
- Can run a long time
### Patterns
- sequencing
- fanning-out and fanning-in
- external events correlation (wait for all 3 things to happen and then continue)
- flexible automated long-running process monitoring
- http-based async long-running api (return immediately with a status endpoint)
- human interaction
### How it works
Az durable fn tracks execution history (WWF?)

1. On exec, first asks if it has already been done ()
2. Task scheduled
3. Orchestrator completes
4. Activity fn runs and task completes
5. Orchestrator starts again (from the top)
6. Checks exec history and sees that the activity fn is done and skips it and continues doing other stuff

### Improvements in 2.0
- durable/stateful entities pattern (actor-like)
- durable/resilient http calls in orchestrator
- pluggable state providers (not just az storage)
- roslyn analyzer to find common pitfalls

### Demo
- api for interacting with durable fn
- ? api calls in VS Code

### Circuit Breaker pattern
- Lots of events triggering a fn that does stuff
- Many instances of fn
- Something downstream (~db) goes down so fn keeps failing
- Durable entity fn watches the exceptions and will turn off the fn trigger if the threshold is hit

### Resources
- aka.ms/durable/2docs
- aka.ms/durable/entitysamples
- aka.ms/durable/circuitsample

### Q&A
- Az Fn t-shirt: At ignite
- Logic apps: declarative, visual designer; similar to az durable fn; personal preference; complex is az durable; logic apps has 200+ connectors so use those
- Fn apps with net core 3 will GA early 2020
- sdks available to clean up az storage account to clean up state (otherwise it stays forever); does cost per your storage account

## Tips and Tricks on Moving to .NET Core - Kathleen Dollard
### Should you port?
#### Benefits
- Deployment
    - Side-by-side installation of runtim
- Faster and less memory
- Cross platform
- open source
- Will have new features
#### Other concerns
- .NET Framework _will_ be supported for a long time
    - Windows component
    - Used heavily within Microsoft
    - VS
    - Stabilizing .NET Framework is important
- NT services are supported
- MIT license is friendly for business
- It _is_ open source but it's also distributed _by Microsoft_ so you get both benefit sides
#### Is your app in active development?
- If you aren't making significant changes, you may not benefit from new features.
- Moving to core will _make it active dev_
#### Are the frameworks you use available in .NET Core?
- Most things are there but some won't be
    - web forms, mvc, wcf, windows workflow, remoting, appdomains, CAS
- Re-implementing things in core from framework is "done"
#### Which support policy is best for your app?
- Major releases every year, LTS in odd years
- LTS core releases supported for 3 years
#### Are the 3rd party tools and dependencies available?
- Look it up
### Preparing to port
- Move to recent .NET Framework first (>= 4.7.2) because it is most similar to core
- How to validate success?  Test coverage, perf metrics
- Evaluate architectural changes
    - Target .NET standard 2.0 where possible for libs
    - Limit arch changes during port (do one first and then the other)
    - Consider strategy changes separate from move
        - Isolation of concerns (move all wpf to one lib for example)
- .NET portability analyzer
### Porting your app
- Projects with least deps first
- Prototype early
- Project file upgrades will be a headache
- ASP.NET
    - If IIS integration pieces, plan to change those pieces because they're different
- WebForms
    - Consider moving to Blazor because it has a similar event model

## Azure App Configuration - Making Centralized Configuration Easy - Jimmy Campbell
- Shared settings across apps
- Settings as key-value pairs
- CLI and UI feature parity
- kvp's can have a label as an additional dimension (not just key: eg, color of premium vs. standard)
- Key Vault is better for secrets because they can be rotated
    - Coming soon: a way to access secrets from within App Config

## Azure Services Every .NET Developer Needs to Know - Tim Heuer   Angelos Petropoulos
### Primer
- account is me; subscription can be shared
- resource is any service in az
- resource grp can group services and establish config/security
- hosting is you provide code, az runs it
- service is you provide the data, az takes action on it
### Key Services
#### App Service
- Great for web apps and apis
- Fully managed os updates
#### Azure SQL
#### Azure Storage (Blob)
#### Azure Functions
#### App Insights

## Diagnostics Improvements in .NET Core 3.0 - Sourabh Shirhatti   John Salem
### Runtime features
- Diag Server in runtime itself
- Metrics - .NET runtime and ASP.NET Core emit EventCounters via EventCounter API; works in low-privilege envs
    - creates .nettrace file which can be viewed in speedscope (can be installed as PWA)
- Tracing
    - dotnet trace
    - collect eventsource events via eventpipe
    - support for gc heap counts coming soon
    - visualizers in speedscope, VS and Perfview (Chrome dev tools and Cachegrind in the workd)
- Crash dump for exceptions
    - dotnet trace: Commands come from sos (hosted version without windbg debugger)
### Tools
- dotnet tool install --global dotnet-counters
- dotnet tool install --global dotnet-trace
- dotnet tool install --global dotnet-dump
- dotnet symbol
- dotnet sos

## Build Amazing Cloud Connected Apps With Xamarin, Azure, and App Center - Matthew Soucoup
- Xamarin.Forms for shared UI
- Use az fn for backend
- App Center for mobile: Auth, Data, Push
    - Configures Az AD B2C and MSAL
    - Can use other identity providers
    - Uses cosmosdb for individual user partitions of data (plus public partition)
    - Local caching of cloud data supports offline
    - Data cosmosdb free tier is coming soon


# Day 3
## Akka.NET - Aaron Stannard
- Akka, Akka.Remote, Akka.Persistence (durable), Akka.Cluster (HA), Akks.Streams (fun?)
- Receive and send messages
- Receive<T> adds a handler for that type
- `var actorSystem = ActorSystem.Create("PingPong");`
- Tell method is fire and forget; Ask for request/response (less popular)
- Actor = a class that can contain state and modifies that state by processing messages it receives (unit of work)
- ActorReference = a handle to an actor. Allows you to send the actor messages without knowing its implementation type or location on network. Enables a high level of decoupling.
- ActorSystem = a collection of actors that exist inside a single process and comm via in-memory message passing.
- Cluster = a collection of networked ActorSystems which communicate via tcp
### What?
- Actors run asynchronously; don't do anything until awakened when a message receives in its mailbox
- 100ks or millions of actors in a busy system; by default only 1k of mem each
- Actors process messages one at a time; a single actor is always thread safe because its state is not shared
- FIFO
- State is shared only through messages; actor B must send message to requesting state from A; A sends immutable copy; A can receive message to update but that doesn't change B's copy; there is a way to always have latest with actor reference
- Actors live in supervision hierarchies: /user -> /parent(s) -> /children
    - If a child actor fails (exception), its parent will get a notification and why. Parent decides what to do--by default restarting child with initial state (Props).  Easier to restart from known state than trying to dig out from exception.
    - Parent can decide to do other workflow like pushing exception up and recycling whole system.
### Why?
- Actors are reactive
    - accumulate state in-memory
    - can react to changes in state in real-time
    - no db calls, io, or external infrastructure
- Actors reduce big problems into small ones
    - Big firehose of events from many different sources (users, iot, etc)
    - Break them down so that each individual actor handles the state for the one entity instance it handles
- When to use akka.net
    - Event-driven applications (chat, workflow, crm)
    - Finance (pricing, fraud detection, algorithm trading)
    - Gaming (multi-player)
    - Analytics & monitoring
    - Market automation
    - Systems integration
    - IOT (healthcare, transportation, security) -- probably biggest segment of akka.net users
-Recap
    - Fun and easy reactive programming (functional programming without the bad taste of some others)
    - Radically simplifies state and event mgmt
    - Breaks big problems down into small ones
    - Integrates with lots of other tech you love (kafka, azure service bus, signalr)
    - Runs everywhere
- Not useful for simple crud
### Learn more
    - http://learnakka.net
    - getakka.net
- Q&A
    - Biggest cost is probably the mindset change from OOP

## ASP.NET Razor: Into the Razor'verse - Ed Charbeneau
### Syntax
- Template syntax based on C#
- Razor is very simple compared to Ng
- Control structures
### Razor Views (cshtml)
- Code-focused
- returned from a controller action as a viewresult
- typically html helpers
- V of MVC
### HTML Helpers
- methods within html razor views
- encapsulates a block of html and code
- produces html strings
- ex: `@Html.ActionLink("Create New", "Create")` --> anchor
- helper sig: `Func<IHtmlHelper, IHtmlContent>`
### Razor Pages (newer asp.net core)
- Page-focused approach incorporates its own controller/action/routing
- Can integrate with mvc
- Content is made of html and tag helpers
- Code behind
- `@page` and `@model`
- `OnGet`, etc., correspond to http methods
- vertical slice
### Tag Helpers
- async server-side processing via html elements
- html helpers are `@Html...` have to escape class names, etc. vs tag helper `<label asp-for="Name" class="caption">First Name:</label>`
- doesn't "stick out" as much; easy to read
- all the form building tag helpers built-in
### Blazor (latest)
- Razor syntax with razor components
- component architecture vs. html generator
- creates a RenderTree (dom abstraction)
- .razor file extension used for code gen of rendertree
- uses a shadow dom to diff the change before writing change back to real dom
- components can have page routes like razor pages (act as both page and component)
- razor page and html helper to bootstrap (older tech)
- don't write raw html (or manipulate dom) because you bypass the diffing
### Resources
- blazorpro.com
- blazorvideos.com
### Q&A
- No view state in blazor (vs web forms); state managed via di and POCOs
- Blazor learning path/curve: pretty easy; component arch is dead simple

## Putting the ".NET" into "Kubernetes" - Elton Stoneman
### 101
- Kubernetes is a cluster of multiple servers running containers (linux and windows)
- yaml file describes how many of which image on which platform and kubernetes manages the rest
- kubernetes monitors servers and restarts the containers elsewhere
### Building & running .NET apps with Docker and AKS
- kubernetes can store secrets like aspnet config files
### Summary
- apps start to look the same:  dockerfile, app.yaml, pipeline commands
### Q&A
- learning path:  docker -> docker-compose -> Docker swarm -> Kubernetes

## Modernizing .NET Applications with .NET Core - Beyond the Basics - Mike Rousos
### Leaving the sandbox (security)
- Most APIs are no-ops; restricting permissions now throws
- OS security-related APIs (ACLs) work as usual (found in compat pack)
### Living without AppDomains
- core has one primary appdomain
- most apis are still there but new domains can be created
- if for sandboxing (~ security-limited code): remove or run out of process
- if for isolation or unloading (~ plugins): AssemblyLoadContext
- .net core 3.0 can now unload AssemblyLoadContexts
- Tip: Use conditional ItemGroups in project to remove whole classes from compile based on target platform (use a file extension ~ .core.cs)
- framework's unload app domain is destructive; core's assembly unload is cooperative (no references)
### Config and its friends
- System.Configuration.ConfigurationManager is present (in compat pack)
- But the Framework doesn't use it (if you have them, it will fail to load)
- Only appSettings, connectionStrings, and custom sections
- apis: wcf client, system.diags tracing, system.net, etc. must be configured _programmatically_
- Regen wcf clients and change other apis to configure programmatically (dotnet-svcutil or VS Connected Services)
- WCF server apis
    - no planned support so consider moving to grpc or web api
    - there is a community effort to port it if you want to help
    - or just leave on .NET
### Interop options
- p/invoke work cross-platform and are generally recommended (they are different per platform)
- com only on windows (still working on dynamic support [or use reflection]) - must use msbuild for comreferences in project files
- winrt interop works as always
- System.EnterpriseServices apis are not supported
- :-) "test burg"
### Remoting, intentional and otherwise
- Remoting is often pulled in incidentally
    - RealProxy (using it for aop type stuff) - use System.Reflection.DispatchProxy or Castle Proxy
    - Delegate.BeginInvoke - uses remoting; use task-based async patterns instead
- For simple ipc: system.io.pipes, system.io.memorymappedfiles
- more complex: grpc is probably best though there others

## Architecting .NET Microservices in a Docker Ecosystem - Hamida Rebai
- Kubernetes more mature on Linux; less on Win
- Az Service Fabric more mature on Win; less on Linux; also supports durable microservices

## A Gentle Intro to Azure Cosmos DB for the ASP.NET and SQL Server Developer - Santosh Hari
- Microsoft Az only
- schema agnostic json data
- SQL API in Cosmos mostly complies with MongoDB api so you can switch to it
- Use appropriate data model for your scenario
- Various db types are to complement not replacement
- Consistency:  strong (ACID but single region); bounded staleness (never out of date but lags); session (Default, most popular); consisten prefix (read-writes are in order); eventual (writes can be out of order)
    - affects cost because of different amounts of writes
- choosing correct partition key is paramount
- use ro and rw keys as much as possible
- Local cosmosdb emulator is available
- Use latest v3 sdk as it has many improvements, including more intuitive
    - streaming api avoids deserializing-serializing when just passes the results to something else
- document keys are case sensitive
- Keep an eye on RUs in the query stats of storage explorer
- Include partition key in query for best performance
- Server-side programming: sprocs, triggers, udfs help with ACID; javascript code
- change feed: only inserts and updates, no deletes

## Tour of Microsoft's Reference ASP.NET Core App: eShopOnWeb - Steve Smith
- http://aka.ms/webapparchitecture
- free cloud native ebook https://dotnet.microsoft.com/learn/azure/architecture
- https://github.com/ardalis/cleanarchitecture
- make the right thing easy, the wrong thing hard ("pit of success")
    - UI classes shouldn't depend directly on infra classes
    - Business/domain classes (same)
    - Repetition of code is a problem
    - n-tier: everything depends on db
    - onion/hexagonal: each piece has a "port" or interface
- Core: interfaces, entitites, value objects, domain services, custom exceptions
- Infrastructure (depends on Core not the other way): repositories, dbcontext, cached repositories, web api clients; file system accessors, logging adapters, email/sms; system clock; config file accessors (builtin in core); other services; some interfaces that are tightly coupled to infra (like an azure sdk)
- Web (depends on core, lightly dependent on infra): controllers, views, razor pages; view models, api models, binding models; filters, binders, tag/html helpers; other services or interfaces which don't belong anywhere else
- Shared kernel: make a nuget package (core depends on this)
### eShopOnWeb reference app
- specification pattern
    - query encapsulated in an object
    - repositories have only basic crud ops instead of so many custom methods
    - seems similar to PPM's SqlStatement and Criteria
- aggregates pattern
    - fetch a whole object or set of objects, not pieces/individuals
### Q&A
- search for eshoponcontainers (free ebooks)
- not yet updated to core 3 but soon

## Disaster Resilience the Waffle House Way: Flat-tops, feature flags, and finite state machines - Heidi Waterhouse
### Waffle House
- plan for degraded service
- prepare at the edges
### problems
- plan for slow/minimal connection
- stop regional outages from taking out others
- slow failure is hard to diagnose
- observation changes state (hiesenburg) - adding a monitor during failure can add to problem
- the human factor
### how to
- state machine what can happen
- plan for routes to paths which are least damaging
- reduced service
    - serve only the essentials/mvp (if slow: drop pictures, ads)
    - must decide what your core value and deliverable is
- talk to the business owners (not the enemy, SMEs of customers)
- service level agreements: things can be in an "ordinary broken" state without shutting the whole thing down
- use circuit breakers and safety valves ("dark is better than dead")
    - humans are the slow and fallible part
- traffic is pressure
    - load shedding?
- modular delivery
    - microservices and modules 
    - distributed monolith is still a monolith that fails when a piece goes down
- feature management (feature flag)
    - not just a staging env; prod is full of real human data
- define victory
    - what's mvp or minimum victory?
    - what's not bad? good enough? <-- aim most of it here
    - what's best case? flawless victory?
### Take Aways
- make failure more nuanced
- make success bigger
- Waffle House: order the hashbrowns

## Modeling Relational Data with Cosmos DB - Steven Faulkner
- SQL storage optimized
- NoSQL speed optimized
- It's a SQL api not a sql db
### Probs
- Scans: it's still possible but not very much
- Cross-partition queries: talking to multiple physical machines
### Partition Keys
- `hash(partitionKey)` determines which machine it is on
- including partition key in query goes straight to machine
- filter only on something that is not a partition key means it has to go to every machine
- if id can be your partition key, it makes it distribute well
### Relational Data and NoSQL Thinking
- Avoid sql thinking (db schema, normalized data, rigid consistency, many tables)
- Application drives schema; denormalized data; flexible consistency; single container
- Transactions?  just try rewriting the failed document
- top-level entities have same pk and id
### ~ Blog
    - post
        -use two docs one with post id and one with "hierarchal" partition key ("user-1-posts")
        - Updates need to update both docs
    - User 2 docs where pk is secondary index "user-emails-user@domain.com"
- Update w/ change feed as an async/lazy update other pieces
- Materialized docs
- Split containers only as an optimization that you've already identified
### Take Aways
- Single container
- Best partition key name?  "partitionKey"
- Top-level entities: id == pk
- Relationships use hierarchal keys
- Optimize as data size grows (cross)
### Q&A
- 10GB per partition: number partitions for "older" stuff

## The Science of Great UI - Mark Miller
- no/lower saturation for secondary buttons
- rounded corners because corners aren't the important part
- every on screen element is info, but not equally important
    - emphasis maches element importance
- sufficient contrast
- physical proximity
- borders thin/low contrast no closer than 1.5 of space width
- sgui.com

## Be an A11Y: Build Accessible Web Sites for Everyone - Rachel Appel
### Why
- It's the right thing to do: reach all the people you should reach
- At some point it's going to be you (temporary or permanently)
- There is money involved: if you're a11y is good, they will flock to you ($8 trillion)
- People want better a11y software not better assistive technology
- 25% of the population at any given time have some issue
- Get over yourself:  make it accessible and care about it
### Types
- Visual (bulk of work)
- Auditory
- Motor
- Cognitive
- You may not realize you already use it:  escalators, glasses, trackpads, light on phone to see in dim env
### Assistive Technology
- screen narrators, braille readers, mouth stick, head wand, single-switch access, sip and pub switch, oversized trackball mouse, adaptive keyboard, eye tracking glasses, voice recognitition software
- people don't like being frustrated and won't use your product
### Visual
- Low vision
- Blindness
- Color blindness
- Color contrast sensitivity
- Screen Narrators
    - Download NVDA, Web Anywhere, etc., and you will see you can't navigate the web without your eyes
    - Use skip links to bypass nav links at top
        - use a hidden link at the top named "skip to main content," with href #maincontent to the element with id maincontent.
        - Use a css style position: absolute, left: -10000px; top: auto; width: 1px; height: 1px; overflow: hidden;
        - Use .sr-only class
    - Use semantic html ~ `nav` or `label` which the screen readers can bypass
    - In .NET, use Data Annotations and display names in models for screen readers
    - Tiny red star to denote required fields would be better with an actual word (see OOA accessibility required fields)
    - For older stuff, use aria-* attributes on elements
- Color blindness
    - download https://colororacle.org which allows you to see what they see so you can correct it
    - Don't use color as the primary indicator of what something does
    - Accessibility Color Wheel
    - Color Blindness Simulator (upload photos of your stuff to see how it looks)
- Color contrast
    - Can physically hurt
    - Use Color Contrast Tool
### Auditory
- mild hearing loss to total deafness
- don't rely exclusively on sounds for feedback
- use transcripts and closed captioning when possible
- be aware of "deaf culture"
    - sign languages (plural)
    - if doing video, be aware that signers can have accents
### Motor/dexterity
- Lots of illnesses/injuries, some very common like arthritis, tremors, broken bones, etc.
- People really do have seizures from web pages
- Ads which have teeny close button is incredibly frustrating
- Use alternative keyboard input
- Check your tab order is logical
- Use alt attributes
### Cognitive
- Lots of memory issues; autism; add; seizures; comprehension differences; injuries/illness
- No tools--just keep things clear and simple
- Do comprehensive UX testing with a wide range of users
### Synesthesia
- People experience things differently, crossed perceptions
- ~ Textures or sounds cause a taste sensation
### General Tools
- WebAIM WAVE scanner - scans your web page
- Web Content Accessibility Guidelines (webaim.org)
- Section 508 Checklist && WCAG2 Checklist (newer) (webaim.org)
- A11Y Project




# Ones I missed that I want to see, once available via on-demand
## *** Cryptography 101 with .NET Core - Robert Boedigheimer
## An Introduction to GraphQL in .NET Core - Nigel Sampson  
## Publish or perish - tricks to successfully ship your .NET Core 3 app - David Gardiner  
## High performance servers with .NET Core - Oren Eini  
## Exploring Cross Platform Unit Testing Tools for .NET Core - Toni Solarin-Sodara  
## ASP.NET Core Health Checks - Jurgen Gutsch  
## *** Move your Web Forms app to .NET Core without rewriting everything - Tomáš Herceg
## *** Versioning APIs with ASP.NET Core - Shawn Wildermuth
