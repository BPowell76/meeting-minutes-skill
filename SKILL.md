---
name: meeting-minutes
description: Create standardized meeting minutes and summaries in PDF and Markdown formats given a supplied transcript in a common text-based format: plain-text (.txt), Markdown (.md), PDF (.pdf), Word documents (.doc/.docx), or .vtt. This information is based on the information provided by Boardbook in their Minutes 101 article.
---

Create standardized meeting minutes to increase the quality of meeting summaries and post-meeting tasks.
The reports are output in both PDF and Markdown formats using a default page size of Letter with fixed 1" margins and default font selection of 10 pt DejaVu Serif.

## Document Mode

This skill supports 2 types of documents: 1) `summary`, and 2) `minutes` (the implied default)

| Mode                  | Verbosity                 | User Confirmations        | Sections Included                                                             |
| :---:                 | :---                      | :---                      | :---                                                                          |
| `minutes` (default)   | Per Verbosity Settings    | All items 1 - 6           | All 8 sections (see Document Layout)                                          |
| `summary`             | Forced `terse`            | Items 4 - 6 only          | Title Page, Key Points, Decisions, Action Items, Follow-Up & Next Meeting     |

In `summary` mode, the title page does not require its own page, overriding the page-break rule in Document Layout and the length-based condition in Document Design.
In `summary` mode, set the maximum document length as 1 page per 30-minutes.
If the meeting length is not known, use timestamps in `.vtt` transcripts to estimate the length of the meeting.
Otherwise or if the timestamps are missing, limit the document to 3 pages.

## Verbosity Settings

There are 3 switches to control how lengthy (i.e., how verbose) the document will be:

| Switch                | Content Type      | Sample                                                                | Example Output                                                        |
| :---:                 | :---              | :---                                                                  | :---                                                                  |
| `terse` (default)     | Sentence          | The problem with Q1's forecast is that it excludes key information.   | Q1's forecast excludes key information.                               |
| `terse`               | Bullet/Fragment   | Concerns re: Q1 forecast metrics — data gaps                   | Q1 forecast — missing data                                   |
| `standard`            | Sentence          | The problem with Q1's forecast is that it excludes key information.   | The problem with Q1's forecast is that it excludes key information.   |
| `standard`            | Bullet/Fragment   | Concerns re: Q1 forecast metrics — data gaps                   | Concerns re: Q1 forecast metrics — data gaps                   |
| `verbose`             | Sentence          | The problem with Q1's forecast is that it excludes key information.   | The fundamental issue with the Q1 forecast lies in its failure to incorporate several critical pieces of information that are essential for an accurate and comprehensive projection. |
| `verbose`             | Bullet/Fragment   | Concerns re: Q1 forecast metrics — data gaps                   | Concerns were raised regarding gaps in the Q1 forecast's underlying data    |

All three switches capture identical information. Terse/standard/verbose only control sentence length and phrasing.

If the user doesn't mention they want the report to be either `standard` or `verbose`, then use the `terse` verbosity switch.

Note: verbose may render fragments as complete sentences; terse and standard should preserve fragment structure where the source content is a fragment.

## Transcript Process Routing

For the following document types, use the following additional skills to process transcripts:

| Document Type                 | Additional Skills                                             |
| :---:                         | :---:                                                         |
| `.pdf`                        | `pdf-reading`                                                 |
| `.doc`/`.docx`                | `docx`                                                        |
| `.vtt`                        | Read as plain-text and strip timestamps and cues              |
| `.txt`/`.md`                  | Read directly; no additional skills needed                    |
| Unrecognizable/unparseable    | Notify the user and request a plain-text or Markdown version  |

## User Confirmations

Ask the user to confirm the following before processing the transcript and constructing the document:

1. Is a Supporting Data section needed?
2. Is a Motions and Resolutions section needed?
3. Is a Follow-Up & Next Meeting section needed?
4. Choose a page size from the following options: Letter, A4, Legal, or Tabloid/Ledger
5. Choose a font-face from the following options: DejaVu Serif, Liberation Serif, or Noto Serif
6. Choose a font size from the following options: 10 pt, 12 pt, 16 pt, or Other (User-specified)

For page size, font face, and font size, present the stated defaults (Letter, DejaVu Serif, 10pt) as the pre-selected options during confirmation.
The user may accept or override them.

If the user answers "No" to any of the section questions, do not include them in the final report.
For the font size options, only accept values between 10 pt and 20 pt.

## Document Layout

The meeting minutes needs to include the following sections:

1. Title page
2. Key Points
3. Supporting Data
4. Questions and Concerns
5. Action Items
6. Motions and Resolutions
7. Decisions
8. Follow-Up & Next Meeting

Use the following formatting guidelines for generating the PDF report:

1. The title page should have a page break before starting the rest of the document.
2. Double-check that for anything put into tabular format the contents do not overflow. Verify that the content is laid out properly before showing the user the generated document.

### Title Page

The title page needs to include the following parts:

1. Meeting Title
2. Organization Name (optional)
3. Date and Time
4. Location (optional)
5. Participants

The organization name and location can be excluded if these are internal meeting minutes as this is redundant information.

### Key Points

Create a summary of the main topics, arguments, and any points of contention.
This section should be a brief, bulleted list of items.
If the transcript was flagged as incomplete or cut off (per Error Handling), state this at the top of this section before the bulleted summary.

### Supporting Data

Include a list of documents or data presented during the meeting.

### Questions and Concerns

Create a numbered list of any questions or concerns that were raised during the meeting.
For each list item, provide the answer provided.
The questions and concerns should be bold-faced font with the answer in a regular font-face.

### Action Items

Create a tabulated list of action items.
The action items should include: 1) the action, 2) the deadline, and 3) the owners of the action.
For deadlines that aren't specified, set them as "TBD".
Action items should be listed in chronological order by due date with "TBD" items put at the end.

### Motions and Resolutions

This section is optional and can be ignored (not part of the final document) if it doesn't apply.

Create a tabulated list of motions that include the following: 1) the mover, 2) the seconder, and 3) the vote outcome.

### Decisions

Organize into general topic groups.
The decisions section must include: 1) what the decision was, 2) who made the decision, and 3) any conditions to the decision.

### Follow-Up & Next Meeting

This section is a summary of follow-up actions and decisions that will need to be addressed in a future meeting, any future meeting dates that are planned, and any specific tasks or preparations for any meetings to follow.
State each follow-up item once, in whichever framing (task, decision, or logistics) makes it clearest. Don't repeat the same item under multiple framings.
If the need for a future meeting is indicated during the meeting, make a note of that, but mark the timeline as TBD if no timeframe was given.
If no future meeting is discussed, note that none is currently scheduled.

## Document Design

Generate the document in two phases:

1. Raw generation from the transcript provided
2. Refine and reduce the sections until only the relevant information is left.

The goal of phase 2 is to reduce the meeting minutes to as small of a document as it can be without losing key information or topics.
The meeting minutes are distilled down too much that important information is lost then the resulting document is useless.
Conversely, if the meeting minutes are too long (overly verbose) then it increases the likelihood they won't be read.
The goal is to create meeting minutes that people will read and not just generate an artifact to be fed back into a LLM to processing again.

If the Key Points section is small enough to fit on the first page along with the Title Page information, then put it there.
Otherwise, leave the original document design rule of the title page being the only thing on page 1 with a page break to ensure Key Points cleanly starts on the next page.

## Error Handling

If no transcript is supplied, abort the rest of the skill processing and ask the user to provide a copy of the transcript in a document format supported by this skill.
If the transcript appears incomplete or cuts off mid-meeting (e.g., ends abruptly without a clear close, or references a meeting duration/agenda not fully covered), note this explicitly at the top of the Key Points section, and inform the user which portion may be missing rather than silently treating the transcript as complete.

