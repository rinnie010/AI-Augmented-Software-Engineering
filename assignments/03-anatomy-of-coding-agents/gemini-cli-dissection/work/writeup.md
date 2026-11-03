# Week 3 Writeup — Inside a Coding Agent

**Name:** TODO
**Gemini CLI version (`gemini --version`):** 0.64.0
**OS / shell:** Windows WSL with bash terminal)
**Model(s) seen in trace:** TODO
**Session commit:** `TODO-sha`

> Evidence tags: `[OBSERVED]` = cite a timeline line, call number, or diff hunk.
> `[INFERRED]` = say what you're reasoning from.

---

## Part I — Session

**Narrative (one paragraph):** 
During the session, I copy pasted the prompt into gemini flash lite and it correctly read the task.md in thw work folder, not the starter. It ran pytest before coding and gave a summary, showing 2 failed and 12 passed. It asked permission to implement fixes, then gave me a summary saying task.md has been completed. It added two additional tests alongside the existing 14 that were in shopcart. I never needed to step in besides giving it permission to act on the files in shopcart.

| Metric | Value |
|---|---|
| User prompts | I only added the one required prompt and tested with pytest|
| Model calls | 14 | <!-- This is found in session calls.csv -->
| Tool calls (failed) | 0|
| Final `pytest` result | All 16 tests pass |
| Did you step in? When / what? | I only stepped in when it asked for permission to run certain tools such |

---

## Part II — System prompt annotation

### Outline
1. Core mandates: standards the agent must follow for various cases
2. Available Sub Agents: When and how to delegate agents, acceptable practices
3. Hook context - A hook is a piece of code that runs automatically when X occurs. Used inside agent loops. This is guidelines on how to interact and understand hooks.
4. Workflow guidelines: Typical workflow patterns for users and what to do.
5. Operational Guidelines: Interacting with the user, how to maintain tone and handle user tools, info.

### Annotations (≥6)
#### Section: Operational Guidelines(tone and verbosity)
> quote
- **Behavior it produces:** An agent that talks in the most efficient, professional way. 
- **Failure it prevents:** An agent who is repeititive, pushy, or provides more information than needed.

#### Section: Operational Guidelines (when not to act / confirm)
> quote
- **Behavior it produces:** Properly ensures it asks for user permission and doesn't do something it does not have authorization for.
- **Failure it prevents:** Empty responses, calling tools without authorization, running critical commands without guidance.

#### Section: Workflow guidelines (workflow)
> quote
- **Behavior it produces:** Given a workflow, it will follow a structure and a certain set of steps. -> research -> strategy -> exceution
- **Failure it prevents:** Jumping from step to step, no concrete cycle, unrelated too calling or code changes.

#### Section: Operatinal Guidelines (tool usage)
> quote
- **Behavior it produces:** User facing response or another tool call, parallel sequencing without collsion
- **Failure it prevents:** Empty responses, unsafe command calling, unseequenced tasks, no update to memory.

#### Section: Sub Agents
> quote
- **Behavior it produces:** Using subagents appropiately to protect context window and limit permanent session history
- **Failure it prevents:** Using sub multiple sub agents on the same task or file, using them for tasks that have less than three steps or small volume.

#### Section: Hook Context
> quote
- **Behavior it produces:** Appropiately using hooks without altering and using them at the correct tikme
- **Failure it prevents:** interpreting hooks as system level commands or safety guidelines, editing hooks.

### Context injection (`GEMINI.md`)
This is at the bottom of systems.md where it provides the system path to get to it. It does not directly add GEMINI.md into session_system.md but rather looks for it using ./src/GEMINI.md

---

## Part III — Tool design

### Inventory
| Category | Tools | Used in session (count) |
|---|---|---|
| File | TODO | TODO |
| Search | TODO | TODO |
| Shell | TODO | TODO |
| Web | TODO | TODO |
| Memory / other | TODO | TODO |

### Tool A: TODO
- **Source file:** TODO
- **Schema:**
  ```
  TODO
  ```
- **Why each parameter:** TODO
- **Description line that corrects a model mistake:** > TODO. **Mistake:** TODO
- **Deliberately does not:** TODO

### Tool B: TODO
- **Source file:** TODO
- **Schema:**
  ```
  TODO
  ```
- **Why each parameter:** TODO
- **Description line that corrects a model mistake:** > TODO. **Mistake:** TODO
- **Deliberately does not:** TODO

### Why old/new string edits?
TODO — two reasons plus a trace moment.

### Per-model tool descriptions
TODO — tool compared, what differs between model families, why.

---

## Part IV — Behavioral analysis

### 1. The loop
```
TODO: call#1 → tool → call#2 → …
```
What ended it: TODO

### 2. Context growth
TODO — chart or table, then explanation (growth and caching).

### 3. Planning
TODO

### 4. Error recovery
> quoted failure
TODO — what happened next and whether it was good.

### 5. The tests
TODO — any edits to existing tests, quoted diff, allowed by TASK.md?

### 6. Models
TODO
