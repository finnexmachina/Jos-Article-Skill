---
name: product-learn
description: Deep-research a product and build a comprehensive profile. Usually runs automatically inside /article on first use, but can be invoked standalone to rebuild or update.
argument-hint: [product name]
allowed-tools:
  - WebSearch
  - WebFetch
  - Read
  - Grep
  - Write
  - Edit
  - Bash
---

# Product Learner (Standalone)

This usually runs automatically inside `/article` when no product profile exists.

Use this standalone command to:
- Rebuild a product profile from scratch
- Update a stale profile with fresh data
- Go deeper on specific modules
- Research a second product

## Run

1. Check `${CLAUDE_SKILL_DIR}/../article/products/` for existing profiles
2. If profile exists, offer: update, go deeper, or start fresh
3. Follow the full pipeline at `${CLAUDE_SKILL_DIR}/../article/product-learner.md`
4. Save to `${CLAUDE_SKILL_DIR}/../article/products/[product].md`
