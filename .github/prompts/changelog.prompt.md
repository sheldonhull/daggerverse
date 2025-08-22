---
mode: agent
description: 'Help use changelog actions via Dagger'
tools: ['changes', 'codebase', 'runInTerminal', 'search', 'terminalLastCommand', 'terminalSelection', 'usages']
---

## /dagger

A command for managing changelog entries with improved wording using changie format.

When this command is invoked:

1. Read the current changie configuration from `.changie.yaml` to understand the available kinds and format
1. Display the available change types from the configuration file, you should read the content of: `.changie.yaml` to get the kinds, and for the command construction use the `key` for kind the user says.
1. Prompt the user to select a change type from the available kinds
1. Ask the user to describe their change entry, provide an initial suggestion based on the changes being sent upstream, ie look at `changes`.
1. Take the user's input and improve it by:
   - Converting to active voice
   - Making it more succinct while preserving meaning.
   - Removing unnecessary words like "this change", "now", "currently"
   - Starting with action verbs when possible
1. Show the improved version to the user for confirmation
1. Generate the changie command for both shells:


```bash
changie new --kind="<selected-kind>" --body="<improved-description>"
```


```powershell
changie new --kind="<selected-kind>" --body="<improved-description>"
```

## Examples

Example transformations:
- "This change adds support for new authentication methods" → "Add support for new authentication methods"
- "Now users can configure timeout settings" → "Enable timeout configuration"
- "Fixed an issue where the API was returning incorrect status codes" → "Fix incorrect API status codes"
- "Updated dependencies to latest versions for security" → "Update dependencies for security fixes"

The goal is to create concise, actionable changelog entries that clearly communicate what changed without unnecessary verbosity.

IMPORTANT: This should not be the same as a git log.
The purpose of this entry is to communicate to developers.

## Things To Check

- If the changes seem to break a public contract, for instance changing the signature of a public function that would cause downstream consumers to have to make code changes, ask me for confirmation if I don't choose a kind of change entry that is a major change.
- If the change entry doesn't properly cover the types of changes, because more than one thing is impacted, suggest creating additional entries for those that in the same manner.
- Use emoji chat response to make things really useful and clear, but not too much, just to highlight certain things.

## Agent Workflow Guidance
- Always read the actual `.changie.yaml` file to get current configuration
- Use the exact label text from the kinds configuration
- Respect the semantic versioning levels (patch/minor/major) when suggesting changes
- Ensure the body format matches the configured `changeFormat: '- {{ .Body -}}'`
