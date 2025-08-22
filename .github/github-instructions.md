# Daggerverse

This is a repo containing Dagger functions based on using Dagger, a tool for containerized workflows.

## Agent Instructions

- Prefer validating any implementation by reference example from the Dagger Cookbook for Go.
- `#context7` MCP server can be used and would reference library: `dagger/dagger`.

The filtering should include:

- `SOURCE: https://github.com/dagger/dagger/blob/main/docs/current_docs/` in the context, to filter to current library docs.
- Look up examples with path: `https://github.com/dagger/dagger/blob/main/docs/current_docs/cookbook/snippets` and filter to the Go examples unless implementing another language specifically.

- Ensure for any new initialozation, you run the `dagger` cli tool instead of trying to do this as a normal Go project, as it's a specific SDK and toolchain.
- For instance, adding or updating dependencies would be done with `dagger init`
- `#context7` MCP lookup for dagger cli commands could be done via: `SOURCE: https://github.com/dagger/dagger/blob/main/docs/reference/cli.mdx` and you'd want to validate the syntax against this.
  If this fails, fallback to just using `dagger <command> --help` to get more details on proper commands.

## Fallback Resources For Fetch

- [Intro to Dagger](https://docs.dagger.io/)
- [Dagger Cookbook Examples](https://docs.dagger.io/cookbook)
