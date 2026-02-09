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
5.  **Rejection Process**: If a company (and optionally a specific position) indicates a rejection, move the corresponding vacancy file to the `99.Rejected` folder.
6.  **Vacancy Closed Process**: If a vacancy for a specified company (and optionally a specific position) is found to be closed (e.g., job posting removed), move the corresponding vacancy file to the `99.Rejected` folder.
7.  **Contextual Understanding**: The context for task execution is typically the company name and, if relevant, the position name (especially if there are multiple positions within the same company). This context is provided in the prompt. If the company or position is unclear, always ask for clarification.
8.  **Status Determination**: The status of a vacancy is determined solely by the folder its `.md` file resides in (e.g., `01.Applied`, `02.Interview`, `99.Rejected`, `00.For Future`).

### Vacancy File Template (Full Definition)

When creating vacancy files:
- The `## 🚀 Details` section is **mandatory**.
- The `## 📅 Schedule` and `## Description` sections are **optional**. These sections should **only be included if corresponding data is available**. For example, if there is no information about a schedule (interviewer, time, link), the `## 📅 Schedule` section should not be created. Similarly, if there is no position description, the `## Description` section should not be created. Sections can be added to the file as more relevant data becomes available.
- **Section Order**: New sections added to a vacancy file should always be placed at the beginning of the file, before existing sections. If multiple instances of a section type are added, the newest should appear first.

Template structure:
```markdown
## 📅 Schedule

* **Interviewer:** {name}
* **Time:** {date}
* **Link:** {link}

## 🚀 Details

*   **Company:** {company}
*   **Position:** {position}
*   **Applied:** {applied_date}
*   **Link:** {link}

## Description

{position_description}
```
- Filename mask: `<company> — <position>.md`
- Folders for vacancies based on status:
    - `Applied` -> `01.Applied`
    - `REJECTED` -> `99.Rejected`
    - `CLOSED` -> `99.Rejected`
    - `For Future` -> `00.For Future`