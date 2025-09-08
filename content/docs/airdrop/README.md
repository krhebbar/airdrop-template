---
# Airdrop Documentation - Authoring Guide

This directory contains the source files for the Airdrop Template documentation. This guide provides short notes for maintainers and future authors.

## Purpose

The primary goal of this documentation is to teach developers how to build a successful Airdrop connector using the `airdrop-template` repository as ground truth. It should be comprehensive, accurate, and easy to follow.

## Structure

The documentation is organized into the following sections:

- **Introduction (`index.mdx`)**: A high-level overview and quick start.
- **Codelab (`your-first-airdrop.mdx`)**: A step-by-step tutorial for building a simple snap-in.
- **Concepts (`concepts.mdx`)**: Explanations of core Airdrop terminology.
- **Cookbooks (`cookbook/`)**: Complete, runnable examples for specific use cases (e.g., local JSON, Notion API).
- **API Reference (`api-reference.mdx`)**: Key code snippets and configuration details.

## Authoring Process

When updating or adding new documentation, please adhere to the following principles:

1.  **Ground Truth Only**: All functional claims, code examples, and configuration details must be traceable to the source code in the `/code` directory or to cited external documentation. Do not invent behavior.
2.  **Validate Your Work**: Follow the per-file validation checklist in the root `AGENTS.md` file to ensure quality and consistency.
3.  **Fumadocs Components**: Use Fumadocs UI components (`<Steps>`, `<File>`, `<Callout>`, etc.) where appropriate to create a rich, readable experience.

For more detailed instructions on the authoring and contribution process, please refer to the main `AGENTS.md` file in the repository root.
---
