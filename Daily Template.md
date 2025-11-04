[[Shopping List]]

## Long Term Focus
```tasks
tag includes #goal
not done
```

## Tasks
### Calendars
<%*
var events = await app.plugins.getPlugin('ics').getEvents(moment(tp.file.title,'YYYY-MM-DD'));

if (events.length === 0) {
    tR += "No events due!\n";
} else {
    events.sort((a,b) => a.utime - b.utime).forEach((e) => {
        const eventDate = moment.unix(e.utime).format("YYYY-MM-DD");
        tR += `- [ ] #task #calendar ${e.summary} 📅 ${eventDate}\n`;
    });
}
%>
### Overdue
```tasks
not done
(starts before <% tp.file.title %>) or (no start date)
due before <% tp.file.title %>
```

### In Progress Tasks
```tasks
has start date
starts before <% tp.file.title %>
due on or after <% tp.file.title %>
not done
sort by due
```

### Today's Tasks
```tasks
not done
due on <% tp.file.title %>
```

### Due tomorrow
```tasks
not done
due after <% tp.file.title %>
due on or before <%* 
const noteDate = moment(tp.file.title, "YYYY-MM-DD");
const tomorrow = noteDate.clone().add(1, 'day').format("YYYY-MM-DD");
tR += tomorrow;
%>
```

### No due date
```tasks
tag do not include #goal
not done
no due date
```

### Done today
```tasks
done on <% tp.file.title %>
```
# Today's Journal
