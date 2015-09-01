
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

A [Guide to Using GitHub with W3C](http://w3c.github.io/) has been produced. It can certainly
welcome more data, but hopefully the first stab that is there is enough to get the ball rolling and
to make it worth maintaining.

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
Midgard](https://labs.w3.org/hatchery/midgard/). They are operational.

If this tool gets used regularly it will require maintenance, and will likely require some features
to be added to it (at the very least some new filters, which are very easy to write). If it is 
popular it will likely be necessary to add new sources of events (which is also easy and modular).

The systeam will need to be involved at the very least in running the application; someone will need
to be in charge of its maintenance and continued development. The stack is Node/CouchDB/React.

At some point this should definitely be moved to a URL that is *not* my hatchery on labs.

I will be writing a specific and detailed document about installing and running it, as well as a
map of the code and details about how to work on it so that someone jumping in can do so (hopefully)
easily.

### GitHub Backup

The unified feed already backs up all GitHub information that is produced *except* the actual
repositories. In order to back the repositories up, the
[gh-backup](https://github.com/w3c/gh-backup) tool is available. It relies (lightly) on the unified
feed in order to easily know which repositories have changed. It can run autonomously and maintain
a full backup of the *public* repositories (private ones are another matter, not handled).

## Future Deliverables

A number of things were listed in the Modern Tooling document that I believe are worth doing but
haven't been done at this point.

### Notifiers

Several people requested the ability to get notifications by email or on IRC for some events of
interest. The general idea is to use the unified feed for that purpose, and have daemons that can
rely on it in order to push notifications to email or IRC.

The unified feed already knows of filters that provide a useful view over a subset of its content.
That would probably be the selection mechanism as this keeps the notifiers simple: all they need to
do is query a filter (and have a configuration that maps filter to IRC channel or to an email 
address).

There are then two ways to implement them. The simple way is a cron job which polls the filters. The
more involved way, which I would have headed towards had I stayed on, would have been to have the
unified feed essentially work with ZMQ (or similar) in order to dispatch pre-munged events when they
occur. The latter is more initial work, but is cleaner and would prove more advantageous the more
tools plug into it. The decision will have to be made by whoever picks this up.

### Group Pages

This was initially listed as a priority, but was replaced with the repository manager that got
bumped up for the WICG needs.

A subset of the use case, I would say the more useful subset, is already being addressed by the
Apiary project (currently private, hence unlinked) that ddavis and tripu have been working on.

For the immediate future I think that the focus should be on Apiary. Once that has shipped and is
being used, it will be interesting to revisit follow-up use cases but they are of a lesser priority
than the information that Apiary exposes (which is what's in the W3C DB all nicely up to date and
most frequently outdated on group pages).

### Mailing List Interface

This is by far the most complicated part of the project. The goal is to expose a mailing list 
archive interface that is up to speed with modern expectations, similar to what was done with
[ES Discuss](https://esdiscuss.org/).

There is no point in undertaking this project unless it is staffed properly, it is not something
that can easily be done on the side. Email is hard in general, and the volume of data makes it
harder, as likely do the performance requirements for ingestion.

My plan was as follows. Use [EmailJS](http://emailjs.org/) to ingest both arriving email and the
archives into CouchDB (but keeping the attachments on the FS). EmailJS is a tried solution, it
notably powers the email system in FirefoxOS.

Once in CouchDB, views can be used to expose individual posts, threads, lists, time-based windows
(without the month rollover issues we have with threading today), and possibly a number of other
things of interest. FTI would remain in Sphinx where it is today (though eventually the URLs it
returns might change).

On top of this, a React application could be built (isomorphic if need be) to explore and render the
email.

My expectation was that this would take me two or three months full time to put together.

### Discourse

There are two topics here. One is whether the W3C needs to have an “official” Discourse instance
which it can use for its groups and the such. The other is what to do with the content of the 
initial Discourse experiment, which was mostly about getting new ideas from the community.

Since the WICG has been launched, in part as a continuation of the broader developer involvement
project of which Discourse was a part, they have inherited that content. Whether the content should 
stay there or be moved to W3C is a “political” decision that is outside the boundaries of this
document. In either case it's a straightforward step to export/import content.

Installing Discourse is simple; the bigger questions are about the fact that the stack does not
match what the systeam usually uses.

### Interactivity in Specifications

Specifications should be spruced up with some interactive features such as finding all usage spots
for definitions, easy linking to sections, bugs can be filed from a selection, etc. There is value
in having a common library for this so that people don't have to think about it, tools can generate
the right markup, users can expect consistency.

I don't think that this falls to the systeam. There was an embryonic start for this called
[specstatic](https://github.com/darobin/specstatic) which can be picked up. My recommendation is to
fold this into the TR Design project (by filing a bug) and calling it a day.

### Live Examples in Specifications

The idea here is to make it possible to embed live examples in specifications, using a system
similar to [Dabblet](http://code.webplatform.org/). This would be extremely valuable in making our
specifications more useful and more readily understandable as they get implemented.

I believe that this can be folded into TR Design as well.

### WebIDL Checker in Specberus

Specberus has the ability to bring in external checkers; it would be useful for it to plug into the
WebIDL Checker. This can probably be handled as a bug on Specberus. PLH and Dom have registered
interest in doing this as a geek week project.

### Etherpad

It would be very useful to have access to Etherpads, that could make use of W3C's LDAP, etc. The
alternative is that people use random pads elsewhere, we lose content. I believe that this is
something that the systeam can carry out at some point, on its own schedule.

### WBS Prettification

Quite a few of our users find WBS daunting. One first step that we could take would be to re-style
it. I believe that this can be done relatively easily, simply by applying some CSS. Further 
improvements can probably be made using some script, but just styling could go a long way.

I don't believe that this is a huge undertaking. Dom has indicated interest in doing this as a 
geek week project.

