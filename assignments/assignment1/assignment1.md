# [Assignment 1: Problem Framing](https://61040-fa25.github.io/assignments/assignment-1)

_Due Sep 7, 2025 11:59 PM_

### Table of Contents:

- [Domains](#domains)
- [Problems](#problems)
- [Stakeholders](#stakeholders)
- [Evidence](#evidence)
- [Features](#features)

---

## Domains

### List of 10 domains:

1. **Waking up on time for the massive heavy, over-sleeper**
2. **Prepping for software engineering interviews**
3. **Remembering to water plants**
4. **Reducing doomscrolling**
5. **Managing move-in/move-out logistics**
6. **Connecting with other interns in a new city**
7. **Coordinating regular meetups with friends**
8. **Remembering to vote absentee**
9. **Consolidating class deadlines**
10. **Auto-summarizing LLM use for citations**

### Selected Domains:

**1. Consolidating class deadlines**

- Academic life at MIT involves managing multiple courses that each operate on their own systems (e.g., Canvas, standalone websites like 6.1040’s, Piazza, static PDFs, etc). Deadlines are often buried in syllabi, one-off announcements, or recitation slides, and they’re rarely presented in a consistent or centralized way. As a result, it becomes the student’s responsibility to hunt down and manually track every assignment and exam date. This creates a constant low-level anxiety that something might have been missed. I and many of my friends start each semester by trying to manually build our own calendar systems, collecting these dates on Notion or Google Calendar, but that process itself is time-consuming and prone to error. The fragmentation of information across platforms adds unnecessary friction to staying on top of work and makes it easy for things to slip through the cracks -- something I and many others have experienced firsthand.

**2. Coordinating regular meetups with friends**

- Everyone says “we should grab a meal sometime", but it's often hard to find a good time and even when a good time is found not everyone follows through. Usually it's a back and forward of asking when someone else is available and sharing when you are available within an X period, and if not a compatible time is found you continue with the next X period and so on, until you find a time or give up altogether and say 'let's meet up next semester actually!'. This is particularly bad during busy periods of the semester such as midterms/finals season. Picking a place and what to do is another whole piece to this coordination and usually many parties are indecisive/indifferent making it even harder. Coordination also sometimes always falls on one person, making that person the designated planner who sometimes feels like their whole friend groups depends on them for meeting up otherwise they never meet.

**3. Prepping for software engineering interviews**

- Applying for software engineering internships and new grad roles can be stressful, especially when juggling classes, projects, and other responsibilities. I’ve often felt like I’m just trying to keep up, bouncing between spreadsheets, application portals, and prep resources without a clear system. When things work out, it sometimes feels more like luck than strategic planning. I want to be more intentional and organized in how I approach the process, particularly during the fast-paced summer and fall recruiting season. With AI rapidly changing the tech job market landscape, staying prepared and adaptable is more important than ever. I also find that the process can feel opaque intimidating-to-start especially for college students and early-career applicants who do not have alot of insider knowledge about the tech industry. This is especially something that I experienced last recruiting season as someone who is the first in their family to attend college, parents are from a working-class background, and was generally unfamiliar with how getting a job in the tech industry works.

---


## Problems

### 3 Problems per Selected Domain:

### Domain 1: Consolidating Class Deadlines

#### a) **[Selected] Deadline information is fragmented across platforms**

- **Description**  
  Course deadlines are often distributed across Canvas, course-specific websites (e.g. 6.1040), PDFs, Piazza posts, lecture slides, and/or emails. Students are expected to manually check each platform regularly, which is cognitively exhausting and increases the chance of overlooking something.

- **Reason for selection**  
  This is the root cause of the other two problems and the most fundamental source of friction. Every student at MIT encounters this fragmentation, and it affects their ability to plan, prioritize, and stay on top of coursework. While the other two problems are real, they stem directly from this one: students build custom trackers because the information is scattered, and deadline shifts are hard to catch because there’s no centralized source of truth. It also allows for a project that explores interesting technical design questions, such as how to surface or sync data from multiple inconsistent sources.

---

#### b) **[Not selected] Students waste time manually compiling deadlines**

- **Description**  
  Many students spend the first week or two of the semester building custom trackers, such as in Notion, Google Calendar, or even Google spreadsheets, to consolidate due dates. This repetitive process is error-prone and time-consuming, and it places an unnecessary burden on students just to function academically effectively.

- **Reason for non‑selection**  
  While this is frustrating, it’s ultimately a workaround for the deeper issue of fragmented sources. Building a better manual tracker might be helpful, but it wouldn’t solve the root problem. Additionally, this space is already saturated with generic tools like Notion and Google Calendar templates.

---

#### c) **[Not selected] Deadline changes are inconsistently communicated**

- **Description**  
  When assignments shift, announcements may be made in passing during lecture, quietly updated in a shared doc, or posted to a piazza. Without a reliable way to detect or surface these changes immediately, students may unknowingly rely on outdated information.

- **Reason for non‑selection**  
  This is a difficult problem to address cleanly without deep integration into instructor workflows and platform APIs (unlike Problem a which requires only a one-time sync, this requires routine syncs) and may also require non-software interventions, such as changes to teaching practices or communication norms. While important, it is harder to scope and build a compelling solution around it within a single semester. Furthermore, this could be a stretch goal/extension for a solution to Problem a.

---

### Domain 2: Coordinating Regular Meetups with Friends

#### a) **[Selected] Finding mutually free times across different schedules**

- **Description**  
  Everyone’s calendar fills up quickly with classes, club meetings, work, and spontaneous commitments. Even if people want to hang out regularly, it’s difficult to find recurring time slots that work for everyone, especially in a group.

- **Reason for selection**  
  This is the core logistical barrier to regular social connection. Even when the motivation and intention are there, coordination fails because schedules are complex and change weekly. The mental load of figuring out “what works for everyone” often prevents plans from happening at all. Solving this could benefit not only friend groups but also study groups, project teams, and roommates.

  From a design perspective, this is can be an enjoyable problem with interesting challenges in calendar syncing, time conflict resolution, and social UX. It also has clear boundaries, making it easier to scope than interpersonal or behavioral problems.

---

#### b) **[Not selected] Social plans fall through due to lack of follow‑up**

- **Description**  
  Even after suggesting “we should get lunch sometime,” no one takes initiative to follow up, or people forget to respond. Without a system for nudging or confirming, the plans quietly die not out of disinterest, but out of friction and forgetfulness.

- **Reason for non‑selection**  
  This is an important issue, but it’s often a symptom of scheduling friction or low urgency. While nudging systems could help, it’s harder to separate true forgetfulness from quiet opt-outs. Solutions here risk feeling spammy or intrusive unless done very thoughtfully.

---

#### c) **[Not selected] Responsibility for planning always falls on the same person**

- **Description**  
  In many friend groups, one person becomes the default planner who proposes times, checks everyone's availability, and finds/books spots. This role can become tiring and makes coordination feel like work, especially when others don’t contribute equally.

- **Reason for non‑selection**  
  This speaks to group dynamics and social roles, which are difficult to standardize or automate. While tools can try to rotate responsibility or share it equally, enforcing fairness in casual relationships is tricky and may not be well received-- prone to antibodies. It’s a meaningful issue, but more complex to address in a lightweight, student-friendly tool. In other words, it falls victim to the idea of what software can and cannot solve/do (i.e., fundamentally change human behavior as we discussed with the rotating who takes out the trash app idea in class).

---

### Domain 3: Prepping for Software Engineering Interviews

#### a) **[Not selected] Finding a consistent mock interview partner**

- **Description**  
  Mock interviews are one of the most effective ways to improve, but many students struggle to find someone who’s available, similarly motivated, and at a compatible experience level. Even when a partner is found, staying consistent can be difficult due to mismatched schedules or awkwardness around feedback.

- **Reason for non‑selection**  
  Building a tool to match people is feasible, but sustaining engagement and ensuring quality practice would require moderation, trust-building, gaining a critical mass to use the app, or social incentives -- all of which are harder to implement within a semester project.

---

#### b) **[Not selected] Keeping track of company‑specific timelines/formats**

- **Description**  
  Each company has a different process: some include online assessments, others start with behavioral calls with recruiters, and some skip straight to technical interviews. Materials and formats vary widely, and timelines shift quickly. Interview formats and expectations also evolute over time as the tech industry landscape evolutes and business needs change. Students often rely on online forums like Reddit or word-of-mouth to understand how different companies operate. It's hard to see where you are in the middle of interview as some companies are not very transparent about the entire interview process.

- **Reason for non‑selection**  
  While the problem is real and frustrating, solving it at scale would likely require collecting and maintaining large volumes of company-specific information -- either through web scraping, crowd-sourcing, or community-driven submissions. This introduces logistical and legal challenges, similar to platforms like Levels.fyi or Blind, which only work because of massive user bases. Without critical mass, any tool would risk becoming incomplete or quickly outdated. This makes the problem difficult to tackle meaningfully within a single semester.

---

#### c) **[Selected] LeetCode practice can be miserable**

- **Description**  
  Many companies use LeetCode-style algorithmic questions as part of their application process. For candidates like myself, practicing LeetCode is often treated as a necessary evil-- repetitive, stressful, and often disconnected from real-world coding. I personally struggle to build consistent habits, falling into cycles of burnout, procrastination, and/or cramming right before interviews-- sometimes pushing off interviews or cancelling them if I don't feel prepared. The practice can feel isolating and demoralizing, especially without clear progress or peer support. I've personally found LeetCode to be something to be more hushed/taboo to talk about in industry and among peers despite the necessary of it to do well in interviews for us non-coding wizards.

- **Reason for selection**  
  This problem is deeply relatable, highly widespread, and yet surprisingly under-discussed. It affects both the emotional and practical sides of interview prep and contributes to avoidable stress and self-doubt. There’s room for creative, lightweight interventions -- like gamification, social motivation, or habit-forming nudges -- that could significantly improve the experience without needing large-scale infrastructure or external data. It’s also a project that could be personally meaningful and fun to prototype, with lots of room for iteration and experimentation.

---

## Stakeholders

### 3 Stakeholders per Selected Problem:

**1. Problem: Deadline information is fragmented across platforms**

**Stakeholders:**  
- **Student Planner** (student responsible for tracking and acting on deadlines)  
- **Instructor or TA** (posts and updates assignments across channels)  
- **Learning Platform Owner** (Canvas/department IT that hosts, integrates, or gates data)

**Impacts:**  
Student Planner bears cognitive load, higher error risk, and last‑minute scramble when updates are missed. Instructors and TAs field repeated clarification requests, spend time duplicating posts, and see uneven participation when information fails to reach all students. Learning Platform Owner faces blame for “poor UX” and support tickets; they may also have weak incentives to open APIs or unify feeds if fragmentation increases platform stickiness.

**2. Problem: Finding mutually free times across different schedules**

**Stakeholders:**  
- **Initiator** (person who tries to organize recurring meetups)  
- **Casual Participant** (friend who attends but does not actively plan)  
- **Calendar Provider** (Google/Apple/Microsoft whose data and permissions drive availability)

**Impacts:**  
Initiator pays a coordination tax: polling, reconciling constraints, nudging, and rescheduling when classes and clubs shift week to week. Casual Participant experiences friction and decision fatigue; overly pushy workflows can feel spammy or exclusionary if preferences like quiet hours or commute windows are ignored. Calendar Provider controls availability semantics, free/busy sharing, and consent; they may prefer ecosystem lock‑in and could resist deep cross‑platform interoperability. 

**3. Problem: LeetCode practice can be miserable**

**Stakeholders:**

- **Candidate** (student preparing for algorithmic interviews)  
- **Recruiter or Hiring Manager** (relies on prep translating to consistent interview signal)  
- **Practice Platform Provider** (LeetCode/HackerRank whose engagement model shapes behavior)

**Impacts:**  
Candidates face burnout cycles, procrastination, and confidence dips that reduce actual learning and lead to avoidable no‑shows or reschedules. Recruiters and hiring managers suffer signal noise: cram‑driven performance swings, false negatives on capable candidates, and elongated pipelines. Practice Platform Providers may optimize for streaks and daily engagement rather than deep mastery, creating incentives that can worsen grind without improving transfer to interviews. 


---

## Evidence

### 1. Problem: **Deadline Information is Fragmented Across Platforms**

1. **[MIT Students Rants over inconvience of centralized calendar for assignments on MIT Confessions](https://www.facebook.com/share/p/1Attashr4Q/)**  
  This MIT Confession expresses frustration over the lack of a centralized calendar for assignments and exams, echoing a widespread desire for streamlined, unified deadline tracking, supporting the need for tools that automatically consolidate academic dates across platforms.

2. **[Reddit Example: Missed Final Due to Comment Submission](https://www.reddit.com/r/Professors/comments/1kozll5/wwyd_student_submitted_final_via_comments_on/)**  
   A student missed a major assignment due to confusion over submission channels, highlighting communication breakdown.

3. **[Deadlines Improve Student Success](https://blogs.bsu.edu/teaching-innovation/2024/11/13/new-in-canvas-multiple-due-date-discussions-checkpoints/)**  
   Research and instructional design experts emphasize that clearly structured deadlines, milestone check-ins, and consistent visibility into upcoming work help students stay on track and reduce last-minute cramming. When deadlines are clearly communicated and easily accessible, students are more likely to engage consistently, submit assignments on time, and perform better overall. This underscores the importance of tools that surface deadlines early and reliably, especially when course platforms are fragmented.

4. **[Google Classroom](https://edu.google.com/intl/ALL_us/workspace-for-education/products/classroom/)**  
   Google Classroom automatically compiles assignments, announcements, and due dates in a unified stream and calendar view, helping students stay organized and reducing missed work. Its adoption in K–12 and some university settings demonstrates how centralizing academic information can improve student awareness and accountability. The strong demand for similar functionality in systems like Canvas or Piazza highlights the need for deadline consolidation tools in more complex academic environments like MIT.

5. **[MIT Student mentions how use their Notion as a Master Calendar for all their academic dates](https://mitadmissions.org/blogs/entry/look-at-my-notion-%F0%9F%8C%B1/)**
   This DIY behavior underscores that the need is real but the burden is placed on students to patch together incomplete systems rather than rely on institutional infrastructure.

6. **[Canvas ICal](https://www.reddit.com/r/cuboulder/comments/j1i7oq/how_to_sync_canvas_calendar_to_your_ios_or/)**
   While Canvas technically offers an iCal feed, instructors often don’t enter deadlines properly or use Canvas inconsistently. This results in calendar feeds that are incomplete or unreliable, defeating the purpose of having a centralized calendar. Students are forced to cross-check against announcements, syllabi, and emails.

7. **[CAT-SOOP](https://catsoop.org/), [6.1040 Course Website](https://61040-fa25.github.io/)**
   Even though Canvas exists, many MIT courses continue to use standalone websites like using CAT-SOOP or their own github-based websites to publish schedules and deadlines. These formats are not machine-readable or easily synced to calendars, making it difficult for students to track updates unless they manually check multiple locations.8. 

8. **[Piazza Notifications](https://support.piazza.com/support/solutions/articles/48000574383-student-email-notification-settings)**
    While Piazza has notifications for summaries of new posts, MIT students receive many emails in their inboxes so important announcements can get lost and not ever read. Also, sometimes, students disable notification if a Piazza forum is very active and prone to sending them many notifications.

9. **[Notion Templates for Students](https://www.notion.com/templates/category/school?srsltid=AfmBOooH8SN8DOJTtuzQjuVbJEbuTgsUkGBMATHN5gwKmL5QKwAGV_MP)**
    Many students use Notion to manually build class dashboards or academic planners, complete with custom calendars, to-do lists, and assignment trackers. While flexible and powerful, this requires significant setup, maintenance, and manual data entry, shifting the responsibility of organization entirely to the student rather than the institution or course platform

10. **[MIT Hacker Tools like Firehose and CourseRoad try to Solve Semester/Registration Schedulability but not mid-semester scheduling](https://firehose.guide/)**
    MIT students have built tools like Firehose and CourseRoad to help pick classes and visualize prerequisites, but there’s still no centralized, trusted platform to track actual assignments or exams across classes when in the class.


### 2. Problem: **Finding Mutually Free Times Across Different Schedules**

1. **[Scheduling Gets Harder with Group Size](https://scitechdaily.com/a-mathematical-nightmare-new-research-explains-why-scheduling-meetings-is-so-hard/)**  
   Mathematically, scheduling availability becomes significantly harder as group size increases.

2. **[Making plans with other people and accomodating their schedules is difficult adulting but is what keep friendship alive throughout adulthood](https://www.buzzfeed.com/terripous/12-rules-for-making-plans-with-friends-like-a-grown-ass-adul)**  
   This reflection highlights how social anxiety and fear of rejection often prevent people from initiating plans-- even when they want to connect--underscoring the need for tools that lower the emotional friction of suggesting meetups and make it easier to take the first step.

3. **[User gets 'organiser' fatigue in friendship groups](https://www.reddit.com/r/AskWomenOver30/comments/15w8qvo/do_you_ever_get_organiser_fatigue_in_friendship/)**  
   Many adults experience "organizer fatigue" (i.e., the emotional burden of always initiating and planning social activities) often feeling unappreciated or anxious about whether friendships would persist without their effort. This highlights a need for lightweight, shared coordination tools that reduce friction and distribute planning responsibility more equitably.

4. **[Scheduling Fatigue in Academic Settings](https://www.raulpacheco.org/2022/09/on-calendars-synchronization-and-collaborative-work-in-academia-aligning-priorities-and-availabilities-across-multiple-people/)**  
   Academics report exhaustion from constantly trying to align schedules across people and platforms.

5. **[47% of Meetings are Rescheduled or Cancelled](https://reclaim.ai/blog/smart-meetings-report)**  
   Meeting failure is common--even with scheduling tools--illustrating persistent coordination issues.

6. **[Manual coordination is still the norm on r/GradSchool](https://www.reddit.com/r/GradSchool/comments/499347/anyone_else_have_difficulties_scheduling_in/)**  
   A user shares the common student experience: "Does anyone else have difficulties with scheduling in grad school?"--highlighting how manual, awkward coordination often persists, even among highly motivated groups.

7. **[MIT Confession about rare follow-up to catch a meal](https://www.facebook.com/share/p/1BmWnsERXC/)**  
   This confession reflects how common it is for social plans to be casually suggested but rarely followed through-- highlighting the need for tools that make informal meetups easier to confirm and act on, turning passive intentions into actual connections.

8. **[Doodle](https://doodle.com/en/)**  
   Popular for polling availability across large groups or scheduling meetings. Doodle is more suited to professional or structured contexts; ad-heavy for free users; requires email or account to respond; lacks real-time syncing or lightweight feel for informal plans.

9. **[When2Meet](https://www.when2meet.com/)**  
    An existing comparable app that helps coordinate availability. However, it requires users to manually input all their available times and depends on someone creating and sharing the link. Its interface feels more formal, which can be awkward or excessive for casual meetups with just 2–3 people. 

10. **[Polling Tools Like Doodle Have Limitations](https://link.springer.com/article/10.1140/epjb/s10051-024-00742-z)**  
   When2Meet and Doodle require effort from every participant, often failing due to non-response or edge-case schedules.

### 3. Problem: **LeetCode practice can be miserable**

1. **[Making LeetCode a Habit Using Psychology](https://medium.com/@_j_/how-to-make-leetcode-a-habit-1988176bb7f8)**  
   The article explains how to apply habit-forming psychology (trigger → action → reward) to consistent practice on LeetCode.

2. **[How One Year of Practice Helped a Developer Beyond the Interview](https://evilmartians.com/chronicles/how-a-year-long-leetcode-habit-upped-my-professional-game)**  
   Case study showing long-term, steady practice (not grinding) improved not just interview outcomes but also helped with real-world engineering (e.g., thinking about different test cases, problem constraints, optimizing solutions, etc.)

3. **[Burnout From the LeetCode Hustle](https://chetan-garg36.medium.com/the-leetcode-hustle-was-burning-me-out-until-i-discovered-this-e46933221d2d)**  
   Honest reflection on how intensive prep led to mental fatigue and lower motivation.

4. **[LeetCode Users Struggling Before Interviews](https://leetcode.com/discuss/career/371602/feeling-burnt-outclose-to-interviews)**  
   Users share emotional strain and lack of confidence nearing technical interviews.

5. **[Steady Prep > Intense Bursts](https://dev.to/dfs_with_memo/leetcode-survival-guide-1cp3)**  
   Survival guide recommending low-stakes, recurring practice rather than high-pressure marathons.

6. **[LeetCode Has Over 26 Million Monthly Users](https://en.wikipedia.org/wiki/LeetCode)**  
   Establishes that LeetCode is a ubiquitous tool-- so there is an authentic demand/existing community that already uses LeetCode and could potentially benefit from an extension of the tool.

7. **[NeetCode](https://neetcode.io/)**  
   A comparable existing web app that roadmaps most important problems to solve in order to be interview-ready. While this tool makes it slightly easier to get started, it misses features that keeps users consistently engaged.

8. **[Deprecation of Codesignal Arcade](https://www.reddit.com/r/learnprogramming/comments/1h0mnlp/replacement_for_codesignal_arcade/)**
    A comparable previously existing web app that gamified algorithmic coding practice is missed by its users after platform removes it. This demonstrates authentic demand for a gamified product. 

9. **[User asking how others stay motivated to keep doing LeetCode](https://www.reddit.com/r/leetcode/comments/ujbhab/lc_grind_motivation/)** 
    The top response mentions the need to gamify it and make it enjoyable but doesn't specify exactly how they do it, demonstrating that generally mindframe shift is already helpful to some people while other might need a tangible tool to help them realize it too.

10. **[An increasing shift away from LeetCode-based interview processes and more focus on how Candidates leverage AI tools](https://www.reddit.com/r/leetcode/comments/1mce28b/breaking_interviews_at_faang_will_no_longer_focus/)**
    Big Tech companies like Meta and Amazon have begun talking about shifting away from LeetCode questions. However, for the forseeable future, most companies still rely on these algorithmic questions to get a signal on the Candidates' abilites, and AI-based coding interviews are still in their experimental/exploratory phases. 

---
## Features

### 3 Features per Selected Problem:

### Problem 1: **Deadline Information is Fragmented Across Platforms**

**a. Auto-Sync Enrollment Integration**  
Automatically detects which classes a student is enrolled in via MIT authentication and scrapes or queries known associated sources-- including Canvas calendar feeds, Piazza announcements, public class websites, and even static PDFs -- to extract relevant deadlines and outputs some structured/standardized format such as a unified timeline dashboard or file that can be easily imported to applications like Notion or Google Calendar or used within the app itself. 

**Why it helps:** Reduces the burden on ***Student Planners*** to manually gather deadlines from fragmented sources. It leverages already accessible institutional systems and publicly posted materials, without requiring major behavior changes from instructors. Students get a unified, up-to-date view of assignments with minimal setup.

**b. Deadline Status Tracker (with Progress States)**  
Each extracted deadline has an associated status label(e.g., "Not Started", "In Progress", "Submitted", "Completed", or custom ) that students can update manually or via integration (e.g., Canvas submission API). Deadlines update visually in the dashboard to reflect progress.

**Why it helps:** Gives ***Student Planners*** a lightweight sense of control and planning clarity, turning passive deadlines into active workflows. It reinforces time management and keeps everything in one place, reducing the need for external tools like Notion or todo lists.

**c. Community-Sourced Deadline Pools**  
When a **Student Planner** extracts or confirms deadlines for a course, those verified entries are optionally shared to a class-wide “deadline pool.” New students enrolled in the same course (verified via MIT login) can import those deadlines instead of redoing the work. Contributions are timestamped and ranked by confidence and agreement.  

**Why it helps:** Reduces duplicated effort across students in the same class and helps late-joiners or those who missed early deadlines catch up. Builds a lightweight knowledge-sharing layer without needing instructors to change workflows, and gives students visibility into what’s already known or trusted for a given class.

---

### Problem 2: **Finding Mutually Free Times Across Different Schedules**

**a. Mini-Scheduler Bot**  
In a group chat (Slack, Messenger, iMessage), a lightweight bot can jump in and say “Looks like 3 of you are free Thursday evening. Want me to book that on everyone's Google Calendar?”  Group members can repond to it with an emoji/quick response and the bot will actually book it on their Google Calendar.


**Why it helps:** Automates the tedious step of actually scheduling, helping **Initiators** close the loop without sending reminders, while respecting opt-in consent from **Casual Participants**.

**b. Real-Time “Soft Hold” Coordination Layer**  
Lets participants temporarily reserve a suggested time slot on their own calendar as a tentative hold, reducing last-minute conflicts.  
**Why it helps:** Helps both **Initiators** and **Casual Participants** align availability without overcommitting, and works well even without tight integration from **Calendar Providers**.

**c. Privacy-Preserving Free/Busy Sync**  
Participants can privately link their calendar and only expose obfuscated availability windows (e.g., "busy 2–4pm"), with no event details shown.  

**Why it helps:** Balances ease of scheduling for the **Initiator** with calendar privacy needs for **Casual Participants**, encouraging broader adoption.

---

### Problem 3: **LeetCode Practice Can Be Miserable**

**a. Daily Mini-Challenges with Streak Tracking and Light Gamification** : A system that surfaces short, low-pressure coding challenges tailored by topic (e.g., “binary search warm-up” or “graph traversal refresher”) and tracks progress through streaks, XP points, or badges. Users can optionally compete in casual weekly ladders or challenge friends.

**Why it helps:** Makes practice feel less intimidating and more game-like, helping ***Candidates*** build habits through positive reinforcement rather than guilt. The gamification adds novelty and motivation, particularly for users who struggle to stay engaged through repetition alone.

**b. Reflective Logging After Each Session**  
After each session, candidates are prompted to briefly tag what went well, what was hard, and how they felt. These logs are visualized weekly.  

**Why it helps:** Helps **Candidates** regulate motivation, recognize progress, and break the cycle of mindless grinding. Useful data source for the **Practice Platform Provider** to understand user engagement beyond raw streaks.

**c. Streak Freeze & Guilt-Free Pause Mode**  
Allows users to intentionally pause their streak during finals, interviews, or low-motivation periods without punishment, and restarts with a gentle re-onboarding.  

**Why it helps:** Encourages sustainable prep habits for **Candidates** and reduces churn risk for **Platform Providers** by acknowledging the emotional rhythms of job hunting.
