# The Unofficial Guide — Project 1

> **How to use this template:**
> Complete each section *after* you've built and tested the corresponding part of your system.
> Do not write placeholder text — if a section isn't done yet, leave it blank and come back.
> Every section below is required for submission. One-liners will not receive full credit.

---

## Domain

<!-- What topic or category of knowledge does your system cover?
     Why is this knowledge valuable, and why is it hard to find through official channels?
     Example: "Student reviews of CS professors at [university] — useful because official
     course descriptions don't reflect teaching style, exam difficulty, or workload." -->

Student experiences with off campus housing near UW
---

## Document Sources

<!-- List every source you collected documents from.
     Be specific: include URLs, subreddit names, forum thread titles, or file names.
     Aim for variety — sources that together cover different subtopics or perspectives. -->

| # | Source | Type | URL or file path |
|---|--------|------|-----------------|
| 1 | UW Website |wiki |https://www.ielp.uw.edu/life-at-the-uw/housing/off-campus-housing|
| 2 | UW Website |wiki |https://hfs.uw.edu/live/apply-for-housing-new-residents/|
| 3 | UW Website |wiki|https://hfs.uw.edu/live/apply-for-housing-current-residents/ |
| 4 | U district Universe |blog |https://uw.offcampus-universe.com/post/student-housing-in-seattle-the-complete-uw-off-campus-guide?utm_source=chatgpt.com |
| 5 | U district Universe|blog|https://uw.offcampus-universe.com/post/student-housing-university-of-washington-seattle-guide?utm_source=chatgpt.com |
| 6 | U district Universe|blog|https://uw.offcampus-universe.com/post/uw-student-housing-a-seattle-off-campus-living-guide?utm_source=chatgpt.com |
| 7 | Reddit| chat post |https://www.reddit.com/r/udub/comments/1l2whc9/uw_student_off_campus_apartments/?utm_source=chatgpt.com|
| 8 | Reddit|chat post |https://www.reddit.com/r/udub/comments/1nu78ga/uw_housing_megathread_fall_2025/ |
| 9 | Reddit| chat post |https://www.reddit.com/r/udub/comments/1e767r3/where_do_most_uw_students_live/ |
| 10 | Reddit| chat post |https://www.reddit.com/r/udub/comments/1r4yekm/getting_housing_with_financial_aid/ |

---

## Chunking Strategy

<!-- Describe your chunking approach with enough specificity that someone else could reproduce it.
     Include:
     - Chunk size (characters or tokens) and why that size fits your documents
     - Overlap size and why (or why not) you used overlap
     - Any preprocessing you did before chunking (e.g., stripping HTML, removing headers)
     - What your final chunk count was across all documents -->

**Chunk size: 200 words**

**Overlap: 30 words**

**Why these choices fit your documents: Most of webpage sections are shorter than 200 words and while the Reddit comments vary in length, most comments and topic are still within the 150  mark with key facts concentrated in the paragraph. A chunk size of 200 words will preserve complete comments and webpage sections while minimizing topic mixing. A 30 word overlap should maintain context across chunk boundaries for the longer Reddit discussions in the mega thread source**

**Final chunk count:**

---

## Embedding Model

<!-- Name the embedding model you used and explain your choice.
     Then answer: if you were deploying this system for real users and cost wasn't a constraint,
     what tradeoffs would you weigh in choosing a different model?
     Consider: context length limits, multilingual support, accuracy on domain-specific text,
     latency, and local vs. API-hosted. -->

**Model used:all-MiniLM-L6-v2**

**Production tradeoff reflection:I would compare some of the larger semantic models and evaluate how much they improve retrieval quality versus how much slower or more expensive they are. One model might have a higher context limit that would reduce the need for extremely precise chunking but it might be more expensive because it is API based that has more usage costs and slight latency due to external dependences**

---

## Grounded Generation

<!-- Explain how your system enforces grounding — how does it prevent the LLM from answering
     beyond the retrieved documents?
     Describe both your system prompt (what instruction you gave the model) and any structural
     choices (e.g., how you formatted the context, whether you filtered low-relevance chunks).
     Do not just say "I told it to use the documents" — show the actual instruction or explain
     the mechanism. -->

**System prompt grounding instruction:**

**How source attribution is surfaced in the response:**

---

## Evaluation Report

<!-- Run your 5 test questions from planning.md through your system and record the results.
     Be honest — a partially accurate or inaccurate result that you explain well is more
     valuable than a suspiciously perfect result. -->

| # | Question | Expected answer | System response (summarized) | Retrieval quality | Response accuracy |
|---|----------|-----------------|------------------------------|-------------------|-------------------|
| 1 | | | | | |
| 2 | | | | | |
| 3 | | | | | |
| 4 | | | | | |
| 5 | | | | | |

**Retrieval quality:** Relevant / Partially relevant / Off-target  
**Response accuracy:** Accurate / Partially accurate / Inaccurate

---

## Failure Case Analysis

<!-- Identify at least one question where retrieval or generation did not work as expected.
     Write a specific explanation of *why* it failed, tied to a part of the pipeline.

     "The answer was wrong" is not an explanation.

     "The relevant information was split across a chunk boundary, so retrieval returned
     only half the context — the model didn't have enough to answer correctly" is an explanation.

     "The embedding model treated the professor's nickname as out-of-vocabulary and returned
     results from an unrelated review" is an explanation. -->

**Question that failed:**

**What the system returned:**

**Root cause (tied to a specific pipeline stage):**

**What you would change to fix it:**

---

## Spec Reflection

<!-- Reflect on how planning.md shaped your implementation.
     Answer both questions with at least 2–3 sentences each. -->

**One way the spec helped you during implementation:**

**One way your implementation diverged from the spec, and why:**

---

## AI Usage

<!-- Describe at least 2 specific instances where you used an AI tool during this project.
     For each: what did you give the AI as input, what did it produce, and what did you
     change, override, or direct differently?

     "I used Claude to help me code" is not sufficient.
     "I gave Claude my Chunking Strategy section from planning.md and asked it to implement
     chunk_text(). It returned a function using a fixed character split. I overrode the
     chunk size from 500 to 200 because my documents are short reviews, not long guides." -->

**Instance 1**

- *What I gave the AI:*
- *What it produced:*
- *What I changed or overrode:*

**Instance 2**

- *What I gave the AI:*
- *What it produced:*
- *What I changed or overrode:*
