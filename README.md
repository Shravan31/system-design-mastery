# System Design Mastery

A 24-week, completely free learning workspace for an intermediate software engineer preparing for product-company interviews, with a longer-term goal of growing toward senior engineer / software architect responsibilities.

## Learning protocol

See [`LEARNING-PROTOCOL.md`](LEARNING-PROTOCOL.md) for our persistent teaching approach, assessments, weekly feedback scorecard, readiness decisions, and chat-window continuity. Read it at the start of a new chat to resume the learning journey consistently.

## How to use this repository

1. Read `ROADMAP.md` and `resources/LEARNING-ORDER.md`.
2. Each week, work from the matching `weeks/week-XX/README.md`.
3. Tick tasks only when you can explain or demonstrate them.
4. Save diagrams, code, trade-off notes, and assessments in the relevant folders.
5. Update `PROGRESS.md` during your weekly review.
6. Keep DSA practice running alongside System Design; see `05-DSA/README.md`.

## Suggested weekly commitment

| Activity | Time |
|---|---:|
| Concepts and videos | 2 hours |
| Reading / documentation | 1 hour |
| Hands-on implementation | 1.5 hours |
| Design problem / DSA | 1.5 hours |
| Review and notes | 1 hour |
| **Total** | **7 hours** |

If you only have five hours in a particular week, reduce the amount of content rather than skipping the assessment and review.

## Repository structure

- `weeks/`: weekly goals, ordered references, tasks, and assessments.
- `projects/`: practical project briefs and acceptance criteria.
- `05-DSA/`: parallel coding-interview preparation.
- `resources/`: free learning resources in recommended order.
- `templates/`: reusable notes and review templates.
- `PROGRESS.md`: single overview of completion.

## Create your GitHub repository

Create a new **public or private** repository named `system-design-mastery` on GitHub. For a personal learning log, private is fine; public is useful if you want feedback and a portfolio.

Then, from the folder where you extracted this project:

```bash
cd system-design-mastery
git init
git add .
git commit -m "chore: initialize system design learning roadmap"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/system-design-mastery.git
git push -u origin main
```

Replace `YOUR-USERNAME` with your GitHub username.

## Recommended Git workflow

Use small, meaningful commits:

```bash
git add .
git commit -m "week-01: document requirements and capacity estimates"
git push
```

Suggested commit prefixes: `week-`, `dsa-`, `project-`, `notes-`, `assessment-`.

## Definition of done

A week is complete when:
- The learning tasks are checked.
- Notes are written in your own words.
- The assessment is attempted without copying a solution.
- Any assigned design / coding deliverable is committed.
- You write a short reflection: what is clear, what is still confusing, and what you will revisit.

## Important

This is a learning plan, not a guarantee of interview readiness or a fixed hiring timeline. Interview expectations vary by company, role, and level. Adapt the plan to job descriptions you are targeting.
