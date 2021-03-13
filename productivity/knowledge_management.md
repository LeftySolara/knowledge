# Personal Knowledge Management

Recently I've become interested in formalizing my [personal knowledge management](https://en.wikipedia.org/wiki/Personal_knowledge_management) system. Over the years I've tried multiple methods to gather and organize my files, documents, and other things I need to keep around, but it always ended up becoming frustrating to maintain.

This page describes how I'm handling this now.

## Goals

My PKM system needs to be clean, searchable, and maintainable. It also needs to be easy to replicate in multiple places, as my PC isn't the only place I store important information. I also need something that allows for easy separation between things that are private (bank info, addresses, etc.) and things that are public (the page you're reading right now).

What I'm looking for is a system that is:

1. **Easy to maintain**: There should be as little friction as possible when adding, removing, and relocating information. The more time/work it takes to do these things, the less likely I am to actually do it.
2. **Easy to replicate in multiple places**: Because I keep information in multiple places (PCs, phones, paper, etc.), it is useful to organize everything in the same way no matter where it is. This eliminates the complexity of having to remember multiple setups and is extremely useful when using file sync.
3. **Searchable**: Text search is usually the quickest way to find things once a knowledge base reaches a non-trivial size. I want to avoid spending lots of time looking through a large collection of directories just to change one line in a file.
4. **Well-organized**: Even though I primarily use search, documents still need to be easy to find manually for times that I'm using paper or a device with poor search functionality. This is also makes it easier to see a complete overview of what's being stored.
5. **Independent of the tools used to maintain it**: I don't want to uproot my entire system and spend weeks re-doing everything in a different way just because some piece of software was discontinued. This is the primary reason all of my notes are written in [Markdown](https://en.wikipedia.org/wiki/Markdown).

## What I Keep

There's a variety of things I keep in my PKM system, including:

- Notes
- Documents (PDFs, spreadsheets, etc.)
- Bookmarks
- "Read later" lists
- Todo lists
- Calendars
- Contact information

Basically, if it's something I'll need to reference in the future or part of a task that takes more than five minutes of intense focus, it goes into the system.

## My System

I currently use a modified version of the [PARA method](https://fortelabs.co/blog/para/), which I call the IPCAR method.

The basic idea of the original PARA method is that all of your information is stored in four top-level categories: _projects_, _areas of responsibility_, _resources_, and _archives_. I've taken that idea and expanded upon it to fit my own needs.

### Top-Level Categories

These categories are implemented as directories on my PC and as folders in my filing cabinet.

#### Inbox

This is where things are stored until I have time to sort them properly.

I'm often in situations where I need to jot something down quickly and don't have time to worry about where to file it. For example, when I come up with some idea while out grocery shopping. Having one central place to store these things makes it easy to process them during my [daily, weekly, and monthly reviews](https://carl-pullein.medium.com/why-the-daily-mini-review-is-so-important-163d3a8a40b). I also practice [rapid logging](https://help.bulletjournal.com/article/7-rappid-logging) and most of those notes end up in my inbox.

I primarily use my [bullet journal](https://bulletjournal.com/) for this, but also have a note-taking app on my phone for times that my journal isn't accessible.

#### Projects

This is where all notes/documentation for any active projects are stored. I use the [GTD definition](https://gettingthingsdone.com/2017/05/managing-projects-with-gtd/) of "project", which is an outcome that requires more than one action step to complete.

#### Codex

This is the [public knowledge base you're reading right now](https://docs.jalenkadams.me/). It's where I keep any acquired knowledge that I don't consider to be private. It began as a place to [learn in public](https://www.swyx.io/learn-in-public/) and grew into something more after I was inspired by people such as [Nikita Voloboev](https://wiki.nikitavoloboev.xyz/).

#### Areas of Responsibility

This one is identical to the PARA version. An Area of Responsibility is "a sphere of activity with a standard to be mainteined over time". Basically, it's things that I'm responsible for for an indefinite amount of time. Examples include my home, my finances, my health, etc.

#### Records

This is identical to the "archive" category from PARA. It is a place where inactive things from the other categories are stored.

I renamed this from "archive" to "records" because I keep all these categories as directories on my PC and wanted to maintain one-letter tab completion in my terminal.

### Tools and Implementation

I use various tools for maintaining my system.

For task management I practice the [GTD methodology](https://gettingthingsdone.com/) and use [taskwarrior](https://taskwarrior.org/) to manage my task list.

For note-taking I use [Visual Studio Code](https://code.visualstudio.com/) on PC and [Markor](https://github.com/gsantner/markor) on mobile. All of my notes are contained in markdown files on my computers/phone, which satisfies my goal of avoiding dependency on specific software. I also keep physical notebooks for various projects.

For file synchronization I use [Syncthing](https://syncthing.net/).

My calendar is stored in a CalDAV server that I sync to my email client (on PC) and calendar app (on mobile).

## References

- [Hierarchy-First Approach to Note-Taking](https://www.kevinslin.com/notes/3dd58f62-fee5-4f93-b9f1-b0f0f59a9b64.html)
- [PARA Method](https://fortelabs.co/blog/para/)
- [How PARA on Google Drive Can Make Your Life Easier](https://themakingofamillionaire.com/the-para-method-lets-you-find-what-youre-looking-for-ff95cad330fe)
- [The PARA method in Workflowy](https://molodtsov.me/2020/08/para-workflowy/)
- [u/Komatik's modified PARA method](https://www.reddit.com/r/productivity/comments/cw2kz8/whats_your_file_organization_system_digital/ey7vlm1/)
