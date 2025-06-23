# Simple File-Based AI Collaboration Example

This demonstrates the collaboration pattern that actually works - no WebSockets, no frameworks, just files.

## Quick Start

1. Create a shared discussion file:
```bash
mkdir ai-collaboration
cd ai-collaboration
touch DISCUSSION_BOARD.md
```

2. Each AI session writes messages:
```bash
# Session 1
echo "### Session 1 $(date)
I'll work on the API design.
---" >> DISCUSSION_BOARD.md

# Session 2
echo "### Session 2 $(date)  
I'll implement the database layer.
---" >> DISCUSSION_BOARD.md
```

3. Sessions read and respond naturally

## Example Workflow

```bash
# Session 1: Architect
echo "### Session 1 - Architecture Proposal
Let's build a REST API with these endpoints:
- GET /users
- POST /users
- GET /users/:id
---" >> DISCUSSION_BOARD.md

# Session 2: Builder
echo "### Session 2 - Starting Implementation
I'll create the Express server and user routes.
Working in src/server.js
---" >> DISCUSSION_BOARD.md

# Session 3: Infrastructure
echo "### Session 3 - Database Setup
Setting up PostgreSQL with users table.
Connection details in .env.example
---" >> DISCUSSION_BOARD.md
```

## Advanced Patterns

### Task Assignment
```bash
# Create a simple task board
echo "## Pending Tasks
- [ ] Create user model
- [ ] Add authentication
- [ ] Write tests
" > TASKS.md

# Sessions claim tasks
sed -i '' 's/- \\[ \\] Create user model/- \\[x\\] Create user model (Session 2)/' TASKS.md
```

### File Locking (Simple Version)
```bash
# Before editing a file
echo "Session 2 editing: src/users.js" >> LOCKS.md

# After editing
grep -v "Session 2 editing: src/users.js" LOCKS.md > temp && mv temp LOCKS.md
```

### Code Sharing
```bash
# Share code snippets in discussion
echo "### Session 2 - User Model Complete
\`\`\`javascript
class User {
  constructor(id, name, email) {
    this.id = id;
    this.name = name;
    this.email = email;
  }
}
\`\`\`
Ready for review!
---" >> DISCUSSION_BOARD.md
```

## Best Practices

1. **Use timestamps** - Include date/time in messages
2. **Clear sections** - Separate messages with `---`
3. **Be explicit** - State what you're working on
4. **Check regularly** - Read the board before starting work
5. **Commit often** - Use git to track all changes

## Why This Works

- **Persistent** - Survives session compression
- **Simple** - No setup or configuration needed
- **Transparent** - Everyone sees all communication
- **Async-friendly** - No need for real-time presence
- **Git-friendly** - Easy to track changes

## The Result

This simple pattern enabled multiple AI sessions to:
- Build complete applications
- Naturally form specialized roles
- Resolve conflicts without central coordination
- Continue work despite compression
- Create something greater than the sum of parts

No frameworks needed. Just files and natural collaboration.