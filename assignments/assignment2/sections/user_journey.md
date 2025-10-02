# User Journey

### ⓉⒾⓜ's 🦫 User Journey

**Title: Tim is aiming for a 5.0 this semester, but if only he could remember all his deadlines**

Tim is a junior at MIT trying to hold it all together. He’s balancing a full load of Course 6 classes, nonstop internship applications, and his beloved extracurricular: MIT’s Concrete Canoeing Team, where he’s somehow in charge of “structural integrity.”

Despite his ambition, Tim is forgetful by nature. His Canvas dashboard is a mess, Notion tables half-filled, and deadlines scattered across PDFs, GitHub Pages, and recitation slides. He’s already missed a warmup window in 6.1220 after mistaking “Wednesday at 10PM” for “next next week, probably?”

But then he discovers **DueStack**: the one calendar to rule them all.

---

**Step 1: Canvas Sync + Confirmation**  
Tim logs in and connects his Canvas account. DueStack fetches assignments from 6.1220 and 6.3700 and parses them into confirmable suggestions. He reviews, tweaks a title, and confirms the deadlines he wants and the confirmed items become official entries on his calendar, tagged as “CANVAS” (See thumbnails 1, 2, 3, 4, 5 in [UI_sketches](../sections/ui_sketches.md))

`sync when Users.connectCanvas --> ParsedDeadlineSuggestions.parseFromCanvas`  
`sync when ParsedDeadlineSuggestions.confirm --> Deadlines.create`

---

**Step 2: Uploading Syllabi or Screenshots**  
Next, Tim tackles 6.1040 and 6.3700’s chaos: one uses a GitHub schedule table, the other splits dates across two PDFs. He uploads both PDFs and a screenshot of the GitHub page to DueStack (See thumbnails 6 in [UI_sketches](../sections/ui_sketches.md)).

`sync when UploadedDocuments.upload --> ParsedDeadlineSuggestions.parseFromDocument`

---

**Step 3: Confirming Suggestions**  
DueStack displays extracted deadlines like “Quiz 2 - Nov 3, 7PM.” Tim reviews, tweaks a misparsed title, and confirms. The confirmed items are now real calendar events he can see on his dashboard  (See thumbnails 7 in [UI_sketches](../sections/ui_sketches.md)).

`sync when ParsedDeadlineSuggestions.confirm --> Deadlines.create`

---

**Step 4: Adding a Manual Deadline**  
Tim recalls that 6.1040 announced a design critique in lecture (but didn’t post it anywhere). He quickly adds it by hand.

`sync when Request.createDeadline --> Deadlines.create with source = MANUAL`

---

**Step 5: Staying on Track**  
As work piles up, Tim keeps DueStack open. He marks some deadlines “In Progress,” others “Done,” and exports everything to his Apple Calendar to keep handy on the go  (See thumbnail 8 in [UI_sketches](../sections/ui_sketches.md)).

`sync when Request.setStatus --> Deadlines.setStatus`

---

**Outcome**  
In 15 minutes, Tim transforms deadline chaos into a dam that actually holds. He might still think his next quiz is “probably next next Thursday,” but DueStack sets him straight before it costs him the 5.0.