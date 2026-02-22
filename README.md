# Video.js Agent Skill

This repository contains a specialized Agent Skill for working with [Video.js](https://videojs.com/).

## What is an Agent Skill?
Skills are modular, self-contained packages that extend an AI Agent's capabilities by providing specialized knowledge, workflows, and tools. This skill equips agents with deep knowledge of the Video.js API, architecture, and common use cases based on its official documentation and guides.

## Contents

- `SKILL.md`: The core metadata and instructions for the agent on how to use this knowledge.
- `references/docs.md`: Comprehensive API reference generated from Video.js JSDoc.
- `references/guide.md`: Step-by-step guides, setup configurations, and best practices.

## How to use

If you are using an AI agent that supports `.skill` files:
1. Download the `videojs-skill.skill` package from the Releases or build it yourself using the Skill Creator.
2. Load it into your agent's workspace or skill registry.

Alternatively, the agent can be pointed directly to the markdown files in the `references/` directory.

## Building the .skill package

If you have the Skill Creator scripts, you can package this repository into a `.skill` file:

```bash
python scripts/package_skill.py /path/to/videojs-skill
```
