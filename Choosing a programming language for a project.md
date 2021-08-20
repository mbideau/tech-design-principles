# Choosing a programming language for a project

[![License: CC BY-SA 4.0](https://img.shields.io/badge/License-CC%20BY--SA%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-sa/4.0/)

When you start a new development project, you have to pick a main programming language.
This is not a trivial choice and you are not helped with all the fanatics flame wars on Internet.

I will try to explain how I do it, and why I am more confident in that approach today with a little
experience now (20 years mostly).

In a nutshell: choose the right tool for the job, at the present stage of your project, and
according to your resources.

More in-depth thoughts below.

**Table of content (TL;DR)**
<!-- toc -->

- [Beware of your bias and emotions](#beware-of-your-bias-and-emotions)
- [Context matters](#context-matters)
  - [Expected outcome (quality, delay, features, support)](#expected-outcome-quality-delay-features-support)
  - [Your resources (money, humans, time and skills)](#your-resources-money-humans-time-and-skills)
  - [Interests of the business and the developer might not be aligned](#interests-of-the-business-and-the-developer-might-not-be-aligned)
    - [Business have to consider: developer availability, and communication on the technology chosen](#business-have-to-consider-developer-availability-and-communication-on-the-technology-chosen)
    - [Developers have to consider: their attractiveness, their level of engineering, and fun](#developers-have-to-consider-their-attractiveness-their-level-of-engineering-and-fun)
      - [Beginner developer: choose the programming language balancing career path and fun](#beginner-developer-choose-the-programming-language-balancing-career-path-and-fun)
- [Full rewrite to another language is okay: that allow to prototype quickly first](#full-rewrite-to-another-language-is-okay-that-allow-to-prototype-quickly-first)
- [Know your design patterns, regardless of the language](#know-your-design-patterns-regardless-of-the-language)
- [Combine multiple programming languages into one program efficiently](#combine-multiple-programming-languages-into-one-program-efficiently)
- [Rarely relevant: using a DSL or creating your own language](#rarely-relevant-using-a-dsl-or-creating-your-own-language)
- [Footprint and efficiency: the Sustainable Software Engineering](#footprint-and-efficiency-the-sustainable-software-engineering)
- [Guidance on a programming language](#guidance-on-a-programming-language)
  - [for Backend or Scripts (Non-graphical apps)](#for-backend-or-scripts-non-graphical-apps)
    - [Balance between hackability, performances, deployment, and ecosystem](#balance-between-hackability-performances-deployment-and-ecosystem)
      - [Hackability: super important at the beginning, and always cool](#hackability-super-important-at-the-beginning-and-always-cool)
      - [Performances: only after measuring](#performances-only-after-measuring)
      - [Deployment: don't forget about it](#deployment-dont-forget-about-it)
        - [Note: Unikernels are relevant now](#note-unikernels-are-relevant-now)
      - [Ecosystem: can be specific in bad or a good way](#ecosystem-can-be-specific-in-bad-or-a-good-way)
  - [for Graphical Web, Mobile and Desktop apps](#for-graphical-web-mobile-and-desktop-apps)
    - [The ever rising trend of targeting multiple platforms with one codebase](#the-ever-rising-trend-of-targeting-multiple-platforms-with-one-codebase)
      - [Hybrid apps based on web standards allow to code web+desktop or web+mobile at once](#hybrid-apps-based-on-web-standards-allow-to-code-webdesktop-or-webmobile-at-once)
      - [Cross-platform apps allow to code with one language and deploy to many platforms](#cross-platform-apps-allow-to-code-with-one-language-and-deploy-to-many-platforms)
      - [Targeting a single platform](#targeting-a-single-platform)
    - [Web frontend app](#web-frontend-app)
      - [Follows the same trend than mobile apps: tool chain is getting more complex](#follows-the-same-trend-than-mobile-apps-tool-chain-is-getting-more-complex)
      - [Recent technologies to consider: transpilers, server-side JS, PWA](#recent-technologies-to-consider-transpilers-server-side-js-pwa)
      - [Single Page Apps might not be the good choice if SEO matters](#single-page-apps-might-not-be-the-good-choice-if-seo-matters)
- [Conclusion: choose wisely according to your context](#conclusion-choose-wisely-according-to-your-context)
- [Feedbacks and PR/MR welcome](#feedbacks-and-prmr-welcome)
  - [TODO](#todo)
- [About this document](#about-this-document)
  - [License: CC-BY-SA](#license-cc-by-sa)
  - [Author: Michael Bideau](#author-michael-bideau)
  - [Production: 4 days](#production-4-days)
  - [Made with: Formiko and Vim, plus some helpers/linters](#made-with-formiko-and-vim-plus-some-helperslinters)

<!-- /toc -->

## Beware of your bias and emotions

Try not to be too biased here, and beware of your emotions :

- **excitement** for something new/trendy: you might not anticipate correctly the impact on the
  deadline, or the technical feasibility of what you want to achieve, or the poor quality of the
  ecosystem, or the sustainability of that new language/framework in time, and you risk ending up
  like a balloon bouncing from one language/framework/toolchain to another, and experiment fatigue
  (like the well know [JS fatigue](https://segment.com/blog/the-deep-roots-of-js-fatigue/))

- **reluctance** to learn something new: you might pay a high price for staying with technologies
  that are becoming obsoletes, like not finding developers, or high salary, or an ecosystem
  deperishing, with upstream bug not fixed, a less rapid development, technical difficulties to
  adopt a new paradigm within that language ecosystem, being seen as not innovative or outdated

- **proudness** to not follow the crowd: you might miss the chance to improve, to get interesting
  insights and learn other way to code (better quality, efficiency, maintainability, etc.), and
  ensure your are not doing things wrong, in a deprecated way, or sub-optimally, and sometimes you
  might be late on a technological shift that provides a competitive advantage or is an economical
  imperative (Nokia rings a bell ? 😆). It is less real with a language but for example, the need
  to switch to a new technology stack too late, might happen at a bad time (less resources) and
  add to the struggle/burden/friction of the company/project

- **confidence** in following the crowd: you might trade time of benchmarking and effectiveness of
  a proper technology survey, by following what is popular/common, with the belief that the crowd
  will offer you the best options, but this isn't always true, especially nowadays when big corps
  are releasing their techs/languages with an appealing call to use those, but it might be totally
  overkill for your needs or resources (if you are not a big corp which heart is digital). How
  many web designer/agencies have chosen *React* and then had debugging issues they would have
  solved way quicker if their stack was simpler ? You can also end up in vendor lock-in (and if the
  vendor change its policy in a negative way for you, it might kill your business… not really a
  thing for a programming language, but very real with HTTP API).


## Context matters

Captain obvious here. No wait, there is more to it.

### Expected outcome (quality, delay, features, support)

If you are in a professional mission with a customer (could be an inner company project, that's the
same kind of relationship… almost), that's totally different from a personal side project, or a
student project, and in some way of a startup project.

It all depends on the expectations versus your resources.

A word of caution: if you/your project manager accept infeasible deadline, you can't change that
with a programming language, same apply for quality, if you are not given the means to provide it,
the programming language won't help you, and if you do not work with a proper methodology
(iterations, testing, documentation, etc.), the programming language would not do any good.


### Your resources (money, humans, time and skills)

If your team master only one programming language, and you are asked to produce a quality
project within short delay, the best option is to stick with it. What a surprise, right ?!  
Yes, sound obvious, but it doesn't hurt to state again that, even if a programming language X is
objectively better suited for coding the project P, the real best programming language might be Z
because of your resources.

On the contrary, if you have someone in your team that knows a programming language that other don't
and would provide a significant advantage for the job, and you are certain than you have time to
switch few people to it, go ahead and embrace novelty.

Finally, if you know multiple languages, you have to conduct a study (short or in-depth) to analyse
which is best suited for the job and context.  
Some guidance on that below.

### Interests of the business and the developer might not be aligned

#### Business have to consider: developer availability, and communication on the technology chosen

Not just that, but those are main topics.  
If you choose a technology that is not common, you will have a harder time to find good and
affordable developers to work for you.  
If you choose a programming language that might be seen has deprecated by the clients (often not
aware that you can build a good product without a trending tech), your branding might suffer.

#### Developers have to consider: their attractiveness, their level of engineering, and fun

The technology you master often drive your career path. Rarely for the good reason though
(often recruiters think that not knowing the last hot tech make you a bad dev).

Learning a new language might increase your level of engineering by a lot, and provide you with a
vision you were missing to be more accurate and effective.

Fun is very important. If you don't experience enough joy in your work, it will inevitably affect
the quality of your work, and your life. And learning something new, testing innovation is a
good way to have fun. Sadly, only devs knows…

##### Beginner developer: choose the programming language balancing career path and fun

Above recommendations are even more true for a beginner.

New comers to the market of the developers should have a slightly different approach than others
developers, they should optimize for career path and return in value/expertise/job.
Their goal is not the project in itself, the project is a mean to the end of getting a stable income
as a developer. And in this regard, the programming language should be chosen with the job market
in mind. For example, even if I praise *Python* for being a very good language to learn programming,
beginners would have a hard time getting a job as a *Python developer* with no experience. Turning
to *Javascript+HTML+CSS* or mobile phone apps languages like [Kotlin](https://kotlinlang.org/) or
[Swift](https://www.apple.com/fr/swift/) would provide more opportunities to get a job.

And about market opportunities, it might be counter intuitive, but very old languages can provide a
very high income in company that are stuck with them, and its a very profitable niche market.
For example see : [Cobol](https://fr.wikipedia.org/wiki/Cobol), or
[Fortran](https://fortran-lang.org/).


## Full rewrite to another language is okay: that allow to prototype quickly first

If you accept the entire re-writing of the project to another programming language as a normal step
toward its industrialization you'll have an easier and more efficient choice for the first
programming language of the project.  
Remember that
[premature optimization](https://en.wikipedia.org/wiki/Program_optimization#When_to_optimize) is
more than often counter productive.

At the beginning there is a lot of value in the hackability (so try no compiled language or complex
tool chain stack here), in the way it offers
[Rapid Application Development](https://en.wikipedia.org/wiki/Rapid_application_development),
especially if your team already share a common programming language (not focusing on performance,
yet).

Later, you will choose a programming language and tool chain stack with the experience of running
the product and knowing where to put your money (what kind of technical performance are critical:
network, survival, memory, parallelization, etc.).  
Depending one those optimization you might consider a lot of different programming languages (with
everything that still apply: resources and ecosystem).  
For example see those different paradigms of programming (alphabetic order):

- [ADA](https://www.adaic.org/) real-time and embedded systems
- [C](http://www.open-std.org/JTC1/SC22/WG14/www/standards) / [C++](https://isocpp.org/) low level
  programming, most wide ecosystem of libraries and tools, but no easy packaging/dependencies
  management
- [Common Lisp](http://common-lisp.net/) designed for extensibility
- [Erlang](https://www.erlang.org/) concurrent and failure resistant, generally telecom apps, but
  nowadays also web backends
- [Go](https://golang.org/) easy syntax and lightweight coroutine, efficient tool chain
- [Haskell](https://www.haskell.org/) pure functional programming, science oriented but not only
- [OcamL](https://ocaml.org/) also purely functional programming, industry and science oriented
- [Rust](https://www.rust-lang.org/) safe programming (relatively), can be pure, efficient tool
  chain, wide range of applications

Yes you will need to adapt your developer experience to a new ecosystem after having played with
another one, but that cost might pay back by large amount depending if it has given you a
time-to-market advantage, or a flexibility you were needing at the early stage of your project.

## Know your design patterns, regardless of the language

The more you know, identify and practice design patterns, the more you will be able to
produce quality software, regardless of the programming language.

I highly recommend you to read [Martin Fowler](https://martinfowler.com/) books and
articles which is an expert on that topic.


## Combine multiple programming languages into one program efficiently

Sometimes having two or three programming language co-existing in a single project, each
for a specific task it does well (or that can't be done with another one), is a good option.

It could also be the case when you start **cutting a legacy monolithic code base into smaller
projects**, sometimes developed with more up-to-date languages (may be because your team
has now a younger/newer generation of developers for example).

A combination of libraries that is great to enable different programming languages to interact
together is :

- [Google Protocol Buffer](https://developers.google.com/protocol-buffers/): for
  serializing/deserializing objects
- [ZeroMQ](https://zeromq.org/): for passing object from one language to another with low latency

## Rarely relevant: using a DSL or creating your own language

In very specific case, it might be relevant to use a
[Domain Specific Language](https://en.wikipedia.org/wiki/Domain-specific_language), or even write
your own.  
They are mostly used to describe configurations (like
[Nix](https://nixos.org/guides/dev-environment.html)) and mappings (like
[Vala](https://wiki.gnome.org/Projects/Vala)), and a lot more (as you can see in the *Wikipedia*
link).


## Footprint and efficiency: the Sustainable Software Engineering

Choosing a programming language and its ecosystem will have an impact on the [footprint of your
program](https://en.wikipedia.org/wiki/Application_footprint).  
From an ecological perspective, it is **desirable to minimize that footprint**, but also from
a pure efficiency point of view, sometimes (often not) at the expanse of the developer's comfort
or the program maintainability.

Different kind of footprints:

- **Energy consumption**: the amount of consumption of energy by the CPU, the RAM, the I/O
  operations (disk and network), the disk usage and network bandwidth (including deployment scripts,
  application backups, software dependencies registry/maintenance/web pages, etc.), but also the
  heat that needs to be dissipated by air conditioning or water coolers in datacenters

- **Hardware degradation**: same as with energy but about the impact on the hardware durability,
  how fast will it become used, dysfunctional, or not powerful enough (technological turn over). For
  example the amount of data written to disk, or high usage of CPU triggering a higher fan speed,
  etc.

- **Hardware requirements**: the more specific/rare the hardware, the more it is going to cost
  environmentally because of the excess of consumption of resources to make it in a
  not-industrialized/common process (generating wastes). Some exceptions exist but they are
  exception.

- **Third party services**: the amount of all consumption that is going to be generated onto other
  systems, like third party services, caches, replicated databases, backups, etc.

- **Gray consumption**: is every aspects that the program generates and needs in order to function:
  infrastructures, logistics, physical space and matter, etc. that will generate its share of
  pollution of CO₂ and wastes

The more your program is going to use those resources, the more it will contribute to
infrastructure costs, climate change (energy + CO₂), technological turn-over (need for more
powerful equipment) and pollution by wastes (old hardware is piled in waste land in poor countries)
and matter extraction, etc.

As a software developer, those are the current trends that you can mitigate when it is appropriate:

- **Collection** of all data: very often for little to no value, especially with the promise of an
  overrated future IA. Stop collecting when you don't have a clear value that justify it.
- **Size of media**: do your UI really needs to have buttons in 4K ?! Increase in all media size
  simultaneously at a worldwide scale generate a massive amount of energy consumed by the network
  to reach consumer online devices, when it is not often necessary / do not generate value.
- **Isolation**: in order to have an easier deployment, we tend to use containerisation
  techniques, and virtual environments, etc, which prevent sharing libraries between different
  programs, and other resources duplications
- **Decomposition**: some ecosystems go too far into modularisation which add a lot of meta
  information to manage/store/download in order to use those modules (think about the web page
  for each of it)
- **Complexification** the stack: for good reason, but sometimes (often?) not. Like transpiled
  languages, are they really required for each project ? It might increase by a lot the program
  footprint in the development phase
- **Abstraction**: good for readability and maintainability, but add many thin layers
  on top of each others, which might become significant in terms of resources consumption

Going even further :

- **Reduce data size and internet distance**: by using distributed and/or geo-localised caching
  for example, media compression, optimised font, mostly vector images, etc.
- **Trigger your workloads on day time**: with the emerging use of sunlight as electricity source,
  it makes a lot of sense. But yes, it is tricky to not degrade the user experience. A fine
  knowledge of the different loads might help a lot.
- **Educate consumers and incentivise to produce less**: reducing the light of their devices, not
  sharing all of their shitty/foggy pictures but only the best ones, making good usage of
  hibernation in devices components (turning off wifi/bluetooth at night times, etc.)

Those lists are absolutely not exhaustive, only examples.

The rational is to first **reduce media size**, and especially videos, in front of which, the
program's consumption might appear insignificant, but as more as more programs are deployed and used
everywhere, it seems reasonable to think about their impact. If a good choice can spare a little bit
of resources, and have no impact on the user and developer's experiences, just do it.

At the end, being "green" or "ecological" is not what matters, it is the **efficient usage of the
resources**, regardless of the reputation benefit one will get from it.

More information on that topic:

- Benchmarks on carbon footprint per programming language:
  [https://sites.google.com/view/energy-efficiency-languages](https://sites.google.com/view/energy-efficiency-languages)
  (papers) and open source tools:
  [https://github.com/greensoftwarelab/Energy-Languages](https://github.com/greensoftwarelab/Energy-Languages)
- Small course made by Microsoft (funny regarding their software obesity):
  [https://aka.ms/sse/learn](https://aka.ms/sse/learn)
- Insights from Facebook (forgetting that their own business is an ecological issue):
  [https://tech.fb.com/sustainable-computing/](https://tech.fb.com/sustainable-computing/)


## Guidance on a programming language

### for Backend or Scripts (Non-graphical apps)

Guidance for apps that do not have a graphical User Interface. Either backend/API or desktop scripts.

#### Balance between hackability, performances, deployment, and ecosystem

##### Hackability: super important at the beginning, and always cool

Depending on the technical constraints, you might rather choose a less safe language and less
performing language for a project if being hackable is a major feature.  
This is especially true at the beginning of a project when you do not really know what your are
doing, and it is also totally relevant in an educational context (for student to easily play
with the code, without having to use a compiler and/or dependencies other than the system ones).

For hackability, the interpreted language that are the most common (i.e.: installed by default)
in your context will provide the greatest value.
Most commons ones are:

- [Python](https://www.python.org/) mostly (yes *Java*, *PHP* and *Ruby* are fine, but rarely
  installed by default)
- [Bash](https://www.gnu.org/software/bash/) or an equivalent, see
  [specific guidance about shell language](Specific%20case%20of%20Linux%20shell%20scripts.md)
- [Perl](https://www.perl.org/) is often the language of choice by sysadmins, so it is often present
  in most *Linux* distributions

Sometimes you won't have access to an interpreter/jit-compiler in the system you will run, but
it is a good opportunity to ask if it is not worth deploying one to get the benefit of the
hackability of the code, rather than basically accepting technical software constraints, and having
to re-run the entire developer tool chain only to modify a file (for example).  
For embedded systems using a tiny interpreter/jit-compiler like
[microPython](https://micropython.org/) might be a good solution.

##### Performances: only after measuring

Performances choice will be proven right when testing will comes into play, then you'll know.

A word of caution: please don't think a language is generally badly performing  
I can't stress enough that **the first bottleneck will be your design/algorithm**.  
For example the *Java* language have been bashed for years and still is but few devs know that
there are benchmarks that show that a well designed *Java* software can almost
reach the performance of the same software coded in *C/C++*. As a concrete use case, trading
software often uses *Java* as their performance tool of choice, with design patterns like the
[Disruptor](https://lmax-exchange.github.io/disruptor/files/Disruptor-1.0.pdf) present in the
[LMAX](https://www.lmax.com/) software.

##### Deployment: don't forget about it

People often forgot about the deployment and maintenance. Less and less true nowadays with the
[DevOps](https://en.wikipedia.org/wiki/DevOps) movement, and containerization. Hopefully,
developers will catch up with sysadmins view.

###### Note: Unikernels are relevant now

The programming field might also change again a little bit with the arriving of the
[unikernels](https://fr.wikipedia.org/wiki/Unikernel).
Yes, its been 30 years that they are arriving 😅, but they tend to be more and more
relevant nowadays.
My tips here, is to follow that guideline when choosing for a unikernel or a full distro
container :

- if the number of dependencies / library is low, and are not focused on security,
  choose a unikernel (dedicated to the programming language), it would be easier to deploy
  and maintain, with huge performance gain (x2).

- if too much libraries or security focused, choose a full distro container, because a
  whole team would be managing the dependencies's hell and security updates for you, it is like
  outsourcing that job for free, by paying little extra Mb in the size of your container.

##### Ecosystem: can be specific in bad or a good way

The ecosystem is harder to grasp, but it boils down to the following : if the programming
language expose some specifics features, or is designed for a specific job, expect libraries
tools and support to be driven and specialized too.
There is kind of a convergence or expansion of many specialized programming languages those
last recent years, but the communities haven't changed that much still (to my opinion).


### for Graphical Web, Mobile and Desktop apps

Guidance for a language in the context of (graphical) web, mobile and desktop apps.

#### The ever rising trend of targeting multiple platforms with one codebase

It boils down to 2 type of SDK or programming tool chain and deployment which I recommend
you to learn, as a career leverage and engineering perspective.

I have not enough recent experience to recommend one over the other, so that would be up to you.

My itch is that the hybrid app is faster to code and easier to deploy, but the cross-platform have
less technical limitation (like integration with third party libraries) and is performing better.  
Especially the *ReactNative* is an obvious choice if your are already coding in *React* or have
that skill.

##### Hybrid apps based on web standards allow to code web+desktop or web+mobile at once

A decade ago appeared SDK like
[Cordova](https://cordova.apache.org/) and [Ionic](https://ionicframework.com/), or
[Titanium](https://www.appcelerator.com/mobile-app-development-products/), that allow to code for
the web and all the mobile platforms at the same time, and are still relevant today. It uses a
Native Runtime wrapping the device's API and exposing it to the embedded web code you developed
with.

Since few years there is [Electron](https://www.electronjs.org/), that targets desktop apps written
with web standards. It packs your web app with [Chromium](https://www.chromium.org/), the
*Google* web browser (without some of its proprietary bits), as its Native Runtime.

So in both case it is really a web app, embedded into a *runner* . That shows that you can use the
web standards HTML/CSS/Javascript to develop, and reuse that code to target two platforms/ecosystems
at once.

##### Cross-platform apps allow to code with one language and deploy to many platforms

Also a decade ago, appeared SDK like
[Xamarin](https://dotnet.microsoft.com/apps/xamarin), now there is
[ReactNative](https://reactnative.dev/).  
They are both, transforming your code made with a single programming language into a Native
Application, regardless of the target platform.

I have recently discovered the [Android JS](https://android-js.github.io/) project, that allow to
code in Javascript directly for the Android platforms. I understand that it is transpiled in a way
then compiled to a Native App (no Runtime wrapper I think, but I am not sure). Might be worth
investigating to reuse web codebase.

Another initiative worth mentioning is the [Haxe](https://haxe.org/) project, which it a
transpiler of *Haxe* code to almost any other programming language. It could be seen as a
cross-platform tool even if it is less direct, not having its own Native Runtime/VM running by
default on the targeted platform, and requiring to compile the transpiled language towards the
platform specs.

##### Targeting a single platform

I recommend to use what the platform's offical SDK is and its programming language. Why ?  
Everything will be easier: finding resources (developers, support, libraries, deployment, etc.).

For example [Swift](https://www.apple.com/swift/) for the *Apple* ecosystem,
[Kotlin](https://kotlinlang.org/) for the *Google Android* one (but it can also compile for *iOS*),
or [C#](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/) on *Microsoft*
machines.
On *Linux* the choice is between two graphical toolkit [GTK](https://www.gtk.org/) and
[QT](https://qt-project-org.herokuapp.com/), but both have a lot of bindings for almost any
language.
So the choice might be guided with the same
[principles that applies for non-graphical apps](#guidance-on-a-language-for-non-graphical-apps),
described above.

If you don't want to go with the recommended programming language prepare for some troubleshooting.
It might be worth it in some cases though if you have specific constraints, like having to learn
that language, or can't easily use the SDK in your environment.

The important question is : "why targeting a single platform" ?  
It might be a good choice to first start with a single chosen platform's ecosystem (for its
app'store conditions, or a dependency to another app which is better in that environment), and then
expand to other platforms later on.

#### Web frontend app

##### Follows the same trend than mobile apps: tool chain is getting more complex

The frontend of web app follows a similar pattern that mobile apps. Their programming tool chain
tend to become more complex to allow for a better quality and better re-usability.

##### Recent technologies to consider: transpilers, server-side JS, PWA

In addition to above hybrid/cross-platform SDK, there are three technologies that should be
considered :

- [Transpilers](https://en.wikipedia.org/wiki/Source-to-source_compiler) (turn another language
  into Javascript)  
  It could improves your quality of code, and facilitate deployment… at the expanse of a more
  complicated tool chain. So use those with caution.  
  Well known are: [CoffeeScript](http://coffeescript.org/) and
  [Typescript](https://www.typescriptlang.org/).  
  I like two recent ones that offers a big improvement on code quality: [ELM](https://elm-lang.org/)
  derived from *Haskell*, and [Reason](https://reasonml.github.io/) derived from *OCamL*

- [Nodejs](https://nodejs.org/en/) (server side Javascript)  
  The ability to code in only one language and reuse a lot of pieces in the server and client
  (browser) might play a big role into saving costs and a better maintainability.  
  But it might make the packaging less convenient, and harder to use specific code targeting the
  server or the client without degrading the readability of the code.  
  A good technology that should be prototyped before adopting it blindly.

- [Progressive Web App (PWA)](https://en.wikipedia.org/wiki/Progressive_web_application)
  (make website look like a Native app, with its icon in the app launcher and its own window)  
  It is desirable that this technology would become more mainstream, but for now there are technical
  limitations (desktop support, browser storage, managing versions, and security) and also consumer
  acceptance or understanding.  
  In the case that you manage the targeted machine, like Kiosk, or Devices/Mobiles for a dedicated
  purpose, it might be a good choice though.  
  For more informations: a good [summary of the situation/future](https://firt.dev/pwa-2021/), and
  an up-to-date [compatibility list](https://firt.dev/notes/pwa/).

##### Single Page Apps might not be the good choice if SEO matters

A new trend in the web application development is to use frameworks that are made for
[SPA](https://en.wikipedia.org/wiki/Single-page_application), but an SPA
is not always what you want, especially if have a lot of content and
[SEO](https://en.wikipedia.org/wiki/Search_engine_optimization) matters.  
In that case, I recommends to create two web apps, one to expose the content in an SEO friendly
manner, and another one for the backoffice or game or whatever is SPA required for.

If your project is a home web page presenting a product or a company, it would be counter
productive to use an SPA approach and you should definitely avoid it.


## Conclusion: choose wisely according to your context

Think before jumping on choosing a programming language. There are many aspects to consider, some
can have a huge impact on your project, other just being optimal or convenient.  
The number of programming language is increasing, some allows to targets multiple platform at once,
others tend to be very specific but very good at what they do.  
And don't forget that it is a okay to prototype, then rewrite with another better suited language.


## Feedbacks and PR/MR welcome

If you have any comments or directly wants to edit/contribute to the document, feel free to send me
a mail/patch/PullRequest/MergeRequest, I would received/accept it with pleasure.

### TODO

- [ ] add more sources, may be videos


## About this document

### License: CC-BY-SA

[![License: CC BY-SA 4.0](https://licensebuttons.net/l/by-sa/4.0/80x15.png)](https://creativecommons.org/licenses/by-sa/4.0/)  

Copyright © 2020-2021 Michael Bideau, France  
This work is licensed under a
[Creative Commons Attribution 4.0 International License](http://creativecommons.org/licenses/by-sa/4.0/).

### Author: Michael Bideau

Michael Bideau, France

### Production: 4 days

It took me about **4 full days** to write that document, from version 1 to the one you see now.

If you value that work, think about saying thank you, giving feedback, and sharing it.

### Made with: Formiko and Vim, plus some helpers/linters

I started with [formiko](https://github.com/ondratu/formiko), then used
[mdtoc](https://github.com/kubernetes-sigs/mdtoc) to generate the table of content, and finally used
[vim](https://www.vim.org/) with linters to help catching mistakes and badly written sentences:

- [mdl](https://github.com/markdownlint/markdownlint)
- [proselint](http://proselint.com/)
- [write-good](https://github.com/btford/write-good)
