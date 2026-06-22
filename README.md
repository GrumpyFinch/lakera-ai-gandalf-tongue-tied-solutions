# Tongue Tied Gandalf - Prompt Injection Writeups

My solutions to **Tongue Tied Gandalf**, a [Lakera Gandalf](https://gandalf.lakera.ai/) challenge for learning **LLM prompt injection**. In this version Gandalf (and friends) have each been *forbidden from talking about a specific topic*. The goal: craft inputs that get them to discuss the forbidden topic anyway.

This repo documents, for each level: the forbidden topic, the exact prompt I used, and *why* I think it worked.

> Sibling repo: my [original Gandalf](../gandalf-original) writeups (the password-extraction game) live separately.

## Disclaimer

This is **educational security content**. Gandalf is an intentionally vulnerable practice game built by [Lakera](https://www.lakera.ai/) to teach how prompt injection works and how to defend against it. Everything here targets that public training sandbox, **not** real or production systems. The goal is to understand these attacks well enough to defend against them.

## Levels (2/5)

| Level | Forbidden Topic | Writeup | Status |
|------:|-----------------|---------|:------:|
| 1 | MAGIC | [writeup](solutions/level-01.md) | ✅ |
| 2 | VEGETABLES | [writeup](solutions/level-02.md) | ✅ |
| 3 | _TBD_ | - | ⬜ |
| 4 | _TBD_ | - | ⬜ |
| 5 | _TBD_ | - | ⬜ |

## File Structure

```
.
├── README.md            # this file (overview + index)
├── LICENSE
├── images/              # screenshots for each level
└── solutions/
    ├── TEMPLATE.md      # copy this for each new level
    ├── level-01.md      # each writeup embeds its screenshot
    ├── level-02.md
    └── ...
```

## Technique Glossary

Common moves for getting a model to discuss a forbidden topic (I tag each writeup with the ones it uses):

- **Talk around the trigger word**: describe or approach the topic without ever naming it, so keyword filters on your input don't fire.
- **Oblique entry point**: pick an adjacent subject the model will *voluntarily* expand into the forbidden one (e.g. ask about a fictional universe so it brings up its magic itself).
- **Roleplay / framing**: wrap the request in a story, game, or persona that lowers the model's guard.
- **Indirect elicitation**: extract the topic without a direct request: hints, examples, "what surrounds X."
- **Encoding / obfuscation**: reversed words, spacing, other languages, Base64 to dodge filters.
- **Output-format games**: ask for a poem, list, or table so a substring filter misses the leak.
- **Context splitting**: keep the forbidden word and the request out of the same obvious place.

---

*Built for learning. If you're defending an LLM app, the takeaway is: LLM models will reveal a banned topic on their own if you give them an adjacent "on-ramp".*
