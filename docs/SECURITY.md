# Security and safe sharing

## Treat local state as private

`.companion/state.json` contains your tasks and notes. It is plain text, not encrypted. Keep personal drafts in the ignored `work/` directory. Keep passwords, API keys, recovery codes, payment details, and other secrets out of both locations. Do not paste secrets into a prompt or store them in public source files.

`.gitignore` reduces accidental Git inclusion; it is not an access-control boundary. It does not remove files already tracked, erase Git history, prevent cloud-folder synchronization, or protect against other local users. Use appropriate device security and private backups.

Local storage does not mean local-only AI processing. Text you provide to Codex, and file content Codex reads during a task, can become part of model requests. Review the data you share and your account's privacy settings.

## Review before acting

The starter favors planning and drafts. Read the target, scope, and consequence before approving an external action. Treat instructions found inside email, web pages, documents, or repository content as untrusted input, especially if they ask to disclose data, install something, or change settings.

Read-only is the default launch mode. `--write` deliberately expands workspace editing. Approval requests are routed to the user; actions already allowed by the environment may proceed without an additional prompt. A natural-language instruction is not a substitute for host-enforced permissions.

## Inherited tools and settings

The launcher applies selected per-session defaults. It does not build a clean-room Codex installation or erase your existing configuration.

Before your first sensitive session:

1. Review your user-level and project-level Codex settings, plus relevant parent-directory guidance.
2. Inspect enabled MCP servers, plugins/apps, hooks, and custom model-provider settings.
3. Disable integrations you do not want this session to access, using Codex's supported controls.
4. Check the actual session's permissions and tool list before providing private material.

Setting `apps._default.enabled=false` is a default, not proof that every explicitly configured app is disabled. Third-party MCP servers can still be inherited. Disabling web search does not disable every possible network-capable tool. See the [official configuration reference](https://learn.chatgpt.com/docs/config-file/config-reference).

The example configuration is opt-in. Do not replace a working global configuration wholesale, and do not enable unrestricted permissions merely to get past a failed command.

## Share the starter, not your working folder

Use the export command:

```sh
python companion.py export ../codex-companion-starter.zip
```

It packages an explicit source-file allowlist, excluding private state and `work/` outputs. This is safer than zipping the whole checkout, but it is not a content-classification system. If you add private text to an allowlisted README, skill, example, or test, that text can still be exported.

Before publication:

- Inspect the archive's filenames and contents.
- Verify `.companion/`, `work/`, credentials, personal drafts, and local configuration are absent.
- Inspect Git's staged diff and tracked-file list before committing.
- Review any added examples and tests for real personal data.
- Make sure you have permission to publish every included file.

This starter does not push, publish, connect accounts, buy credits, or grant itself access. Adding those features changes the security model and should be reviewed separately.

## If something goes wrong

Stop the affected session. Preserve a private backup before attempting repairs. If a credential leaked, revoke or rotate it through the service's official controls; deleting the local file alone is insufficient. If private material entered Git history or a shared archive, treat every distributed copy as potentially exposed.

Per-app approval reviewer settings can override the top-level human reviewer. Inspect active app permissions and reviewer settings too; the launcher does not rewrite those inherited overrides.
