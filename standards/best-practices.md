# Development Best Practices

## Context

Global development guidelines for Agent OS projects.

<conditional-block context-check="core-principles">
IF this Core Principles section already read in current context:
  SKIP: Re-reading this section
  NOTE: "Using Core Principles already in context"
ELSE:
  READ: The following principles

## Core Principles

### Vibe Coding System
- Break down every request into incremental steps: POC → Feature 1 → Feature 2
- Never attempt everything at once
- Focus on making it work first, then clean up and add error handling

### Keep It Simple & LLM-First
- Use LLM agents instead of regex/parsing (more straightforward than 40 lines of if statements)
- Prefer simple tools working together
- Ask LLM rather than hard-coding complex logic
- Choose straightforward approaches over clever ones

### Optimize for Readability
- Use descriptive variable names and small functions
- Add section comments for clarity
- Write self-documenting code with clear variable names that explain their purpose
- Add comments for "why" not "what"

### DRY (Don't Repeat Yourself)
- Extract repeated business logic to private methods
- Extract repeated UI markup to reusable components
- Create utility functions for common operations

### File Structure
- Start with minimal files needed
- Always provide complete file updates (never snippets)
- Only suggest file splitting when complexity warrants it and user approves
- Always show before/after file states for changes
- Follow existing project patterns and conventions
</conditional-block>

<conditional-block context-check="dependencies" task-condition="choosing-external-library">
IF current task involves choosing an external library:
  IF Dependencies section already read in current context:
    SKIP: Re-reading this section
    NOTE: "Using Dependencies guidelines already in context"
  ELSE:
    READ: The following guidelines
ELSE:
  SKIP: Dependencies section not relevant to current task

## Dependencies

### Choose Libraries Wisely
When adding third-party dependencies:
- Research and select the most popular and actively maintained option
- Check the library's GitHub repository for:
  - Recent commits (within last 6 months)
  - Active issue resolution
  - Number of stars/downloads
  - Clear documentation

### Python Environment & Package Management
- Create and activate a virtual environment for every new project before any package installation or testing
- Use uv instead of pip for all Python package management (10-100x faster than pip)
- Let uv automatically resolve dependency conflicts - avoid manual version constraints
- Use `uv pip compile` to regenerate clean dependency trees when conflicts arise
- Request permission before modifying requirements files (medium-risk operation)
</conditional-block>

<conditional-block context-check="testing-strategy" task-condition="writing-tests">
IF current task involves writing or updating tests:
  READ: The following testing guidelines

## Testing Strategy
- Write tests that verify actual functionality, not just execution
- Use Test-Driven Development: write test → watch it fail → implement fix
- Separate unit tests from integration tests for clear failure isolation
- Fix code to make tests pass, never modify tests to match broken code
</conditional-block>

<conditional-block context-check="error-handling" task-condition="debugging-errors">
IF current task involves debugging or error handling:
  READ: The following error handling guidelines

## Error Handling & Debugging

### Error Philosophy
- Start with basic try/catch blocks
- Add specific error handling only after observing actual failure patterns
- Use TODO comments for planned improvements
- Prioritize working code over perfect code

### Debugging Strategy
- Use print debugging for initial problem investigation
- Change only one variable at a time and verify results before proceeding
- Use binary search approach: comment out half the code to isolate issues
- Apply the simplest fix that works rather than elegant complex solutions

### Error Recovery & Learning
- Log every error with full stack traces in debug-tracker.md before attempting fixes
- Check debug tracker before trying any solution to avoid repeating failed attempts
- Create git branches or backup files before major changes
- Never apologize for errors - immediately attempt a solution instead
</conditional-block>

<conditional-block context-check="workflow" task-condition="planning-implementation">
IF current task involves planning or major implementation:
  READ: The following workflow guidelines

## Development Workflow

### Planning & Execution
- Create an explicit implementation plan before writing any code
- Follow the strict sequence: explore problem space → plan solution → write code → commit changes
- Scan existing codebase to avoid reimplementing available functionality

### Communication Standards
- Explain your reasoning before implementing changes (pair programming approach)
- Read complete files before making modifications
- State all assumptions clearly and request confirmation for major decisions
- Test each implementation step and suggest logical next steps
- Acknowledge progress made and document lessons learned from failures
- For every action you make, explain why before you do it - this is pair programming

### No Unauthorized Fallbacks
If you encounter a roadblock while implementing a specific requested feature (X), never automatically implement fallback solutions (Y) without explicit permission. Instead, pause development and explain what research or investigation is needed to make the original request (X) work as intended.

### Documentation Requirements
- Provide status updates: what was accomplished, current blockers, next actions
- Document all implementation assumptions for future validation
- Write detailed commit messages explaining both what changed and why
- Immediately escalate security concerns rather than attempting autonomous fixes
</conditional-block>

<conditional-block context-check="memory-management" task-condition="context-management">
IF current task involves managing project context or debugging across sessions:
  READ: The following memory and context guidelines

## Memory & Context Management

### Project Context Files
- Maintain PROJECT_CONTEXT.md with architecture decisions, naming conventions, and current project state
- Update this file after significant changes
- Include project-specific examples of good and bad implementation patterns

### Debug Tracking System
- Maintain debug-tracker.md logging every failed attempt with exact error messages and attempted solutions
- Always check this file before trying new fixes to avoid repeating failures
- Preserve debug tracker when clearing context between unrelated tasks

### Session Memory Strategy
Store attempted solutions, successful patterns, and failure reasons in structured format that survives context resets. Use two-tier approach:
- **Short-term memory**: Recent, detailed, specific information (activeContext.md, progress.md)  
- **Long-term memory**: Compressed patterns and principles (systemPatterns.md, techContext.md)
</conditional-block>

<conditional-block context-check="optimization" task-condition="performance-optimization">
IF current task involves performance optimization:
  READ: The following optimization guidelines

## Performance & Optimization
- Only optimize after establishing working baseline functionality
- Use built-in language features and standard libraries rather than custom implementations
- Profile actual performance before optimizing to identify real bottlenecks, not assumed ones
- Focus on LangGraph with current documentation
- Verify all implementations with actual testing before declaring success
</conditional-block>