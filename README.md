# chat-skills

A collection of AI skills I'm developing — modular instructions that extend how a model handles specific kinds of requests. Model-agnostic by design.

## Skills

### `ponder`
Flag a claim you're unsure about with `/ponder` in front of it, anywhere in your message. The model checks that specific claim (using web search when it's the kind of thing that could be outdated or context-dependent), reports a quick verdict (✓ correct, ✗ wrong, ! mixed, ? unverifiable, ≠ contradicts something you said earlier), and then continues with the rest of your request as normal — using the corrected info if needed.

### `ste100_inspired` (clear-tech)
Rewrites technical text — manuals, error messages, API docs, troubleshooting steps — into short, plain, unambiguous sentences. Inspired by Simplified Technical English (ASD-STE100). Works in any language. Use it for a one-off rewrite of a specific piece of text, or turn it on to make the model write this way for the rest of the conversation. Code, quotes, numbers, and technical facts are always kept exact — only the phrasing gets simplified.

## License

MIT — see [LICENSE](LICENSE).
