# git-skills

Local workspace for Codex skills.

## Included skills

- `conventional-commits`: Draft and validate Conventional Commits 1.0.0 messages.

## Repository structure

```text
.
├── conventional-commits/
│   ├── SKILL.md
│   └── agents/openai.yaml
└── .gitignore
```

## Usage

Use the skill in prompts like:

```text
Use $conventional-commits to write a Conventional Commit message for the changes I describe.
```

## Notes

- Main skill instructions live in `conventional-commits/SKILL.md`.
- UI metadata for skill lists/chips lives in `conventional-commits/agents/openai.yaml`.
