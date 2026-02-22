# Video.js Agent Skill

This repository contains a specialized Agent Skill for working with [Video.js](https://videojs.com/).

## What is an Agent Skill?
Skills are modular, self-contained packages that extend an AI Agent's capabilities by providing specialized knowledge, workflows, and tools. This skill equips agents with deep knowledge of the Video.js API, architecture, and common use cases based on its official documentation and guides.

## Contents

- `SKILL.md`: The core metadata and instructions for the agent on how to use this knowledge.
- `references/docs.md`: Comprehensive API reference generated from Video.js JSDoc.
- `references/guide.md`: Step-by-step guides, setup configurations, and best practices.

## How to use

Si usas un gestor de skills soportado mediante `npx`, puedes instalar esta skill directamente desde este repositorio ejecutando el siguiente comando:

```bash
npx skills add https://github.com/danraf77/videojs-skill --skill videojs-skill
```

Si prefieres usar los archivos directamente, puedes descargar el repositorio o apuntar a tu agente a los archivos de la carpeta `references/`.

## Building the .skill package

If you have the Skill Creator scripts, you can package this repository into a `.skill` file:

```bash
python scripts/package_skill.py /path/to/videojs-skill
```
