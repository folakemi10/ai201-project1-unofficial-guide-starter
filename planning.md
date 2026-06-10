# Project 1 Planning: The Unofficial Guide

> Write this document before you write any pipeline code.
> Your spec and architecture diagram are what you'll use to direct AI tools (Claude, Copilot, etc.) to generate your implementation — the more specific they are, the more useful the generated code will be.
> Update the Retrieval Approach and Chunking Strategy sections if you change your approach during implementation.
> Update this file before starting any stretch features.

---

## Domain

<!-- What domain did you choose? Why is this knowledge valuable and hard to find through official channels? -->
Student experiences with off campus housing near UW
---

## Documents

<!-- List your specific sources: URLs, subreddit names, forum threads, or file descriptions.
     Aim for at least 10 sources that together cover different subtopics or perspectives within your domain. -->

| # | Source | Description | URL or location |
|---|--------|-------------|-----------------|
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

<!-- How will you split documents into chunks?
     State your chunk size (in tokens or characters), overlap size, and explain why those
     numbers fit the structure of your documents.
     A review-heavy corpus warrants different chunking than a long FAQ. -->


**Chunk size: 200 words**

**Overlap: 30 words**

**Reasoning: Most of webpage sections are shorter than 200 words and while the Reddit comments vary in length, most comments and topic are still within the 150  mark with key facts concentrated in the paragraph. A chunk size of 200 words will preserve complete comments and webpage sections while minimizing topic mixing. A 30 word overlap should maintain context across chunk boundaries for the longer Reddit discussions in the mega thread source.**

---

## Retrieval Approach

<!-- Which embedding model are you using (e.g., all-MiniLM-L6-v2 via sentence-transformers)?
     How many chunks will you retrieve per query (top-k)?
     If you were deploying this for real users and cost wasn't a constraint, what tradeoffs
     would you weigh in choosing a different embedding model — context length, multilingual
     support, accuracy on domain-specific text, latency? -->

**Embedding model:ll-MiniLM-L6-v2**

**Top-k:3**

**Production tradeoff reflection:I would compare some of the larger semantic models and evaluate how much they improve retrieval quality versus how much slower or more expensive they are. One model might have a higher context limit that would reduce the need for extremely precise chunking but it might be more expensive because it is API based that has more usage costs and slight latency due to external dependences**

---

## Evaluation Plan

<!-- List your 5 test questions with their expected correct answers.
     Questions should be specific enough that you can judge whether the system's response
     is right or wrong. "What are good dining halls?" is too vague.
     "What do students say about wait times at [dining hall name] during lunch?" is testable. -->

| # | Question | Expected answer |
|---|----------|-----------------|
| 1 |What are the main neighborhoods where UW students live off-campus?|U District,Ravenna, Wallingford, Northgate, Bryant, and Capitol Hill|
| 2 |What is the deadline for current UW residents to apply for on-campus housing |Applications  open in early April and close April 12.
| 3 |What utilities are usually included in rent for off campus apartments near uw? |electricity, water, gas, internet, and trash |
| 4 |What is the typical rent range for a one-bedroom apartment near UW?|$1,600 to $2,200 |
| 5 |What is the application process for new UW residents seeking on-campus housing?|New residents must create an HFS account, complete the online housing application in the HFS portal, and submit it during the application period to be considered for assignment.|

---

## Anticipated Challenges

<!-- What could go wrong? Name at least two specific risks with reasoning.
     Consider: noisy or inconsistent documents, missing source attribution, off-topic
     retrieval, chunks that split key information across boundaries. -->

1. The Reddit housing megathread contains hundreds of comments discussing rent prices, roommates, and housing experiences. However, the information is repetitive, varies widely in reliability, and sometimes conflicts across users (same neighbourhood but different rices or experience)

2. Hallucination is always a risk if i ask a question not related to my limited sources because i only have 10 and some are similar, despite me trying to make sure they have some varaince

---

## Architecture

<!-- Draw a diagram of your pipeline showing the five stages:
     Document Ingestion → Chunking → Embedding + Vector Store → Retrieval → Generation
     Label each stage with the tool or library you're using.
     You can use ASCII art, a Mermaid diagram, or embed a sketch as an image.
     You'll use this diagram as context when prompting AI tools to implement each stage. -->

---

## AI Tool Plan

<!-- For each part of the pipeline below, describe:
     - Which AI tool you plan to use (Claude, Copilot, ChatGPT, etc.)
     - What you'll give it as input (which sections of this planning.md, which requirements)
     - What you expect it to produce
     - How you'll verify the output matches your spec

     "I'll use AI to help me code" is not a plan.
     "I'll give Claude my Chunking Strategy section and ask it to implement chunk_text()
     with my specified chunk size and overlap" is a plan. -->

**Milestone 3 — Ingestion and chunking:I'll give Claude my Chunking Strategy section and ask it to implement chunk_text() with my specified chunk size and overlap and I will manually inspect chunk outputs to ensure the chunks does not exceeds target size by much, and reddit comments are not merged in unnatural ways or I'll ask how to scrape the data on reddit to feed in a txt file for the mega thread**

**Milestone 4 — Embedding and retrieval:**

**Milestone 5 — Generation and interface:**
