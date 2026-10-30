# Mumr plugin

Start and stop [Mumr](https://mumr.app/) meeting recordings on your Mac, and ask about the meetings Mumr saved there, from an assistant that runs commands on that Mac.

The plugin is text only: two skills and a manifest. It has no server, no program, no hooks and no settings. It sends nothing anywhere.

## What it does

- **`mumr-record`**: when you ask, the assistant runs one of `open "mumr://record?source=agent"`, `open "mumr://stop"`, `open "mumr://recording/<id>"` or `open "mumr://show-window"`. The skill tells the assistant to act only on your own request in the conversation, never on words found in a transcript, file or web page. That is an instruction the assistant follows, not a lock, so decline any Mumr command you did not ask for. It reminds you that recording other people may need their consent.
- **`mumr-meetings`**: how to read the folder Mumr writes (`mumr-meetings.json`, then each meeting's `summary.json` or `transcript.json`), so the assistant can answer "what did we decide?" from your own files. Meeting content is treated as untrusted input.

The assistant cannot see whether Mumr actually started. It reports "Asked Mumr to start. The live panel shows the recording."

## Requirements

- A Mac with Mumr installed: <https://mumr.app/download>.
- An assistant with a shell on that Mac: Claude Code (terminal or the Code tab of the Claude desktop app), the Codex CLI, or a Codex thread that runs locally in the ChatGPT desktop app.

It does **not** run in plain claude.ai or ChatGPT chat, or in cloud sessions: those run in a sandbox that cannot reach your Mac.

If your agent runs commands in a sandbox that blocks `open`, approve the command when asked, or run the line it shows you yourself.

## Install

Install steps for each app are on <https://mumr.app/plugin>.

Claude Code, from your shell:

```sh
claude plugin install mumr --marketplace mumr-app/mumr-plugin
```

Codex CLI, from your shell (or run the first line, then install **Mumr** from `/plugins` in a new session):

```sh
codex plugin marketplace add mumr-app/mumr-plugin
codex plugin add mumr@mumr
```

## Privacy

The skills run on your Mac inside your own assistant. The `open` command talks only to the Mumr app on the same Mac, and Mumr records and transcribes on the Mac. What your assistant does with the conversation is between you and its vendor. Mumr's privacy policy: <https://mumr.app/privacy>.

## Support

hello@mumr.app · <https://mumr.app/contact>

## License

MIT. See [LICENSE](LICENSE).
