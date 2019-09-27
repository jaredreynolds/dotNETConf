# [.NET Conf 2019](https://www.dotnetconf.net/)
The conference is virtual, free, and three days. The main content was broadcast from Microsoft Studios for 16 hours over two days (see [videos](https://www.youtube.com/playlist?list=PLReL099Y5nRd04p81Q7p5TtyjCrj9tz1t)). That was followed by presentations for 24 hours straight by speakers from all over the world. I hope those videos are also made available. Any slide decks provided by presenters are in a GitHub [repo](https://github.com/dotnet-presentations/dotnetconf2019/tree/master/Technical).

## My Top Takeaways
- .NET Core 3.0 and VS2019 16.3 are GA
- Keep your app on .NET Framework if it's not in active development
- Watch all the videos and/or read all you can about converting to Core before deciding to do so.
- Blazor is the recommended upgrade path from WebForms 😮 (due to similar event and component models).
- Accessibility support is **important**.

## Action Items
- VS2019 is the fastest adopted version; let's get on the bandwagon.
- We need deep dive investigations to decide if/what/how we will convert to Core.
- Accessibility: we need to get over ourselves, care about humanity, and just do it.

## New/Hot Tech
- .NET Core 3.0
- C# 8.0
- VS 2019 16.3 (supports all this stuff)
- Blazor
- Kubernetes
- ML.NET (machine learning)
- gRPC
- SignalR


## My Selected Faves and Random Notes (chronological order)
### .NET Conf 2019 Keynote - Scott Hunter, et al
- Most .NET Core 3.0 conversions are seeing perf improvements (speed/mem)
- WPF and WinForms support (open-sourced, too! 🙌)
- Blazor server pages
- Worker Services
    - Long running processes on Linux and Windows (e.g., queue handlers)
    - Replacement for Windows Services
- All Win10 APIs are available
- 3.1 is scheduled for November and will be LTS
- Major and first minor releases will come annually
- Next major version (11/2020) will be 5.0 to avoid confusion with .NET Framework 4.x

### ❤️ What's new in C# 8 - Part 1 - Mads Torgersen
- Only for .NET Core 3.0+
- Enforcement of nullable and non-nullable reference types
- Opt-in, somewhat experimental adoption phase
- Expect library writers to upgrade for the next year and flesh out any problems
- .NET 5.0 will begin solid adoption (if possible)

### ️️️️️❤️ What's new in C# 8 - Part 2 - Bill Wagner
- Switch expressions and more pattern matching support
- Default interface members
    - Adds a default implementation of new members _in the interface_ so that you don't have to update all the class implementers.
    - Compiler will ensure only one can be called (no ambiguity or error) to avoid problems with multiple inheritance.
- Indices and Ranges (`array[^1]` for last element--finally! 😥)
- Using declarations
    - `using var blah = new System.IO.StreamWriter("WriteLines2.txt");`
    - No scope indicators to reduce using ladders
    - Goes out of scope at end of enclosing scope (e.g., fn)
- Readonly members
    - Indicate member fns don't make changes which enables compiler optimizations
    - A step toward functional programming
- Null coalescing assignment `??=`

### Modernizing .NET Desktop Applications with .NET Core - Olia Gavrysh
- It's okay to choose not to convert to Core since Framework will be supported for a long time
- VS itself will stay on .NET Framework

### ❤️ Building Full-stack C# Web Apps with Blazor in .NET Core 3.0 - Daniel Roth
- https://blazor.net
- Currently server-side rendering only
- Web Assembly-based client support coming in May 2020
- Hope to have Electron apps hosting Blazor apps in .NET 5.0
- Install blazor webassembly template (preview)
- Use VS 2019 16.3 or VSC with C# extension

### ❤️ Entity Framework Core 3.0 and beyond - Diego Vega
- LINQ overhaul
    - Client eval only at top level select
    - Single sql query per linq query
- C# 8 support
    - async streams
    - nullable ref types
- Cosmos DB provider
- Database interception
    - Before/after event handlers
- Reverse engineering of views
    - Key-less entities
- Microsoft.Data.SqlClient
    - Latest version: encryption, Azure
- Next?
    - EF Core 3.1, LTS, bug fixes, small enhancements
    - vNext (all under discussion): perf, many-to-many, table-per-type inheritance, sprocs, update model from db, primitive types from raw sql, property bag entities, ignore parts of model for migration

### ❤️ .NET Community Roundup - Scott Hanselman, Jon Galloway
- .NET Foundation 240k members
    - Get involved, let your voice be heard
    - Dues default to $100 but can be any amount (including none)
    - Free for students
- ["Presentations in a box"](https://presentations.dotnetfoundation.org)
    - .NET Foundation will help you with presentation materials so you can do it yourself in user group.
- Your unique experience is worth blogging about.
- https://dot.net/videos - videos for beginners/101
- Weekly .NET Community standups

### ❤️ The Future of Blazor on the Client - Daniel Roth
- Blazor to have native-like capabilities on mobile, etc.
- WebAssembly in May 2020
- PWA - Progressive Web App
    - Supports offline, push notifications, fast & response, possibly OS installable
    - Icon in browser allows application to be installed as a PWA
    - Some additional files required
    - Still Web Assembly
- Blazor Hybrid for desktop
    - App runs natively but uses web controls for rendering
    - Not WA
    - Electron instance is running in .net core so it has full access to native capabilities
    - see aka.ms/blazorelectron
- Blazor Native
    - Default renderer uses html but can be replaced such as one that does native controls
    - aka.ms/blutter (blazor + flutter) for a concept of what's possible (not going to ship)
- Roadmap
    - Server now
    - Web Assembly May 2020
    - PWA & Electron previews with .NET 5 (November 2020)
    - Native is under investigation
- More
    - aka.ms/blazorworkshop
    - aka.ms/awesomeblazor

### ❤️ Blazor and Azure Functions for Serverless Websites - Jeff Hollan
- Very cheap
    - web site is static files from storage
    - az fn for db/secret code only runs when called
    - user's machine powers (pays) for everything else
- But scalable

### ❤️ Durable Functions 2.0 - Serverless Actors, Orchestrations, and Stateful Functions - Jeff Hollan
- One orchestrator fn alongside activity fns
- Can run a long time
- Patterns
    - sequencing
    - fanning-out and fanning-in
    - external events correlation (wait for all 3 things to happen and then continue)
    - flexible automated long-running process monitoring
    - http-based async long-running api (return immediately with a status endpoint)
    - human interaction
    - circuit breaker

### ❤️❤️ Tips and Tricks on Moving to .NET Core - Kathleen Dollard
- Too much good stuff - just watch it

### ❤️ Akka.NET - Aaron Stannard
- Fun and easy reactive programming (functional programming without the bad taste of some others)
- Radically simplifies state and event mgmt
- Breaks big problems down into small ones
- Integrates with lots of other tech you love (kafka, azure service bus, signalr)
- Runs everywhere
- Not useful for simple crud

### ❤️ ASP.NET Razor: Into the Razor'verse - Ed Charbeneau
- Explains how the various ASP.NET models differ (including decompilation of output)
- Don't write raw html (or manipulate dom) because you bypass the diffing

### Putting the ".NET" into "Kubernetes" - Elton Stoneman
- app configs/ops start to look the same (a good thing):  dockerfile, app.yaml, pipeline commands

### Modernizing .NET Applications with .NET Core - Beyond the Basics - Mike Rousos
- More helps on converting

### ❤️ Tour of Microsoft's Reference ASP.NET Core App: eShopOnWeb - Steve Smith
- Surprisingly good overview of ASP.NET solution patterns

### ❤️ Disaster Resilience the Waffle House Way: Flat-tops, feature flags, and finite state machines - Heidi Waterhouse
- plan for degraded service
- prepare at the edges
- plan for slow/minimal connection
- stop regional outages from taking out others
- state machine what can happen
- plan for routes to paths which are least damaging
- reduced service
    - serve only the essentials/mvp (if slow: drop pictures, ads)
    - must decide what your core value and deliverable is
- talk to the business owners (not the enemy: "SMEs of customers")
- service level agreements: things can be in an "ordinary broken" state without shutting the whole thing down
- use circuit breakers and safety valves ("dark is better than dead")
- modular delivery
    - use microservices and modules 
    - distributed monolith is still a monolith that fails when a piece goes down
- feature management (feature flag)
    - not just a staging env; prod is full of real human data
- define victory
    - what's mvp or minimum victory?
    - what's not bad? good enough? <-- aim most of it here
    - what's best case? flawless victory?

### ❤️ Modeling Relational Data with Cosmos DB - Steven Faulkner
- For those of us who struggle to move from sql to nosql
- 💡 partition keys should be hierachal

### ❤️ The Science of Great UI - Mark Miller
- How our brains should drive the need for good UI

### ❤️ Be an A11Y: Build Accessible Web Sites for Everyone - Rachel Appel
- 25% of the population at any given time have some accessibility issue
- At some point it's going to be you (temporary or permanently)
- Get over yourself:  make it accessible and care about it
