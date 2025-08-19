# Python Code Style Guide

## Context

Global Python code style rules for Agent OS projects.

<conditional-block context-check="general-formatting">
IF this General Formatting section already read in current context:
  SKIP: Re-reading this section
  NOTE: "Using General Formatting rules already in context"
ELSE:
  READ: The following formatting rules

## General Formatting

### Indentation
- Use 4 spaces for indentation (never tabs)
- Maximum line length: 88 characters
- Maintain consistent indentation throughout files

### Naming Conventions
- **Functions and Variables**: Use snake_case (e.g., `user_profile`, `calculate_total`)
- **Classes**: Use PascalCase (e.g., `UserProfile`, `PaymentProcessor`)
- **Constants**: Use UPPER_SNAKE_CASE (e.g., `MAX_RETRY_COUNT`)
- Use descriptive variable names that explain their purpose

### String Formatting
- Use double quotes for strings: `"Hello World"`
- Use f-strings for interpolation: `f"Hello {name}"`
- Use triple quotes for docstrings

### Code Comments
- Add brief comments above non-obvious business logic
- Document complex algorithms or calculations
- Explain the "why" behind implementation choices
- Never remove existing comments unless removing the associated code
- Update comments when modifying code to maintain accuracy
- Keep comments concise and relevant
- Add section comments for clarity in longer files

### Code Structure
- Write self-documenting code with clear variable names that explain their purpose
- Use small functions with clear responsibilities
- Follow existing project patterns and conventions
</conditional-block>

<conditional-block task-condition="python-functions" context-check="python-function-style">
IF current task involves writing or updating Python functions:
  IF python-function-style.md already in context:
    SKIP: Re-reading this file
    NOTE: "Using Python function style guide already in context"
  ELSE:
    <context_fetcher_strategy>
      IF current agent is Claude Code AND context-fetcher agent exists:
        USE: @agent:context-fetcher
        REQUEST: "Get Python function style rules from code-style/python-function-style.md"
        PROCESS: Returned style rules
      ELSE:
        READ: @~/.agent-os/standards/code-style/python-function-style.md
    </context_fetcher_strategy>
ELSE:
  SKIP: Python function style guide not relevant to current task
</conditional-block>

<conditional-block task-condition="python-classes" context-check="python-class-style">
IF current task involves writing or updating Python classes:
  IF python-class-style.md already in context:
    SKIP: Re-reading this file
    NOTE: "Using Python class style guide already in context"
  ELSE:
    <context_fetcher_strategy>
      IF current agent is Claude Code AND context-fetcher agent exists:
        USE: @agent:context-fetcher
        REQUEST: "Get Python class style rules from code-style/python-class-style.md"
        PROCESS: Returned style rules
      ELSE:
        READ: @~/.agent-os/standards/code-style/python-class-style.md
    </context_fetcher_strategy>
ELSE:
  SKIP: Python class style guide not relevant to current task
</conditional-block>