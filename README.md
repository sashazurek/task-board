# task-board
Experimenting with ways to model day-to-day tasks to hopefully figure out a method better than the whiteboard :)

## Why?
I'm neurodivergent, and have been struggling for pretty much my entire sentient life with organizing my day to day life -- keeping track of events, dates, chores, tasks, etc.
In the process of growing up, I've tried many different solutions for keeping track of things:

- Calendars
    - These kinda work, so long as the actual events are shoved in my face regularly.
    - Calendars only work for *timed* events -- occuring on a specific day, at a specific time range. They do not work for untimed events, events with floating and not-yet-defined times, and trying to represent *tasks* would bloat your calendar to information overload hell. There's also not really a good way to define dependencies.
- "Reminders" on my phone
    - These also kinda work, especially for very simple one-off tasks. They are not great at representing tasks with dependencies, tasks with temporal needs, and often can only be represented as a simple list. The best use case i've had for the Reminders app is for groceries, which it works very well for (check off an item, it's removed from the list.)
- A physical planner
    - Most of my schooling we were given planners. Most of my schooling my planners were very inaccurate, out of date with life, and not very useful to me generally. This is likely because they're too easy to ignore -- especially in an age of rapid technological intrusion into life, as I had growing up in the 2000s.
- A whiteboard
    - This has an advantage over a planner as you can place a planner in a hard to ignore location. This is what I'm currenly using -- I have a whiteboard permanently affixed to the wall near my desk.
    - You can represent many different things here, though not anything particularly well. 
        - A simple to-do list -- like a list of daily tasks -- works pretty well, just cross off what's done and erase the checks at the beginning of every day.
        - Tasks with periodic due dates -- like paying a bill, or scooping a litterbox -- also can be represented pretty well.
        - One-off tasks are easily represented, but easily ignored. Without the discipline to force yourself to check the one-offs, you can often ignore them for prolonged periods of time. They're always visible, but not always *noticable*

Something none of these methods can really capture well is task _dependencies_. Take, for example, this list of morning tasks:

- Brush teeth
- Make and eat breakfast
- Take medication
- Apply sunscreen to face.
- Apply lotion to face.
- Wash face.

Some of these tasks have implicit dependencies -- it makes no sense to apply lotion and sunscreen _after_ you wash your face, for example. Some of these tasks have logical connections -- depending on your medication, it may be necessary to take it after you have eaten food. A simple list, as is usually represented in reminders apps, is only really capable of representing a do-this-then-this-then-this relationship. Anything more complex would require additional modelling. Take, for example, this simple "metatask"

- Skin care routine
    1. Wash face
    2. Put on lotion
    3. Put on sunscreen

Pretty easy to model -- these things have a very simple relationship to one another, and you either would write them separately, or just understand when you see "skin care routine" it means those three things. But what about more complex relationships? 
- Sometimes tasks have co-dependency -- while it doesn't matter when each of these tasks are done temporally, they must be done at the same time
- Sometimes, your daily task is dependent on a periodic task -- taking daily medication is dependent on getting your medication refilled in a timely matter, for example.
- Sometimes tasks are more important than one another -- it's far more important to take one's medication than to keep your skincare routine
- Sometimes tasks have fluctuating importance, whether it's throughout the day, to the user's personal circumstances, etc

How do you represent these relationships in current methods of task organizing? Poorly, if at all. In order to keep track of one's life, you have to use many different tools that don't really talk to one another. Keeping track of life is difficult!

So my goal here is to create some kind of system that can not only represent the most complex things we need to do in our lives, but can also effectively push you to do these things :)

Some ideas:
- A sunscreen task, which fluctuates in importance (i.e. how urgently you are reminded) based on the UV index
    - This could probably be implemented through a user-defined method in the taskfile
- Leveraging push notifications to periodically remind the user of certain tasks
- Suggesting next tasks for user based on the task they just finished

## So what's the current goal?
In order to do anything of note with this desire, we need a way to represent tasks in a composable and expressive way. That's the first goal -- create a representation of tasks in code.