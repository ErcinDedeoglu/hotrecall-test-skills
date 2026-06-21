# hotrecall-test-skills

A **persistent test fixture** for the [hotrecall](https://hotrecall.com) agentic
skill-ingestion pipeline. It holds a small `SKILL.md` source skill that the
hotrecall converter (opencode + `CONVERT-TO-SKILL.md`) turns into a finalized
skill — used to verify the end-to-end conversion path and the Sentry `gen_ai.*`
AI-Agent tracing.

This repo is intentionally kept alive so verification runs can simply re-trigger
a refresh against it instead of recreating throwaway data each time.

## Layout

```
skills/
  conventional-commits/
    SKILL.md        # source skill (frontmatter: name + description)
```

Discovery walks the tree for any file named `SKILL.md`.
