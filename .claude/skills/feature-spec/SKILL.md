---
name: feature-spec
description: Start spec work for a new feature or the next roadmap phase — finds the next unstarted phase in specs/roadmap.md (or uses a feature name given as an argument), creates a feature branch, asks the user three grouped questions about scope, decisions, and context, then writes plan.md, requirements.md, and validation.md into a new dated directory under specs/. Use whenever the user wants to kick off spec work, start the next feature or phase, or says things like "next phase", "start the next feature", "let's spec out X", or "/feature-spec".
---

# Feature Spec

Kicks off spec work for a feature: branch + three planning docs (`plan.md`,
`requirements.md`, `validation.md`) in a new `specs/YYYY-MM-DD-feature-name/`
directory. This captures a workflow the user previously typed out by hand each
time, so follow it exactly in order — the value is in the repeatability.

## 1. Determine the feature

- If the user (or `/feature-spec <arg>`) gave an explicit feature name/topic,
  use that as the feature.
- Otherwise, read `specs/roadmap.md` and find the next phase that hasn't been
  started yet (no matching `specs/*-<phase-name>/` directory already exists,
  and nothing suggests it's done — check `git log` / existing specs
  directories if it's ambiguous which phase is "next"). Roadmap phases are
  usually ordered (Phase 0, Phase 1, ...) — pick the first one without a spec
  directory.

Derive a short kebab-case feature name from the phase/topic (e.g. "Phase 2 —
Agent records" → `agent-records`).

## 2. Create the branch

Check `git status` first — if there are uncommitted changes, flag it to the
user before switching branches (don't lose work). Create and check out a new
branch named after the feature, e.g. `feature/agent-records`. Use whatever
branch naming convention the repo already uses if one is evident from
`git branch -a` or recent history; otherwise default to `feature/<kebab-name>`.

## 3. Ask about the spec — before writing anything to disk

Read `specs/mission.md` and `specs/tech-stack.md` first so your questions and
options are grounded in the project's actual goals and stack, not generic
boilerplate.

Then use the **AskUserQuestion** tool, grouped into exactly these three
questions, in one call:

1. **Scope** — what's in and out of bounds for this feature slice. Offer
   options that reflect realistic scope cuts for this phase (e.g. minimal
   vs. fuller version), grounded in what the roadmap phase actually says.
2. **Decisions** — the key technical or product decision(s) this feature
   needs made before implementation can start (e.g. a data model choice, a
   library/approach choice, a UX behavior). Offer the realistic options.
3. **Context** — anything else needed to write accurate docs: dependencies on
   other phases, constraints, open questions, who this is for, deadline
   pressure, etc.

Do **not** create the directory or any files until these answers are in hand.

## 4. Create the spec directory

Create `specs/YYYY-MM-DD-feature-name/` using today's actual date and the
kebab-case feature name from step 1.

## 5. Write the three docs

Base all three docs on the AskUserQuestion answers, plus `specs/mission.md`
and `specs/tech-stack.md` for consistency with the project's stated goals and
stack choices. Reference the relevant roadmap phase text where useful.

**`requirements.md`** — scope, decisions, and context:
- What's in scope / explicitly out of scope for this slice (from the scope
  answer)
- Key decisions made and why (from the decisions answer)
- Relevant context, constraints, dependencies (from the context answer)
- Link back to the roadmap phase this fulfills

**`plan.md`** — a series of numbered task groups for implementation:
- Group related tasks (e.g. "1. Data model", "2. API/routes", "3. UI",
  "4. Tests") rather than a flat checklist — task groups should reflect an
  order that makes sense to build and demo incrementally, consistent with the
  roadmap's "small enough to ship and demo on its own" philosophy.
- Keep each task concrete enough to act on, not vague restatements of the
  requirements.

**`validation.md`** — how to know the implementation succeeded and can be
merged:
- Concrete, checkable criteria (tests passing, specific flows working
  end-to-end, lint/typecheck clean, etc.) — pull from `specs/tech-stack.md`
  for what CI/tooling already exists so validation steps are things that
  actually run in this repo.
- Tie criteria back to the requirements/scope so "done" is unambiguous.

## 6. Wrap up

Tell the user the branch name and the new spec directory path. Don't commit
the new files automatically — let the user review first unless they ask you
to commit.
