# Getting Things Done

Getting Things Done is a time management methodology described in [David Allen's famous book of the same name](https://gettingthingsdone.com/). Below is my understanding of how GTD works and some descriptions of how I implement it in my own life.

## Overview

There are a lot of things that enter my mind throughout the day \(inputs\) and I need to decide what to do with them \(outputs\). Inputs can be things like phone numbers to remember, errands that need to be run, or meetings to attend. Outputs would be things like putting events in my calendar or adding tasks to my to-do list.

The goal is to capture all my inputs and put them into a trusted system so I can deal with them later on. This removes the burden of having to remember everything.

## Steps

There are five basic steps to the GTD methodology: 1. Capture 2. Clarify 3. Organize 4. Reflect 5. Engage

### Capture - Collect what has your attention

This one is simple. I just make sure to note down _everything_ that comes to mind as an input. It doesn't matter where this info is kept, as long as all of it gets captured. In my case, I write everything in my [bullet journal](https://bulletjournal.com/).

### Clarify - Process what it means

Once everything is collected in my inbox, I take some time to process it all and decide what to do with each input. This needs to be done regularly, as letting a backlog accumulate will just make this more difficult.

I usually do this once or twice a day. It helps remove friction from the system.

### Organize - Put it where it belongs

Once I know what something is, it gets put in its proper place. Here is where things usually end up:

- If it's something actionable, it goes into my task management system. I use [taskwarrior](https://taskwarrior.org/) for this.
- If it's time-sensitive, it goes on my calendar.
- If it's reference material I might need later, it goes into my personal notes or on this wiki. For this I keep a collection of local Markdown files that sync between my machines. For file sync I use [Syncthing](https://syncthing.net/).
- If it's not important, it gets trashed and I don't think about it anymore.

This is also where contexts come in. A _context_ is basically just a tool, thing, place, or person you need to get something done. For example, I have a "home" context for things that need to be done at home or a "phone" context for all the calls I need to make. Other contexts include work, school, my PC, etc.

### Reflect - Review frequently

Each week I like to take time to clean up and maintain my lists. Skipping this just allows things to pile up, which defeats the whole purpose of have a system in the first place.

### Engage - Simply do

I think this one speaks for itself.

## My Process

This is a description of how I use the GTD methodology in my own life to organize my tasks.
I've tried many different things over the years and this is how I'm currently doing things.
Remember, there is no "correct" way of doing things. The best way is whatever works _for you_.

### Monthly Review

On the first day of each month I take the time to sit down and go through my entire task list,
no matter how long it is. Doing this helps streamline the weekly and daily reviews that I'll be
describing next.

I like the way I'm doing this now, as it works regardless of whether I've been keeping up with
it. Whenever I go through down periods and fall behind, it's difficult to make myself start again
because of the extra work needed to catch up. With this method I can just to the same steps
as usual, reducing the friction and making me more likely to re-form the habit.

The exact process I follow is:

1. Create a monthly spread in my bullet journal. This spread consists of a calendar page
   and a task page. I use a format very similar to the original version shown on the
   [bullet journal website](https://bulletjournal.com/pages/learn).
2. Go through my calendar and add existing events to the calendar page in the monthly spread.
   I use Nextcloud as a calDAV server for storing events, and sync that to various clients on
   my PCs and mobile devices.
3. Clean out tasks from taskwarrior. Here I just mark tasks as done if they're already complete,
   or delete them if they're no longer relevant. This reduces the amount of stuff you have to
   look at and filter through while organizing things in later steps.
4. Brain dump. At this point I look through my GTD trigger list and add everything that comes to mind
   into my taskwarrior inbox. My setup uses an `in` tag to specify inbox items that still need
   to be reviewed/processed, as described [here](https://cs-syd.eu/posts/2015-06-21-gtd-with-taskwarrior-part-2-collection).
5. Process all pending tasks in taskwarrior. This will include all tasks added in the previous steps
   and any tasks that were already there. Here I update all tasks with info like due date, recurrence,
   detailed descriptions, tags, and which projects they belong to. This is also a good time to check
   which tasks are being blocked by other tags and which ones need a `wait` filter applied.
6. Add any tasks with a due date during the current month to the bullet journal monthly spread.
7. Do the weekly review process (described below).
8. Do the daily review process (described below).

### Weekly Review

The weekly review is shorter and much less formal than the monthly. I used to keep weekly spreads
in my bullet journal but it became too much work with too little payoff for me. Right now my weekly
process doesn't involve my bullet journal at all.

At the start of each week, I review all the pending tasks in taskwarrior and make any needed updates.
I also process everything in the inbox and make sure I have a good idea of what my priorities should
be for the week. The is the time to shift around due dates if some things are taking longer than expected,
and mark tasks as `started` if they're in progress.

### Daily Review

This part is meant to be quick and require as little work as possible, as it's supposed to be done
first thing in the morning.

In my bullet journal I use a daily log format very similar to the one on the [bullet journal website](https://bulletjournal.com/pages/learn).
Each morning I look at my calendar and add any upcoming events to the daily log. This gives a godd estimate
of how much time I'll have for my tasks that day. I then look at the top 10 or so items in taskwarrior
and add them to the daily log. Which items are added depends on how important they are and how much time
I have available that day. Taskwarrior is pretty good about assigning priority on its own, and things
should be more or less organized already because of the weekly and monthly reviews.

## Links

- [Asian Efficiency - GTD 101: The Beginner's Guide to Getting Things Done](http://www.asianefficiency.com/task-management/gtd-intro/)
- [GTD in 15 Minutes - A Pragmatic Guide to Getting Things Done](https://hamberg.no/gtd)
- [GTD with Taskwarrior](https://cs-syd.eu/posts/2015-06-14-gtd-with-taskwarrior-part-1-intro)
