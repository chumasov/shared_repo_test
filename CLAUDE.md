# Instructions for Claude

Two people work on this project, each with their own Claude. This repository is how
the two Claudes share progress. Follow these rules in every session.

## Language

- Write every `.md` file in English.
- Write every code comment in English.
- The chat with the user can be in any language; only repository content must be English.

## Files

| File | What goes in it |
|------|-----------------|
| `PLAN.md` | Hackathon plan: challenge, product concept, tech decisions, schedule, and "Where we stopped". Read it before any hackathon work. |
| `STATUS.md` | Progress: what each person has done, is doing now, and plans next. |
| `design.md` | Everything about design: UI/UX, visual style, colors, fonts, layouts, design decisions and their reasons. |
| `README.md` | General project description only. Do not put status or design notes here. |

Never put design notes in `STATUS.md`; put them in `design.md` and, if useful, add a
one-line pointer in `STATUS.md` (for example "Updated button styles, see design.md").

## At the start of every session

1. Run `git pull` to get the partner's latest updates.
2. Read `PLAN.md`, `STATUS.md` and `design.md`.
3. Briefly tell the user what the partner did since their last update and what they
   are working on now.

## After finishing work (or when the user asks to update the status)

1. Run `git pull` first.
2. Update **only the current user's own section** in `STATUS.md`. Never edit the
   partner's section, so the two Claudes never conflict.
   - Move finished items to "Done" with the date (YYYY-MM-DD).
   - Keep "In progress" and "Next" current.
   - Update the "Last updated" date of that section.
3. If any design work was done or decided, record it in `design.md`
   (add to the relevant section and to the "Decision log" with the date and author).
4. Commit with a short English message, e.g. `status: <name> - <what changed>`,
   and `git push`.
5. If the push is rejected, run `git pull --rebase`, resolve any conflict while
   keeping both people's text, and push again.

## Who is who

Identify the current user by their GitHub login (`gh api user --jq .login`) and use the
section in `STATUS.md` that matches it. If the login has no section yet, add one.
