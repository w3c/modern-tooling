
# Next in Modern Tooling

The [Modern Tooling Project](http://w3c.github.io/modern-tooling/) is nearing the end of its first
phase, and I am leaving. This is a good time to look at the many ideas that were captured in the 
report, to figure out which of those are truly important, what that entails, and to look at what has
been developed with a view on upcoming development and maintenance of these new tools.

The approach of the initial document was to capture as much as possible in order to get a feel for 
the vast number of things that people would like to have, with a thin layer of prioritisation on 
top. The goal of this here document is on the contrary to only cover what I consider to be 
absolutely vital to cover. Anything not covered here is, in my humble opinion, not very important.
This document serves as a status checkpoint and suggested roadmap for the next steps, in a very
synthetic manner.

## New Modern Stuff

These are the things that have already been worked on, and that are planned to be finished by the 
end of August. By “finished” I mostly mean that they are up and operational; it does not mean that
no work on them will need to be done.

### GitHub Guide

A [Guide to Using GitHub with W3C](http://w3c.github.io/) is in the works. At this point it only has
a landing page, but I will be adding content in the coming days and weeks. After I've added content,
it ought to be usable but will certainly require some maintenance and the occasional addition.

This is *not* something that I would expect the systeam to take over.

It will be necessary for someone to become the point of contact for this document; but I expect the
W3C community to carry out the maintenance by itself. We basically just need someone to review the
likely rare pull requests.

### Developer Landing Page

[@guibbs](https://github.com/guibbs) took care of [this page](http://www.w3.org/developers/tools),
which is online and operational.

I don't have anything specific to add at this point.

### TR Styles

PLH has taken this over, and Elika is running it for this year. A 
[repository](https://github.com/w3c/tr-design/) is available and progress is being made.

I don't have anything specific to add at this point.

### Repository Manager

What this tool does is make it possible to flag GitHub pull requests as acceptable or not depending 
on whether the people who have contributed to them are part of the right group. It does that by 
enabling the bridging of the W3C user database and GitHub contributors.

This is not a small chunk. An early release is [online in my 
Hatchery](https://labs.w3.org/hatchery/ash-nazg/).

If this tool does indeed get used on a regular basis (which is certainly the plan), it will require
maintenance. I will try to weed out as many bugs as possible before leaving, but we all know the 
reality of software. It would also be desirable for the W3C to capture GitHub usernames in its DB
and to expose that through its API. When that happens, the application will need to be updated.

The systeam will need to be involved at the very least in running the application; someone will need
to be in charge of its maintenance and continued development. The stack is Node/CouchDB/React.

At some point this should definitely be moved to a URL that is *not* my hatchery on labs.

I will be writing a specific and detailed document about installing and running it, as well as a
map of the code and details about how to work on it so that someone jumping in can do so (hopefully)
easily.

### Dashboard & Unified Feed

This is a duo of tools. The unified feed is an API that can receive events (typically from GitHub)
or poll for information (for instance from RSS) and store all of that information in a unified
manner that can then be filtered usefully. The dashboard is a Web interface that talks to that
API.

Hatchery has running versions of both the [unified feed, aka 
Pheme](https://labs.w3.org/hatchery/pheme/) and the [dashboard, aka 
Midgard](https://labs.w3.org/hatchery/midgard/). They are operational but I will be modifying some
parts relatively extensively.

If this tool gets used regularly it will require maintenance, and will likely require some features
to be added to it (at the very least some new filters, which are very easy to write). If it is 
popular it will likely be necessary to add new sources of events (which is also easy and modular).

The systeam will need to be involved at the very least in running the application; someone will need
to be in charge of its maintenance and continued development. The stack is Node/CouchDB/React.

At some point this should definitely be moved to a URL that is *not* my hatchery on labs.

I will be writing a specific and detailed document about installing and running it, as well as a
map of the code and details about how to work on it so that someone jumping in can do so (hopefully)
easily.

## Future Deliverables

### Notifiers

### GitHub Backup

### Group Pages

See apiary as part of this.

### Mailing List Interface

### Discourse

### Interactivity in Specifications

### Live Examples in Specifications

### WebIDL Checker in Specberus

### Etherpad
