# Contributing

These prompts run in production on [winthorpe.net](https://winthorpe.net), where users pick an AI model and get both analyses on a stock. Every improvement merged here reaches those users at the next tagged version, so contributions are welcome and reviewed with care.

## How to propose a change

1. **Discuss first for anything structural.** Open an issue if you want to add or remove a scored dimension, change a scoring band, or change the JSON block. Those changes need matching work on the site.
2. **Open a pull request for wording and scoring guidance.** Clearer pillar descriptions, scoring anchors, missing-data rules and the like can go straight to a PR. Explain what problem you saw in real output and, if you can, paste before-and-after excerpts from a model run.
3. **Keep the contract.** Every prompt must keep its front matter, its placeholders, and its closing JSON block with the same keys. The site has a contract test that fails on any of these.
4. **Test on at least two stocks and two models** if you can. The site runs these prompts on models from Google, Anthropic, OpenAI, DeepSeek and Moonshot; a change that helps one model and hurts another is a discussion, not a merge.

## Rules every prompt follows

- One file per rubric under `prompts/`, kebab-case, with front matter: `id`, `title`, `summary`, `placeholders`.
- Placeholders are `{{TICKER}}`, `{{NAME}}`, `{{DATE}}` and `{{DATA}}`. The data block format is in `prompts/data-table-template.md`.
- The model is told to use only the supplied data for numbers and its own knowledge for qualitative judgement. Prompts do not ask the model to browse.
- Each scored dimension is 0-20 and the interpretation bands are stated in the prompt so results are comparable across stocks and models.
- The prompt ends with the machine-readable JSON block.

## Releases

Maintainers tag versions as `vMAJOR.MINOR.PATCH` and record them in `CHANGELOG.md`. A patch changes wording without moving scores much; a minor changes scoring guidance; a major changes dimensions or the JSON contract. The site pins a tag and syncs it explicitly; nothing here changes production on its own.

## License

By contributing you agree your contribution is released under the MIT license in `LICENSE`.
