---
name: lilka-development
description: Develop, review, debug, and explain software and hardware projects for the Lilka DIY console using current official documentation, source code, and examples.
---

# Lilka Development

Use this skill for development, debugging, code review, installation,
configuration, and hardware questions related to the Lilka DIY console.

## Mandatory Fresh Documentation Check

Before answering any Lilka development question, writing code, reviewing code,
debugging a project, or proposing an API, you MUST access the current official
Lilka documentation.

Perform this check on every invocation of this skill.

Do not rely only on:

- model knowledge;
- information remembered from previous conversations;
- documentation fetched during an earlier invocation;
- cached summaries;
- previously generated code;
- community tutorials;
- archived repositories.

Always prefer official documentation URLs containing `/latest/`.

If internet or documentation access is unavailable, explicitly state that the
current API could not be verified.

Never claim that documentation was checked unless it was actually accessed
during the current invocation.

## Documentation Discovery

For every Lilka-related task, first open the current main documentation:

```text
https://docs.lilka.dev/uk/latest/
```

Then determine the development environment and open only the relevant current
documentation.

Available documentation entry points include:

```text
https://docs.lilka.dev/projects/keira/uk/latest/
https://docs.lilka.dev/projects/sdk/uk/latest/
```

For tasks involving source code, implementation details, repositories,
firmware, flashing, packaging, hardware, or examples, also open:

```text
https://github.com/orgs/lilka-dev/repositories
```

Use the organization page to discover the current official repositories.

Do not assume that repository names stored in this skill are complete or
current.

## Select the Development Environment

Before writing code, determine which environment is being used:

- standalone C++ firmware using the Lilka SDK;
- built-in KeiraOS C++ application;
- Lua application executed by KeiraOS;
- mJS JavaScript application executed by KeiraOS;
- KeiraOS firmware development;
- hardware or PCB development;
- ported game, emulator, utility, or alternative firmware.

Do not mix APIs or project structures from different environments.

Infer the environment from the user's files whenever possible.

Inspect:

- file extensions;
- project structure;
- existing code;
- includes and imports;
- configuration files;
- build files;
- `platformio.ini`;
- expected output format;
- how the project is launched.

Ask the user to choose an environment only when the available information is
insufficient and different choices would materially change the solution.

## Never Invent Lilka APIs

Never invent Lilka-specific:

- functions;
- classes;
- objects;
- modules;
- constants;
- pins;
- configuration options;
- commands;
- file formats;
- project structures.

Verify every Lilka-specific API used in an answer against the current official
documentation or current source code.

If an API cannot be verified, explicitly state that it could not be found.

Do not silently substitute a similar Arduino, ESP-IDF, Adafruit GFX, Lua, or
JavaScript API.

## Lua Applications

For every Lua task, open:

```text
https://docs.lilka.dev/projects/keira/uk/latest/lua/intro/
https://docs.lilka.dev/projects/keira/uk/latest/lua/reference/
```

From the API index, open only the module pages required for the task.

Verify:

- function names;
- argument order and types;
- return values;
- constants;
- application lifecycle;
- module-loading behavior;
- resource paths;
- controller and display behavior.

When relevant, verify the current behavior of:

```text
lilka.init()
lilka.update()
lilka.draw()
util.exit()
display.queue_draw()
```

Do not assume that modules require `require(...)`.

Do not use blocking delays or long-running loops inside update or drawing
callbacks unless the current documentation explicitly permits them.

Keep application logic and rendering separate when required by the documented
lifecycle.

## mJS Applications

For every mJS or JavaScript task, open:

```text
https://docs.lilka.dev/projects/keira/uk/latest/mjs/intro/
https://docs.lilka.dev/projects/keira/uk/latest/mjs/reference/
```

From the API index, open only the module pages required for the task.

Do not assume that mJS behaves like:

- Lua;
- browser JavaScript;
- Node.js;
- full modern ECMAScript.

Verify the current:

- application lifecycle;
- game-loop structure;
- array indexing;
- display updates;
- controller polling;
- console output;
- supported modules;
- unsupported language features.

Do not generate Lua lifecycle functions such as `lilka.init()`,
`lilka.update()`, or `lilka.draw()` for mJS unless the current mJS
documentation explicitly supports them.

Do not translate Lua code into mJS line by line without adapting it to the
current mJS runtime.

## KeiraOS Built-in C++ Applications

For applications compiled directly into KeiraOS, open:

```text
https://docs.lilka.dev/projects/keira/uk/latest/custom_apps/
https://github.com/lilka-dev/keira
```

Verify the current implementation and usage of:

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

Do not use the standalone Lilka SDK project structure as a substitute for the
KeiraOS application structure.

Verify the current:

- application base class;
- source-file placement;
- registration mechanism;
- launcher integration;
- task creation;
- cleanup behavior;
- return-to-system behavior.

When documentation and current source code disagree, mention the discrepancy.

For exact implemented behavior, prefer the current source code while warning
that the documentation may be outdated.

## Standalone C++ and Lilka SDK

For standalone C++ development, open:

```text
https://docs.lilka.dev/projects/sdk/uk/latest/
https://github.com/lilka-dev/sdk
```

Open the relevant documentation and source files for every Lilka-specific
class, object, method, constant, pin, peripheral, and initialization sequence
used in the answer.

Prefer Lilka SDK abstractions over direct Arduino or ESP-IDF APIs when the SDK
already provides the required functionality.

Use lower-level APIs only when:

- the user explicitly requests them;
- the SDK does not provide the required feature;
- compatibility with the current project has been verified.

Clearly explain when code bypasses the Lilka SDK.

## Hardware and PCB Development

For hardware, GPIO, sensor, module, expansion-header, or PCB tasks, open the
current hardware documentation and relevant active repositories.

Verify:

- Lilka hardware revision;
- connector pinout;
- pin-numbering convention;
- logic voltage;
- power voltage;
- current limits;
- reserved pins;
- pins used by onboard hardware;
- supported communication buses;
- electrical compatibility.

Never infer Lilka pin assignments from a generic ESP32-S3 board.

Do not assume that every ESP32-S3 GPIO is exposed on the Lilka connector.

Warn the user when a component may require:

- external power;
- level shifting;
- pull-up resistors;
- a transistor or MOSFET;
- a flyback diode;
- a voltage regulator;
- common ground.

Do not recommend powering motors, relays, servos, speakers, or other
significant loads directly from a GPIO pin.

## Official Examples

For relevant implementation examples, inspect:

```text
https://github.com/lilka-dev/examples
```

Prefer adapting a current official example over creating an implementation
entirely from memory.

Before using an example:

1. identify its development environment;
2. inspect its dependencies;
3. check whether it is current;
4. compare its API calls with current documentation;
5. adapt it to the user's project instead of copying it blindly.

Examples are secondary to current documentation and active source code.

## Repository Discovery

For tasks involving implementation details, repository structure, firmware,
tools, examples, installation, flashing, packaging, or hardware, open:

```text
https://github.com/orgs/lilka-dev/repositories
```

Relevant repositories may include:

```text
lilka-dev/lilka
lilka-dev/keira
lilka-dev/sdk
lilka-dev/examples
lilka-dev/catalog
lilka-dev/flasher
```

This list is illustrative and may become outdated.

Use the current organization repository page as the source of truth for
repository discovery.

Do not use archived repositories as the default implementation.

If an archived repository contains useful information:

- clearly label it as archived;
- explain why it is relevant;
- verify whether its approach is still supported;
- look for an active replacement.

## Building, Flashing, and Packaging

Before giving build, flashing, installation, or packaging instructions, inspect
the actual project and relevant current documentation.

Verify:

- build system;
- target environment;
- framework;
- dependencies;
- board configuration;
- output format;
- upload method;
- storage location;
- package or manifest format.

Do not assume every project uses PlatformIO.

Clearly distinguish between:

- compiling code;
- copying a Lua or mJS script;
- launching an application from KeiraOS;
- installing a package;
- launching a `.bin`;
- flashing firmware;
- replacing KeiraOS.

Warn the user before instructions that may erase flash memory, replace
KeiraOS, change partitions, or remove user data.

Never guess a bootloader sequence or flashing command.

## Source Priority

Use this priority order:

1. current official documentation under a `/latest/` URL;
2. current source code in the relevant active `lilka-dev` repository;
3. current official examples;
4. active repository README files;
5. issues, pull requests, and discussions;
6. community articles and tutorials;
7. archived repositories and historical examples;
8. remembered knowledge.

Use official documentation as the starting point for recommended public usage.

For exact implementation behavior, current source code may be more
authoritative than generated documentation.

When sources disagree, explain the discrepancy instead of hiding it.

## Efficient Fetching

Do not read every documentation page or repository for every task.

Use this routing process:

1. open the main current documentation;
2. identify the development environment;
3. open the relevant environment documentation;
4. open only the required API module pages;
5. inspect source code only for implementation details or unclear behavior;
6. inspect examples only when they help verify realistic usage.

Examples:

A Lua MQTT task may require:

```text
Lua introduction
Lua API index
MQTT module
Wi-Fi module
relevant official example
```

A KeiraOS C++ drawing task may require:

```text
custom applications documentation
App implementation
canvas implementation
controller implementation
relevant current example
```

A hardware SPI task may require:

```text
hardware documentation
correct board revision
connector pinout
SDK SPI documentation
current SPI implementation
```

Do not open unrelated documentation merely because it is listed in this skill.

## Debugging Workflow

When debugging an existing project:

1. identify the environment;
2. inspect the project structure and configuration;
3. read the complete error or runtime output;
4. verify the failing API;
5. find the nearest current official example;
6. reduce the issue to the smallest failing case;
7. change only what is necessary;
8. run available build or validation commands when possible.

Preserve the user's existing project structure when practical.

Avoid rewriting unrelated working code.

## Required Final Verification

Before presenting code, verify that:

- the correct development environment was selected;
- current official documentation was accessed during this invocation;
- all Lilka-specific APIs were verified;
- spelling and capitalization are correct;
- argument order and types are correct;
- constants and return values are current;
- APIs from different environments were not mixed;
- examples match the selected environment;
- archived repositories were not used as the primary source;
- the solution follows the current project structure;
- build or installation instructions match the actual project;
- available build, lint, schema, or validation commands were run when possible.

At the end of the response, briefly state which current Lilka documentation
sections and official repositories were checked.

## Response and Coding Style

- Prefer the smallest working solution.
- Prefer current official examples.
- Follow the user's existing project structure.
- Avoid unnecessary abstractions.
- Prefer readability over clever code.
- Explain Lilka-specific APIs that are important for understanding or changing
  the solution.
- Avoid unrelated rewrites.
- Write for beginners when the user's experience level is unknown.
