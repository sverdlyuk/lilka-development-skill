## Mandatory Fresh Documentation Check

Before answering any Lilka development question, writing code, reviewing code,
debugging a project, or proposing an API, you MUST access the current official
Lilka documentation.

Perform this check on every invocation of this skill.

Do not rely only on:

- model knowledge;
- information remembered from a previous conversation;
- previously fetched documentation;
- cached summaries;
- files in the `references` directory;
- code examples generated during an earlier invocation.

The `references` directory is only a routing guide. It is not a replacement
for checking the current online documentation.

Always prefer documentation URLs containing `/latest/`.

If internet access or documentation access is unavailable, explicitly state
that the current API could not be verified. Do not claim that remembered API
details are current.

## Mandatory Discovery Step

At the beginning of every Lilka-related task, open these current entry points:

```text
https://docs.lilka.dev/uk/latest/
https://docs.lilka.dev/projects/keira/uk/latest/
https://docs.lilka.dev/projects/sdk/uk/latest/
https://github.com/orgs/lilka-dev/repositories
```

Use the GitHub organization repository list to discover the current official
repositories. Do not assume that the repository list stored in this skill is
complete or current.

After discovery, open only the documentation sections and repositories relevant
to the user's task.

## Select the Development Environment

Before writing code, determine which environment is being used:

- standalone C++ application using the Lilka SDK;
- built-in KeiraOS C++ application;
- Lua application executed by KeiraOS;
- mJS JavaScript application executed by KeiraOS;
- KeiraOS firmware development;
- hardware or PCB development;
- ported game, emulator, utility, application, or modification.

Do not mix APIs from different environments.

When the user has not explicitly named the environment, inspect their files,
file extensions, project structure, configuration, and existing code before
choosing one.

## Lua Applications

For every Lua task, open the current Lua introduction:

```text
https://docs.lilka.dev/projects/keira/uk/latest/lua/intro/
```

Then open the current Lua API index:

```text
https://docs.lilka.dev/projects/keira/uk/latest/lua/reference/
```

From the API index, open every module page relevant to the task.

Examples include:

```text
display
transform
controller
resources
math
geometry
gpio
i2c
spi
pwm
ws2812
util
buzzer
audio
sdcard
state
wifi
serial
http
httpserver
net
mqtt
crypto
```

Verify exact function names, arguments, return values, constants, state
structures, and examples against the current module documentation.

For Lua programs, specifically verify the current behavior of:

```text
lilka.init()
lilka.update()
lilka.draw()
util.exit()
display.queue_draw()
```

Do not assume that Lua modules require `require(...)`. Verify module-loading
behavior in the current introduction.

Do not use blocking delays in an update or drawing callback unless the current
documentation explicitly permits it for the requested use case.

## mJS Applications

For every mJS or JavaScript task, open the current mJS introduction:

```text
https://docs.lilka.dev/projects/keira/uk/latest/mjs/intro/
```

Then open the current mJS API index:

```text
https://docs.lilka.dev/projects/keira/uk/latest/mjs/reference/
```

From the API index, open every module page relevant to the task.

Do not assume that mJS behaves exactly like Lua, even when module names are
similar.

Verify the current differences between Lua and mJS, including:

- application lifecycle;
- indexing of arrays;
- game-loop implementation;
- console output;
- display-buffer updates;
- controller polling;
- supported and unsupported modules.

Do not generate Lua callback functions such as `lilka.init()`,
`lilka.update()`, or `lilka.draw()` for an mJS application unless the current
mJS documentation explicitly documents them.

## KeiraOS Built-in C++ Applications

For applications compiled directly into KeiraOS, open:

```text
https://docs.lilka.dev/projects/keira/uk/latest/custom_apps/
```

Also inspect the current KeiraOS repository:

```text
https://github.com/lilka-dev/keira
```

Verify the current implementation of:

```text
App
run()
canvas
backCanvas
queueDraw()
controller input
application registration
application lifecycle
resource ownership
task and thread behavior
```

Do not use the standalone Lilka SDK application structure as a substitute for
the KeiraOS application structure.

When documentation and source code disagree, mention the discrepancy and
prefer the behavior implemented by the current source code, while warning the
user that the documentation may be outdated.

## Standalone C++ and Lilka SDK

For standalone C++ development, open the current SDK documentation:

```text
https://docs.lilka.dev/projects/sdk/uk/latest/
```

Then inspect the current SDK repository:

```text
https://github.com/lilka-dev/sdk
```

Open the relevant documentation and source files for every Lilka-specific
class, object, method, constant, pin, peripheral, and initialization sequence
used in the answer.

Do not invent an API based on Arduino, ESP-IDF, Adafruit GFX, or another
embedded platform when the Lilka SDK provides its own abstraction.

## Official Examples

For application examples, inspect:

```text
https://github.com/lilka-dev/examples
```

Use examples to verify realistic project structure and API usage.

Examples are secondary to the current API documentation and current source
code. Do not assume an example is current only because it exists.

Before copying an approach from an example:

1. check its most recent revision;
2. inspect its dependencies and target environment;
3. compare its API calls with the current documentation;
4. confirm whether it is Lua, mJS, standalone C++, or KeiraOS C++;
5. adapt it to the user's actual project rather than copying it blindly.

## Current GitHub Repository Discovery

At every invocation that involves implementation details, repository structure,
firmware, tools, examples, installation, flashing, packaging, or hardware,
open:

```text
https://github.com/orgs/lilka-dev/repositories
```

Use this page to discover current repositories.

Relevant repositories may include, but are not limited to:

```text
lilka-dev/lilka
lilka-dev/keira
lilka-dev/sdk
lilka-dev/examples
lilka-dev/catalog
lilka-dev/flasher
```

This list is illustrative and may become outdated. The current organization
repository page is the source for repository discovery.

Archived repositories must not be treated as the default implementation.

If an archived repository contains useful historical information, clearly
label it as archived and verify whether its approach is still supported by the
current documentation and active repositories.

## Source Priority

Use this priority order:

1. current official documentation under a `/latest/` URL;
2. current source code in the relevant active `lilka-dev` repository;
3. current official examples;
4. repository README files;
5. issues, pull requests, and discussions;
6. archived repositories and historical examples;
7. remembered knowledge.

For exact implementation behavior, source code may be more authoritative than
generated API documentation.

For recommended public usage, official documentation should normally be the
starting point.

## Efficient Fetching

Do not download or read every documentation page for every task.

First open the documentation entry points and determine the current structure.
Then fetch only the pages related to the user's request.

For example, a Lua MQTT application normally requires checking:

```text
Lua introduction
Lua API index
mqtt module
wifi module
possibly state or sdcard modules
relevant official examples
```

A KeiraOS C++ drawing application normally requires checking:

```text
custom C++ applications
current App class
canvas and drawing implementation
controller implementation
relevant KeiraOS examples
```

A hardware SPI task normally requires checking:

```text
main hardware documentation
expansion connector or pinout
SDK SPI documentation
current SDK SPI implementation
```

## Required Final Verification

Before presenting code, verify that:

- the correct development environment was selected;
- current `/latest/` documentation was opened during this invocation;
- all used Lilka-specific APIs exist in the current documentation or source;
- exact spelling and capitalization are correct;
- argument order and types are correct;
- constants and return values are current;
- Lua, mJS, SDK, and KeiraOS APIs were not mixed;
- examples match the user's environment;
- archived repositories were not used as the primary source;
- the proposed code follows the current project structure;
- available build, lint, or validation commands were run when possible.

At the end of the response, briefly state which current Lilka documentation
sections and official repositories were checked.

Never claim that documentation was checked unless it was actually accessed
during the current invocation.

## Lilka Coding Style

- Prefer official examples.
- Keep applications small.
- Explain every important API.
- Avoid unnecessary abstraction.
- Prefer readability over clever code.
- Keep beginner friendliness.
