# AI-Powered HR Vacancy Management System

## 🚀 Project Overview

This project presents an innovative, agent-driven system for managing Human Resources vacancies, leveraging the power of an AI Command-Line Interface (CLI) agent and Obsidian-style Markdown files. Designed for efficiency and clarity, this system transforms the often-cumbersome task of tracking job applications into a streamlined, interactive process. It acts as a digital HR vault, where the status and details of each vacancy are managed through intuitive file operations guided by natural language commands.

## ✨ Why This System?

Traditional HR tracking methods can be static and manual. This system addresses those challenges by:
-   **Automating Workflow**: An intelligent agent handles file creation, updates, and movements based on your natural language instructions.
-   **Dynamic Status Management**: The status of a vacancy is visually and logically represented by its location within a structured folder system.
-   **Centralized Knowledge**: All vacancy details are stored in easily readable Markdown files, compatible with Obsidian for enhanced knowledge management capabilities.
-   **Automated Event and Calendar Management**: Seamlessly creates interview events and manages your calendar, keeping track of your schedule efficiently.
-   **Template-Based Cover Letter Generation**: Generates customized cover letters on demand, utilizing templates to match specific vacancies and companies without manual editing.
-   **Scalability & Clarity**: As your hiring pipeline grows, the system maintains organization and provides immediate insights into the status of every application.

## 🛠️ How It Works: The Agent-Driven Workflow

At its core, this system operates through interaction with a sophisticated AI CLI agent (like myself). You provide instructions, and the agent executes predefined workflows, manipulating Markdown files and folders to reflect the real-time status of your vacancies. The system is entirely driven by explicit rules, ensuring consistent and predictable behavior.

### Core Principles:

1.  **Status by Folder**: A vacancy's status is determined *solely* by the folder its Markdown file resides in.
    -   `00.For Future/`: Vacancies saved for future consideration.
    -   `01.Applied/`: Applications that have been submitted.
    -   `02.Interview/`: Vacancies currently in the interview stage.
    -   `99.Rejected/`: Applications that have been rejected or closed.
2.  **Template-Based Files**: All vacancy details are stored in individual Markdown files generated from a consistent template.
3.  **Dynamic Date Handling**: Dates are automatically managed, defaulting to the current date if not specified for mandatory fields.

### Vacancy Management Workflow Highlights:

-   **Creating New Vacancy Files**: New vacancies are initiated by creating a Markdown file in either `01.Applied/` (default) or `00.For Future/`.
-   **Mandatory Date Handling**: For most statuses, the 'Applied' date is mandatory. If not provided, the system defaults to the current date. For `00.For Future` vacancies, this date is explicitly omitted.
-   **Conditional Actions (e.g., Interview Scheduling)**: Adding a `## 📅 Schedule` section to a vacancy file automatically triggers its move to `02.Interview/` and the creation of a corresponding event file in `Calendar/Interview/` for calendar integration.
-   **Rejection/Closed Processes**: Indicating a rejection or closure for a vacancy automatically moves its file to `99.Rejected/`.
-   **Contextual Understanding**: The agent understands commands based on company and position names, asking for clarification if needed.

## 📄 Vacancy File Template (Full Definition)

All vacancy files adhere to the following structure. The `## 🚀 Details` section is mandatory, while `## 📅 Schedule` and `## Description` are optional, included only when relevant data is available. New sections are always prepended to maintain a chronological event log.

**Template structure:**

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

-   **Filename mask**: `{Company} — {Position}.md` (using an em dash `—`)

## 💡 Prompt Examples: Interacting with the Agent

Here are examples of how you would interact with the CLI agent to manage your vacancies:

### 🆕 Creating New Vacancies

-   **Create a new applied vacancy**:
    `"new vacancy: company CompanyA, position Software Engineer, link https://jobs.globaltech.com/fullstack-dev, applied today."`
-   **Create a vacancy for future consideration**:
    `"add to future vacancy: company CompanyB, position Senior Fullstack Developer, link https://careers.innovatecorp.com/senior-fs-ts-dev"`

### 🗓️ Managing Status & Schedules

-   **Add an interview schedule**:
    `"create call for Innovate Corp. — Senior Software Engineer on March 15, 2027 10:00 - 10:30 with Jane Doe, link https://meet.example.com/meeting-id"`
    *(This would automatically move the file to `02.Interview/`)*
-   **Mark a vacancy as rejected**:
    `"company Quantum Solutions — Senior Backend Developer rejected the application, update documents"`
    *(This would move the file to `99.Rejected/`)*
-   **Mark a vacancy as closed**:
    `"the vacancy for Pinnacle Tech — Lead QA Engineer is closed"`
    *(This would move the file to `99.Rejected/`)*
-   **Update applied date for a vacancy**:
    `"correct the applied date for Future Systems — Data Scientist to March 10th"`
    *(This updates the date within the file)*

### 📝 Other Operations

-   **Add a description section**:
    `"add a description section to Global Dynamics — Cloud Engineer. I will fill it myself."`
    *(This adds the `## Description` section to the file)*
-   **Update a link**:
    `"for Apex Innovations — DevOps Engineer change the link to https://jobs.synergysolutions.com/fs-js-eng-new-url"`

### 💌 Cover Letter Generation

This system also empowers you to quickly generate customized cover letters.
-   **How it works**: When you request a cover letter, the agent intelligently searches for a suitable template within the `@Cover\` directory. This directory can contain multiple templates (e.g., `Senior Frontend Dev.md`, `Fullstack Engineer.md`) allowing for tailored responses based on the specific role. It then replaces placeholders (like `{company_name}`) with the provided details, refines the text for optimal clarity, grammar, and style, and presents the polished cover letter directly in your console. This process is non-destructive; no files on your system are created or modified.
-   **Example**:
    `"write a cover letter for the position of Senior Frontend Developer at Stellar Innovations"`

### ⚙️ Local Deployment

To get this AI-powered HR Vacancy Management System up and running on your local machine, follow these steps:

1.  **Clone the Repository**:
    Begin by cloning the project repository from GitHub:
    ```bash
    git clone https://github.com/rahmanroman/ai-vms.git
    cd ai-vms
    ```

2.  **Prerequisites**:
    Ensure you have the following installed:
    *   **Gemini CLI**: This project is designed to be interactive with the Gemini CLI. If you don't have it, please refer to its official documentation for installation instructions.
    *   **Obsidian (Optional)**: While not strictly required for the CLI agent's operation, Obsidian is the recommended application for interacting with the Markdown files as a knowledge base.
    *   **Obsidian Full Calendar Plugin (for event integration)**: To effectively manage and visualize interview schedules, install the [Full Calendar plugin](https://github.com/obsidian-community/obsidian-full-calendar) in Obsidian. Event files are automatically created by the agent in `Calendar/Interview/` and can be viewed and managed through this plugin.

3.  **Initial Setup**:
    Navigate into the cloned directory (`ai-vms`). This repository's root directory serves as the Obsidian vault containing all vacancy data.

4.  **Launch the Gemini CLI Agent**:
    Execute the Gemini CLI from the root of the `ai-vms` directory (or within the `HR` sub-directory, depending on Gemini CLI's context handling). Follow the Gemini CLI's instructions to load the project context.
    ```bash
    # Example command to launch Gemini CLI (might vary based on your setup)
    gemini
    ```
    Once the CLI agent is active, it will load the project context and be ready to receive commands as outlined in the "Prompt Examples" section.

5.  **Interacting with the System**:
    You can now manage your vacancies by issuing natural language commands to the Gemini CLI agent. The agent will read your instructions, apply the defined workflows (such as creating files, moving them between status folders, or updating their content), and provide feedback on its actions.

## 🏗️ Project Structure

The project's root directory functions as an Obsidian vault. Vacancy files are organized into subfolders corresponding to their status:
-   `00.For Future/`
-   `01.Applied/`
-   `02.Interview/`
-   `99.Rejected/`

## 🤝 Contribution

This project is open-source and contributions are welcome! Feel free to explore, adapt, and enhance this agent-driven HR management system. Your insights can help evolve this tool for even greater efficiency.
