<%*
const filePath = tp.file.path(true); // e.g., "Journal/2025/10/week-42-review.md"

const pathParts = filePath.split("/");

// Adjust indexes if your folder structure is different
const year = parseInt(pathParts[1], 10); // 2025
const month = parseInt(pathParts[2], 10); // 10

const filename = tp.file.title.replace(/\.md$/, ""); // "week-42-review"
const match = filename.match(/week-(\d+)-review/i);
if (!match) throw "Filename not in expected format 'week-XX-review'";
const weekNum = parseInt(match[1], 10); // 42

const startOfWeek = moment().year(year).isoWeek(weekNum).startOf('isoWeek'); // Monday
const endOfWeek = moment().year(year).isoWeek(weekNum).endOf('isoWeek');     // Sunday
tR += `Week starts: ${startOfWeek.format("YYYY-MM-DD")}, ends: ${endOfWeek.format("YYYY-MM-DD")}`;

// Create monthly patreon newsletter if not already created
// Get the folder path by slicing off the filename
const folderPath = filePath.substring(0, filePath.lastIndexOf("/")); // "Journal/2025/10"
const newsletterName = `Patreon Newsletter ${year}-${month}`;
const newsletterPath = `${folderPath}/${newsletterName}.md`;

if (!app.vault.getAbstractFileByPath(newsletterPath)) {
  await app.vault.create(newsletterPath, `# ${newsletterName}\n\n`);
}
%>
## 1. Review the Week

**Prompts:**
Looking at only things in Obsidian...
- What got completed?
- What slipped or needs moving forward?
- Any deadlines or events missed or added?
- Any tasks now irrelevant or blocked?

**Checklist:**
- [ ] Review completed tasks
    - Which ones need putting in <%* tR += `[[${newsletterName}]]` %> or blog post
- [ ] Check for overdue tasks
- [ ] Check for unscheduled tasks
- [ ] Close or reschedule them

### Write review here
*Write as bullet points*
## 2. Projects & Priorities
**Prompts:**
Looking at things in [Nextcloud Decks](https://xxxxxxxx/apps/deck/)
- Which projects are active right now?
- What progress did you make on each?
- Any projects that need more attention, delegation, or pausing?
- What is coming next week?

**Checklist:**
- [ ] Looked at what videos are due soon and put them in here as tasks
- [ ] Adjusted Nextcloud decks to match progress

## 3. Plan the Coming Week
**Prompts:**
- What’s due next week?
- What 1–3 outcomes would make the week successful?
- What obstacles can you anticipate?

**Checklist:**
- [ ] Look at calendar and decks for next two weeks
- [ ] Identify deadlines and events, including at work
- [ ] Define 1-3 clear goals
- [ ] Create or update tasks
    - [ ] Organise Nextcloud
    - [ ] Create tasks in Obsidian with dates
    - [ ] Update Habitnow
- [ ] Block out time for work during the week

## 4. Review this process
Is this process working, does anything need changing?

## Tasks from last week

```tasks
done
due after <%* tR += startOfWeek.format("YYYY-MM-DD") %>
due on or before <%* tR += endOfWeek.format("YYYY-MM-DD") %>
```
## Tasks this week
Put tasks here with dates for when they're due
