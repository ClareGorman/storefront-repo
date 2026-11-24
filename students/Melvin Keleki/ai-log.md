# AI Log

## Prompts I sent

### Prompt 1 — Choosing the question and dataset

> I am using this data page link to find a data set that can help me answer a business question for my business: Minnesota Precision Feed Network. Link: https://quickstats.nass.usda.gov/. I would like to use the crop sector. Using page three of the executive summary, which business question could I answer with a crop based data set in this link? **Your goal:** Build one web page that helps your team's link in our Minnesota agriculture supply chain make a single decision using real public data. Do not create the link until I approve the data set chosen and question chosen from my specified sources.

### Prompt 2 — Approving the question and dataset

> yes

### Prompt 3 — Sharing the assignment rubric and asking for help

You are a supply chain and data analytics tutor for college students. I am a student in a digital supply chain class. This is my assignment meant for use of AI and github, including the rubric:

**Harvest to Screen: Build an Ag Data Web Page**

**Individual assignment** · Part 1 in class (about 25 minutes) · Part 2 as homework (about 60–90 minutes) · due date in Canvas

**Your goal:** Build one web page that helps your team's link in our Minnesota agriculture supply chain make a single decision using real public data. You will use an AI assistant (LLM) to write the code. Your job is to direct it, read what it built, and prove the data is real. You may talk with teammates, but each of you builds and submits your own page.

**What you will submit**

| Deliverable | Where | When |
| --- | --- | --- |
| Decision question, data source, first draft page | Committed to your folder in the team repo | End of class |
| Working page using stored data | Your folder in the team repo | Due date |
| AI log | Your folder in the team repo | Due date |
| Reflection + link to your folder | This Canvas assignment | Due date |

Put everything in `students/your-name/` in your team repo so your commits show your own work.

**Part 1: In class (about 25 minutes)**

**1. Write your decision question (3 minutes)**

One sentence about a decision your team's link in the chain actually faces. Example: *"Should our co-op hold or sell corn this month?"*

**2. Choose a data source (4 minutes)**

Start with one of these, or find a better public source that fits your question.

| Source | What it holds | How to get it |
| --- | --- | --- |
| [Open-Meteo](https://open-meteo.com/) | Historical and forecast weather for any latitude/longitude, back to 1940 | Free web API, no key needed |
| [USDA NASS Quick Stats](https://quickstats.nass.usda.gov/) (web tool) | Crop yields, acres planted, prices, and livestock by state and county | Point-and-click, then download as CSV |
| [USDA NASS Quick Stats API](https://quickstats.nass.usda.gov/api) | The same NASS data, pulled by code | Free API key required |

**3. Build a first draft with your LLM (12 minutes)**

Paste this starter prompt and fill in the brackets. Expect to refine it; the first answer is rarely the final one.

Build one self-contained HTML file that answers this question for a Minnesota agriculture supply chain: [your question]. Use this data source: [URL or file name]. The fields I need are: [fields]. Add a dropdown or slider to filter by [county / year / crop] and a chart that updates when I change it. Add comments that explain, in plain English, where the data comes from and where it is stored.

Save the result as a `.html` file and open it in your browser. Start your AI log now: copy each prompt you send and note anything the LLM got wrong.

**Check before you leave:**

- Does the page show *real* data? How do you know?
- If the numbers look smooth and round, ask the LLM directly whether it made up sample data.
- If something breaks, do not just ask the LLM to "fix it." First figure out *where your data actually lives*.

**4. Commit your draft (3 minutes)**

Commit your question, source, draft page, and AI log to `students/your-name/`, even if the page does not work yet. A broken draft is fine; an empty folder is not.

**Part 2: Homework (about 60–90 minutes)**

**5. Make it work from stored data**

Your final page must still work if the original source goes offline. Save a copy of the data you use (CSV or JSON) in your folder and have the page load from that copy. Keep the source URL and the date you downloaded it in a comment at the top of the file.

**6. Read the code**

Add your own comments (starting with `// ME:`) at three spots in the code:

1. Where the data comes **in**
2. Where the data is **kept** while the page runs
3. Where the data is **changed** (filtered, summed, charted)

Write them in your own words. You are explaining the instructions, not writing new code.

**7. Finish your AI log**

Save as `ai-log.md`. Include every prompt, at least one thing the LLM got wrong or made up, and how you checked it.

**8. Write your reflection (submit in Canvas)**

About 250 words, answering:

1. What broke or surprised you in class, and what was the real cause?
2. Where does your data live now, and who could change it without you knowing?
3. Your page is one signal in our supply chain. Who downstream would act on it, and what would they need to trust it?
4. Name one thing your team's storefront would need to store for its signal to be trusted next week.

Include the link to your `students/your-name/` folder.

**How it is graded (20 points)**

| Criterion | Full credit looks like | Points |
| --- | --- | --- |
| In-class draft | Question, source, and draft committed by end of class | 3 |
| Working page | Loads real stored data, filter and chart work, source and download date noted | 5 |
| Code reading | Three `// ME:` comments that correctly explain in, kept, and changed | 4 |
| AI log | All prompts, at least one LLM error caught, and how it was checked | 4 |
| Reflection | Answers all four questions with specifics from your own page | 4 |

How do I go about this? Please take me step by step.

### Prompt 4 — Asking for one step at a time

> wait im confused, explain to me step by step

### Prompt 5 — Asking for help with GitHub

> here is github, help me out (i've never used it before) https://github.com/ClareGorman/storefront-repo

### Prompt 6 — Confirming my first commit

> Done! I committed it.

### Prompt 7 — Showing my GitHub screen

> This is what im seeing right now

I attached a screenshot showing `README.md` in `students/Melvin Keleki/`.

### Prompt 8 — Confirming I added the draft page

> ok done

### Prompt 9 — Asking which prompts to log

> what are the prompts i used

### Prompt 10 — Asking for the same log format

> put it in the same format as the edit we have started making in the ai-log.md

### Later prompts and progress updates

> alright I am a little confused. Here is what I have so far

[Attached a screenshot of the GitHub editor.]

> this is what I have:

[Attached the draft AI log.]

> rwait why

> i think its ok right?

> omg it didnt save. i only have two files again

> what should i paste

> this doesnt show tho code tho

> this is what i have, looks like im missing something?

[Pasted my AI log draft.]

> im confised

> ok i did that

> now what

> this code doesnt work

> help me understand thi

[Selected the earlier AI log instructions.]

> this is what my github looks like now

[Pasted the Markdown shown in GitHub.]

> this is where im at

[Attached a file named `index.html` containing Markdown.]

> this is my ai-log.md

[Attached my AI log.]

> ok i want to make this a final submission

> i need the code version right?

> I dont have the raw markedown

## What I found in the draft

The AI put the county averages directly into the first version of `index.html`. The draft also had no dropdown or chart. The assignment asks for the chart to update when the selected year changes and for the final page to load its numbers from a separate data file.

To verify where the draft's numbers were stored, open the first version of `index.html` in the GitHub commit history and look for Mower County's `39,484,500` bushels inside an `<li>` tag.
