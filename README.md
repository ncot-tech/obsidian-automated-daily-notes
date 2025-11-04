# Obsidian Automatic Daily Notes

There are various plugins for Obsidian that help you keep a daily journal or simply see a new page to write on every day. I wanted something more complex that would give me

* A daily plan of what I need to do, and a place to keep notes from each day
* A weekly review of what I did during the week, showing tasks I had completed, and not yet completed
* A monthly review that let me plan ahead for the coming month, and to see if I managed to achieve what I planned the previous month
* A yearly review of the whole process

While there are plugins to do this, none of them did the simple thing of opening the relevant notes when necessary, or were able to function quite in the way I wanted. So I made my own using the Tasks plugin and the Templater plugin.

The purpose of this setup is to keep me organised. I can plan what to do, but unless there's a daily reminder I will forget. I can't be trusted to look at yesterday's todo list, or to sit down at the end of the day and manually copy my day's incomplete tasks into tomorrow's. Or to go and look at my future plans page to see what's coming up.

This setup has zero effort in maintaining it, but doesn't send me easily ignored repeat reminders on my phone. I don't need to schedule when on the day a task needs completing. I just need to say "On Thursday do XYZ". I will then make time to do it.

## Note Storage

All my notes are stored in a "Notes" folder, organised by year and month. Each daily note is named after the current date in YYYY-MM-DD format. For example I have a structure like this:

```
Notes/
    2025/
        2025-Review
        10/
            2025-10-16
            2025-10-17
            ... etc ...
            Week-43-Review
            October-25-Review
```

## Daily Notes

These are what I look at every day and are a combination of task list and place for me to write down what I did, random notes to remember, things to do in the future, etc.

The top half of the page is taken up by Templater and Tasks generated lists
* Weekly Focus: Tasks marked with #goal that I need to remember
* Overdue: Tasks that are overdue
* In Progress Tasks: Longer running multi-day tasks
* Today's Tasks: Things I need to complete today
* Due Tomorrow: What's coming tomorrow, so I don't forget
* No Due Date: Tasks that need doing, but haven't a specific date
* Done Today: Tasks that I completed today

This is a lot of lists of tasks, but that's the main point. I know what I want to do, and find it quite easy to plan these tasks, but then forget all about them if they're not literally staring me in the face every day.

This isn't a system aimed at people who avoid doing tasks for whatever reason. I simply forget they exist, and without the prompt, won't do them.

After this is a section simply titled **Today's Journal** where I can make notes on what I did. I've discovered I'll also create tasks in here too, possibly based on tasks I completed today. It allows me to plan a task to be completed in the future, and then forget all about it until the necessary time.

## Weekly Review

This follows a fairly standard reviewing system where I look back on the week and identify what worked, what didn't and what changes I might make.

There is also a list of tasks I had planned for last week and for this week. This lets me see on one page what I got up to, and what things I didn't do.

All the incomplete tasks can then be reviewed to see if they're still worth doing.

## Monthly and Yearly Reviews

These are similar, but less detailed. There are no task lists in them, by the end of the month I will have seen my weekly tasks four times, I'll know what worked and what didn't. The monthly and yearly reviews are there to keep me on track for longer projects or to remind me to look at my calendar to see what is coming up.
## Organising Tasks

Since the Tasks plugin can pull in tasks from anywhere inside Obsidian, it doesn't matter where I make them. I don't have to remember to create a special "tasks" file, or go back to yesterday to look at my old tasks.

However, to help plan things better I do have a **Repeating Tasks** page where all my repeating tasks live, and each month tends to accumulate tasks to do in the following month.
