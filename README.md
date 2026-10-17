# Document Summarizer

An Agent Skill that reads user-provided documents and returns a clear, accurate summary in **no more than 10 lines**.

Built for the [Agent Skills](https://agentskills.io/specification) format: a folder with a `SKILL.md` file containing YAML frontmatter and Markdown instructions.

## Purpose

Help an AI agent turn a long document into a short, reliable summary. The skill prioritizes accuracy over completeness and never invents information.

It identifies the main topic, key points, important findings, conclusions, and essential recommendations when they are present.

## Who it is for

University students, researchers, developers, professionals, and anyone who wants to understand long documents quickly.

## Features

- Hard limit of 10 physical text lines per summary.
- Optional document title kept within the same 10-line budget.
- Numbered lines when the content is a list of points.
- Clear notes for missing pages, unreadable text, tables, figures, and conflicting information.
- Separate 10-line summaries for multiple documents unless a combined summary is requested.
- Safeguards against hallucination and against instructions embedded in documents.

## Trigger phrases

- "Summarize this document in 10 lines or less."
- "Give me a short summary of this file."
- "Extract the key points from this document."

## Supported inputs

- Plain text and Markdown files.
- PDF, DOCX, and similar documents readable by the agent's tools.
- Pasted or in-conversation text.
- Web pages the agent is permitted to fetch.

Formats the agent cannot read are reported plainly; the skill never claims to have read inaccessible content.

## Folder structure

```
.
├── SKILL.md      # Metadata (YAML frontmatter) + instructions
├── README.md     # This file
└── LICENSE       # MIT License
```

No scripts, dependencies, or configuration files are required.

## Frontmatter fields

| Field         | Value                                        |
| ------------- | -------------------------------------------- |
| `name`        | `document-summarizer`                        |
| `description` | What the skill does and when to use it       |
| `license`     | `MIT`                                        |

## Installation

1. Copy this project folder into the skills directory used by your agent.

   A common location is `~/.config/<product>/skills/` or a project-level `.skills/` folder. Check your agent's documentation for the exact path.

   ```bash
   cp -r . ~/.config/<product>/skills/document-summarizer
   ```

2. Restart or reload the agent so it picks up the new skill.
3. Confirm the agent can see the skill (for example by asking it to summarize a document).

## Usage examples

- "Summarize this document in 10 lines or less."
- "Give me a short summary of this file."
- "Extract the key points from this document."

## Example output

```
Title: Quarterly Network Security Report
1. The document reviews network security incidents from Q1.
2. It reports a rise in phishing attempts targeting staff.
3. Two minor breaches were contained within one working day.
4. Multi-factor authentication reduced account takeovers.
5. The main recommendation is mandatory security training.
6. It also advises quarterly access reviews for all systems.
7. Remaining risks include unpatched third-party software.
8. The report concludes that controls are broadly effective.
9. No major data loss was reported during the period.
```

That example is 10 lines including the title line.

## Validation

The skill follows the naming and frontmatter rules in the official specification. To validate with the reference tool:

```bash
pip install skills-ref
skills-ref validate .
```

If `skills-ref` cannot be installed, perform these manual checks:

- Folder name is lowercase, uses only letters, numbers, and hyphens, is 64 characters or fewer, and starts and ends with an alphanumeric character.
- `name` in the frontmatter exactly matches the folder name.
- `description` is non-empty and 1024 characters or fewer.
- `license` is present.
- `SKILL.md` body is under 200 lines and contains all required sections.

## License

MIT License. Copyright (c) 2026 Aminu Gambo Abubakar. See `LICENSE`.
