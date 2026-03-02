# HR Project Overview

This directory is an **Obsidian vault** dedicated to **Human Resources (HR)** management or tracking, likely related to activities planned for the year **2026**. It is structured for knowledge management and note-taking using Markdown.

## Directory Overview

The project is currently in its early stages, containing basic Obsidian configuration and placeholder documents. It serves as a centralized hub for organizing HR-related information, which may include:
- Candidate tracking
- Recruitment workflows
- Job descriptions
- Interview notes
- HR policy documentation

## Usage

As an Obsidian vault, this directory is intended to be opened with the [Obsidian](https://obsidian.md/) application. 
- **Note Taking**: Create new `.md` files to document HR processes or individual records.
- **Linking**: Use `[[Internal Links]]` to connect related concepts (e.g., linking a candidate to a specific job role).
- **Tagging**: Use `#tags` for easy categorization of notes.
- **Graph View**: Utilize Obsidian's built-in graph view to visualize connections between different HR documents.

## Vacancy Management Workflow

When managing vacancies:
1.  **Create New Vacancy File**: Create a separate `.md` file for the vacancy.
    *   **Filename**: `{company} — {position}.md` (using an em dash and spaces).
    *   **Initial Location**:
        *   If the vacancy is for "future consideration" or "favorites", place the file in the `00.For Future` folder, and the 'Applied' date should be omitted.
        *   For all other new vacancies, place the file in the `01.Applied` folder initially.
2.  **Mandatory Date Handling**: For all statuses except "For Future" (`00.For Future`), the 'Applied' date is mandatory. If it's not specified in the prompt, use the actual current date as the default.
3.  **Transition from 'For Future' to 'Applied'**: If a vacancy currently in the `00.For Future` folder is indicated as "applied for":
    a. Move the vacancy file from `00.For Future` to the `01.Applied` folder.
    b. Assign the current date (at the moment of this transition) as the 'Applied' date in the vacancy file.
4.  **Conditional Action for Schedule Section**: If a `## 📅 Schedule` section is added to a vacancy file, and no `## 📅 Schedule` section existed previously in that file, then the vacancy file must be moved to the `02.Interview` folder.
5.  **Event File Creation**: If a `## 📅 Schedule` section is added to a vacancy file, create an additional file in `Calendar\Interview\` using the name format `{date|YYYY-MM-DD} {company} — {interviewer_name}.md`. For details on the content and format, refer to the "Calendar Event Management Workflow" section below.
6.  **Rejection Process**: If a company (and optionally a specific position) indicates a rejection, move the corresponding vacancy file to the `99.Rejected` folder.
7.  **Vacancy Closed Process**: If a vacancy for a specified company (and optionally a specific position) is found to be closed (e.g., job posting removed), move the corresponding vacancy file to the `99.Rejected` folder.
8.  **Offer Process**: When a vacancy is identified as having an offer, move the corresponding vacancy file to the `03.Offer` folder.
9.  **Contextual Understanding**: The context for task execution is typically the company name and, if relevant, the position name (especially if there are multiple positions within the same company). This context is provided in the prompt. If the company or position is unclear, always ask for clarification.
10. **Status Determination**: The status of a vacancy is determined solely by the folder its `.md` file resides in (e.g., `01.Applied`, `02.Interview`, `99.Rejected`, `00.For Future`, `03.Offer`).
11. **Duplicate Check**: Before creating a new vacancy file, check for existing files with the same company name and/or a very similar position title. If a potential duplicate is found, warn the user and ask for confirmation before proceeding.

### Vacancy File Template (Full Definition)

When creating vacancy files:
- The `## 🚀 Details` section is **mandatory**.
- The `## 📅 Schedule` and `## Description` sections are **optional**. These sections should **only be included if corresponding data is available**. For example, if there is no information about a schedule (interviewer, time, link), the `## 📅 Schedule` section should not be created. Similarly, if there is no position description, the `## Description` section should not be created. Sections can be added to the file as more relevant data becomes available.
- **Section Order**: New sections added to a vacancy file should always be placed at the beginning of the file, before existing sections. If multiple instances of a section type are added, the newest should appear first.

Template structure:
```markdown
## 📅 Schedule

* **Interviewer:** {name}
* **Time:** {date|YYYY-MM-DD} {start_time|HH:mm}—{end_time|HH:mm}
* **Link:** {link}

## 🚀 Details

*   **Company:** {company}
*   **Position:** {position}
*   **Applied:** {applied_date}
*   **Link:** {link}

## Description

{position_description}
```
*   **Date Format**: Use `dd.mm.yy` (e.g., `09.02.26`).
*   **Time Format**: Use `hh:MM` for 24-hour format (e.g., `14:30`).
- Filename mask: `<company> — <position>.md`
- Folders for vacancies based on status:
    - `Applied` -> `01.Applied`
    - `Offer` -> `03.Offer`
    - `REJECTED` -> `99.Rejected`
    - `CLOSED` -> `99.Rejected`
    - `For Future` -> `00.For Future`

## Agent Instructions

- All instructions should be recorded in GEMINI.md.

## Calendar Event Management Workflow

When asked to create a calendar event not associated with a vacancy:
1.  **Input Data**: You will be provided with event details (date, company, interviewer name, start time, end time).
2.  **Event File Creation**: Create a file in `Calendar\Interview\` using the name format `{date|YYYY-MM-DD} {company} — {interviewer_name}.md`.
3.  **Content Template**: The content of this file should follow the YAML front matter template, with `endTime` calculated as 30 minutes after `startTime` if not explicitly provided:
    ```
    ---
    title: {company} — {interviewer_name}
    allDay: false
    startTime: {start_time|HH:mm}
    endTime: {end_time|HH:mm}
    date: {date|YYYY-MM-DD}
    completed:
    link: {link}
    ---
    ```
4.  **No Vacancy File Updates**: This action should NOT trigger any updates or movements of vacancy files.

## Cover Letter Generation Workflow

When asked to write a cover letter:
1.  **Vacancy and Company Details**: You *must* specify the vacancy and company name. If not provided, I will ask for clarification.
2.  **Template Selection**: I will use a suitable template file, either provided by you or identified by me (e.g., `Senior React Developer.md`), based on the vacancy title. I will not create this file if it doesn't exist.
3.  **Clarification**: If there is any ambiguity in selecting the template, I will ask for confirmation or allow you to specify the correct content to use as a template.
4.  **Populate Template**: I will replace the macro `{company_name}` in the chosen template with the provided company name.
5.  **Refinement**: I will then rephrase the text, check for spelling and grammar, improve phrase construction, and make other stylistic enhancements.
6.  **Output**: The final cover letter will be displayed directly in the console.
7.  **Preservation**: The original cover letter template file will remain unchanged and should never be modified by this process.
