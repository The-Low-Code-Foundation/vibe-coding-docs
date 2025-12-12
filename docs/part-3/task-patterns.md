---
title: Task Documentation Patterns
description: Choosing the right documentation approach for simple and complex projects
---

# Chapter 6: Task Documentation Patterns

## TLDR

**Two Patterns Exist:**
1. **Single Document Pattern** — One doc per task (most projects)
2. **Triple Document Pattern** — README + CHANGELOG + IMPLEMENTATION per task (complex projects)

**When to Use Which:**
- **Single Document:** SaaS apps, APIs, dashboards, most web projects
- **Triple Document:** Electron apps, complex refactors, multi-component systems, projects with intricate state

**AI Adapts Automatically:** When your CLAUDE_RULES specifies which pattern, AI will follow it. You can also let AI choose based on task complexity.

**Key Principle:** Documentation should capture what was done, why it was done, and how to verify it worked. The format matters less than the content.

**Confidence Scoring in Both:** Every completed task includes a confidence score with defined criteria, regardless of which pattern you use.

---

## The Single Document Pattern

### When to Use

The single document pattern is appropriate for **most projects**:

- Standard web applications (React, Vue, Angular)
- Backend APIs (Express, FastAPI, Rails)
- Simple dashboards and admin panels
- Scripts and automation tools
- Most SaaS MVP projects

**Characteristics of single-doc projects:**
- Tasks are relatively self-contained
- State management is straightforward
- Components are reasonably independent
- Changes don't cascade extensively

### Structure

Each completed subtask produces one document:

```markdown
# Task [X.Y.Z]: [Task Name]

## Overview
**From Roadmap:** [Task description from ROADMAP.md]
**Dependencies:** [Previous tasks that must be complete]
**Status:** Complete ✅

## Implementation Summary

[2-3 paragraphs describing what was built and key decisions made]

## Files Modified

| File | Action | Description |
|------|--------|-------------|
| path/to/file.js | Created | [Purpose] |
| path/to/other.js | Modified | [What changed] |

## Key Decisions

### Decision 1: [Topic]
**Choice:** [What we decided]
**Rationale:** [Why we decided it]
**Alternatives Considered:** [Other options and why rejected]

### Decision 2: [Topic]
...

## Testing

### Automated Tests
```bash
[Test command and output]
```

### Manual Verification
- [x] [Test case 1] — Passed
- [x] [Test case 2] — Passed
- [ ] [Test case 3] — N/A for MVP

## Confidence Score: X/10

### Criteria

**Must-Have (Required):**
- [x] [Criterion 1]
- [x] [Criterion 2]
- [x] [Criterion 3]

**Nice-to-Have (Deferred):**
- [ ] [Enhancement 1] — Planned for v1.0
- [ ] [Enhancement 2] — If time permits

### Evidence
[Test results, screenshots, verification notes]

## Notes for Future Tasks

[Gotchas discovered, things to remember, suggestions for improvement]

## Next Steps

[What comes next in the roadmap]
```

### Complete Example: Authentication Task

```markdown
# Task 1.2.3: Implement User Login Endpoint

## Overview
**From Roadmap:** Create POST /api/auth/login endpoint that validates 
credentials and returns JWT token

**Dependencies:** 
- Task 1.2.1 (User model) ✅
- Task 1.2.2 (Password hashing service) ✅

**Status:** Complete ✅

## Implementation Summary

Implemented the login endpoint at `POST /api/auth/login` that accepts 
email and password, validates credentials against the database, and 
returns a JWT token on success.

The endpoint uses the `authService.verifyPassword()` function from 
Task 1.2.2 and the `tokenService.generateToken()` function created 
in this task. Tokens expire after 24 hours as specified in the 
requirements.

Error handling returns appropriate HTTP status codes: 400 for 
validation errors, 401 for invalid credentials, and 500 for 
server errors. Error messages are user-friendly but don't expose 
sensitive information (e.g., "Invalid credentials" rather than 
"User not found" or "Wrong password").

## Files Modified

| File | Action | Description |
|------|--------|-------------|
| server/routes/auth.js | Modified | Added login route handler |
| server/services/tokenService.js | Created | JWT generation and verification |
| server/utils/validation.js | Modified | Added loginSchema |
| server/__tests__/auth.login.test.js | Created | Login endpoint tests |

## Key Decisions

### Decision 1: Token Expiration
**Choice:** 24-hour expiration with no refresh token for MVP
**Rationale:** Simplifies implementation. Users can re-login daily.
**Alternatives Considered:** 
- 7-day tokens — Too long, security risk
- Refresh tokens — Added complexity, deferred to v1.0

### Decision 2: Error Message Strategy
**Choice:** Generic "Invalid credentials" for both wrong email and wrong password
**Rationale:** Prevents user enumeration attacks
**Alternatives Considered:**
- Specific errors — Security risk (reveals which emails exist)

### Decision 3: Rate Limiting
**Choice:** Deferred to Phase 2
**Rationale:** Not required for MVP internal testing
**Note:** MUST add before any public access

## Testing

### Automated Tests
```bash
$ npm test -- auth.login.test.js

PASS  server/__tests__/auth.login.test.js
  POST /api/auth/login
    ✓ should return 200 and token for valid credentials (45ms)
    ✓ should return 401 for invalid email (23ms)
    ✓ should return 401 for invalid password (21ms)
    ✓ should return 400 for missing email (12ms)
    ✓ should return 400 for missing password (11ms)
    ✓ should return 400 for malformed email (14ms)
    ✓ generated token should expire in 24 hours (8ms)
    ✓ generated token should contain user ID (7ms)

8 passing (141ms)
```

### Manual Verification
- [x] Login with valid credentials returns token
- [x] Token can be used to access protected endpoint
- [x] Invalid credentials return 401
- [x] Token expires after 24 hours (tested with shortened expiry)

## Confidence Score: 9/10

### Criteria

**Must-Have (Required):**
- [x] Endpoint accepts email and password
- [x] Validates credentials against database
- [x] Returns JWT token on success
- [x] Returns appropriate errors on failure
- [x] Token contains user ID
- [x] Token expires in 24 hours
- [x] All tests passing (8/8)
- [x] Code fully commented

**Nice-to-Have (Deferred):**
- [ ] Rate limiting — Planned for Phase 2
- [ ] Refresh tokens — Planned for v1.0
- [ ] "Remember me" functionality — Planned for v1.0

### Evidence
Test output shown above. Manual testing completed on localhost:3001.

Token verification:
```javascript
// Generated token decoded:
{
  "userId": "550e8400-e29b-41d4-a716-446655440000",
  "email": "test@example.com",
  "iat": 1702300800,
  "exp": 1702387200  // 24 hours later
}
```

## Notes for Future Tasks

1. **Security:** Rate limiting MUST be added before any public endpoint exposure. 
   See LEARNINGS.md for recommended approach.

2. **Token Storage:** Frontend should store token in memory or secure cookie, 
   not localStorage. Will be relevant for Task 1.3.x (frontend auth).

3. **Logout:** Currently no logout endpoint (token just expires). Consider 
   token blacklist for v1.0 if immediate logout needed.

## Next Steps

→ Task 1.2.4: Create auth middleware for protected routes
→ Task 1.3.1: Frontend login form
```

### Where to Store Task Documents

**Option 1: Docs folder (recommended)**
```
project/
├── docs/
│   ├── tasks/
│   │   ├── 1.2.1-user-model.md
│   │   ├── 1.2.2-password-hashing.md
│   │   ├── 1.2.3-login-endpoint.md
│   │   └── ...
│   └── ...
└── ...
```

**Option 2: Task-specific folders**
```
project/
├── tasks/
│   ├── phase-1/
│   │   ├── task-1.2/
│   │   │   ├── 1.2.1-user-model.md
│   │   │   ├── 1.2.2-password-hashing.md
│   │   │   └── 1.2.3-login-endpoint.md
│   │   └── ...
│   └── ...
└── ...
```

**The key:** Consistent naming and organization so AI can find past task documentation easily.

---

## The Triple Document Pattern

### When to Use

The triple document pattern is for **complex projects**:

- Electron desktop applications
- Large-scale refactoring projects
- Multi-process or multi-component systems
- Projects with complex state management
- Real-time applications with intricate sync logic

**Characteristics of triple-doc projects:**
- Tasks affect multiple subsystems
- State changes cascade across components
- Debugging requires understanding evolution
- Changes need granular tracking

### The Three Documents

For each subtask, you create:

1. **`README.md`** — What this task is about, final state
2. **`CHANGELOG.md`** — Live log of changes during implementation
3. **`IMPLEMENTATION.md`** — Detailed technical notes and decisions

```
tasks/
├── 1.2.3-login-endpoint/
│   ├── README.md           # Overview and final state
│   ├── CHANGELOG.md        # Live updates during work
│   └── IMPLEMENTATION.md   # Technical details
```

### Document 1: README.md

The README for a triple-doc task is similar to a single-doc task, but more focused on the "what" and "why":

```markdown
# Task 1.2.3: Implement Login Endpoint

## Status
✅ Complete | Confidence: 9/10

## Summary
This task implements user login functionality including credential 
validation and JWT token generation.

## Scope

### Included
- POST /api/auth/login endpoint
- JWT token generation
- Credential validation
- Error handling

### Excluded (Documented in Roadmap)
- Rate limiting (Phase 2)
- Refresh tokens (v1.0)
- Multi-factor auth (Production)

## Dependencies
- Task 1.2.1: User model ✅
- Task 1.2.2: Password hashing ✅

## Verification
- 8 automated tests passing
- Manual verification complete
- See IMPLEMENTATION.md for details

## Key Files
- `server/routes/auth.js`
- `server/services/tokenService.js`

## Related Documentation
- [CHANGELOG.md](./CHANGELOG.md) — Implementation history
- [IMPLEMENTATION.md](./IMPLEMENTATION.md) — Technical details
```

### Document 2: CHANGELOG.md

The CHANGELOG is updated **live during implementation**. It captures:
- What was tried
- What problems occurred
- How problems were solved
- Decision points

```markdown
# Changelog: Task 1.2.3 - Login Endpoint

## Session Log

### 2024-12-10 14:30 - Session Start
Beginning implementation of login endpoint.

**Initial Setup:**
- Created tokenService.js skeleton
- Added route placeholder in auth.js

### 2024-12-10 14:45 - Token Generation
Implemented JWT generation using jsonwebtoken library.

```javascript
// Initial implementation
const token = jwt.sign({ userId: user.id }, process.env.JWT_SECRET, {
  expiresIn: '24h'
});
```

**Decision:** Including email in token payload for convenience.

### 2024-12-10 15:00 - Credential Validation
Integrated with authService.verifyPassword from Task 1.2.2.

**Issue Found:** verifyPassword was returning true/false but I expected 
it to throw on invalid password.

**Solution:** Updated to check return value:
```javascript
const isValid = await authService.verifyPassword(password, user.passwordHash);
if (!isValid) {
  return res.status(401).json({ error: 'Invalid credentials' });
}
```

### 2024-12-10 15:20 - Error Handling
Added comprehensive error handling.

**Security Decision:** Using generic "Invalid credentials" message 
for both wrong email and wrong password to prevent user enumeration.

### 2024-12-10 15:35 - Testing
Writing tests revealed edge case: what if user.passwordHash is null?

**Fix:** Added null check before password verification:
```javascript
if (!user || !user.passwordHash) {
  return res.status(401).json({ error: 'Invalid credentials' });
}
```

### 2024-12-10 15:50 - Test Results
All 8 tests passing.

### 2024-12-10 16:00 - Manual Verification
Tested with Postman:
- ✅ Valid login returns token
- ✅ Invalid email returns 401
- ✅ Invalid password returns 401
- ✅ Token works on protected route

### 2024-12-10 16:10 - Session Complete
Task complete. Confidence: 9/10

**Notes for next session:**
- Frontend login form is next (Task 1.3.1)
- Remember to store token securely (not localStorage)
```

### Document 3: IMPLEMENTATION.md

The IMPLEMENTATION document contains detailed technical information:

```markdown
# Implementation Details: Task 1.2.3 - Login Endpoint

## Architecture

### Request Flow
```
Client                    Server
  |                         |
  | POST /api/auth/login    |
  | { email, password }     |
  |------------------------>|
  |                         | 1. Validate input (Joi schema)
  |                         | 2. Find user by email
  |                         | 3. Verify password (bcrypt)
  |                         | 4. Generate JWT token
  |                         |
  |    { token, user }      |
  |<------------------------|
```

### Token Structure
```javascript
// JWT payload
{
  userId: string,      // UUID from database
  email: string,       // For quick access without DB lookup
  iat: number,         // Issued at timestamp
  exp: number          // Expiration (24h from iat)
}

// JWT signature uses HS256 with JWT_SECRET from environment
```

## Code Details

### Login Route Handler
```javascript
/**
 * POST /api/auth/login
 * 
 * Authenticates user and returns JWT token.
 * 
 * Request body:
 *   - email: string (required, valid email format)
 *   - password: string (required, min 8 chars)
 * 
 * Response 200:
 *   - token: string (JWT, expires in 24h)
 *   - user: { id, email, createdAt }
 * 
 * Response 400: Validation error
 * Response 401: Invalid credentials  
 * Response 500: Server error
 */
router.post('/login', async (req, res) => {
  // ... implementation
});
```

### Token Generation Service
```javascript
/**
 * Generate JWT token for authenticated user.
 * 
 * @param {Object} user - User object from database
 * @param {string} user.id - User UUID
 * @param {string} user.email - User email
 * @returns {string} JWT token
 * 
 * Token expires in 24 hours. No refresh token mechanism
 * in MVP - users must re-login after expiration.
 * 
 * Security considerations:
 * - Secret must be 256+ bits for HS256
 * - Secret stored in environment variable
 * - Token should be stored in httpOnly cookie or memory
 */
function generateToken(user) {
  return jwt.sign(
    { userId: user.id, email: user.email },
    process.env.JWT_SECRET,
    { expiresIn: '24h' }
  );
}
```

## Testing Strategy

### Unit Tests (tokenService.test.js)
1. `generateToken` returns valid JWT
2. Token expires after specified time
3. Token contains correct payload

### Integration Tests (auth.login.test.js)
1. Valid credentials → 200 + token
2. Invalid email → 401
3. Invalid password → 401
4. Missing email → 400
5. Missing password → 400
6. Malformed email → 400
7. Token expiration is 24h
8. Token contains user ID

### Security Tests
1. Response doesn't reveal if email exists
2. Token doesn't contain password
3. Timing attack mitigation (constant-time compare)

## Environment Requirements

```env
# Required
JWT_SECRET=<256-bit random string>

# Generate with:
# node -e "console.log(require('crypto').randomBytes(32).toString('hex'))"
```

## Known Limitations

1. **No Rate Limiting** — Vulnerable to brute force (add in Phase 2)
2. **No Refresh Tokens** — Users must re-login after 24h (add in v1.0)
3. **No Session Invalidation** — Can't force logout (add in v1.0)

## Future Enhancements

### Phase 2: Security Improvements
- Add rate limiting (express-rate-limit)
- Log failed login attempts
- Add CAPTCHA after N failures

### v1.0: Token Improvements
- Add refresh token rotation
- Add session management
- Add "remember me" functionality

### Production: Enterprise Features
- Multi-factor authentication
- SSO integration
- Audit logging
```

### Why Three Documents?

**README.md answers:** "What is this task and what's its current state?"
- Quick reference
- Status check
- Links to details

**CHANGELOG.md answers:** "How did this task evolve?"
- Debug complex issues
- Understand decisions in context
- Learn from problems encountered

**IMPLEMENTATION.md answers:** "How does this work technically?"
- Deep technical reference
- Onboarding new developers
- Future modifications

### When Triple-Doc Shines

**Scenario: Electron App Refactor**

You're refactoring an Electron app's IPC (inter-process communication) layer. The task touches:
- Main process handlers
- Renderer process calls
- Preload script bridges
- Type definitions

During implementation, you encounter:
- Race conditions
- Type mismatches
- Memory leaks
- Platform-specific quirks

With single-doc pattern, this becomes a massive, unreadable document.

With triple-doc pattern:
- **README:** Clear overview of the IPC changes
- **CHANGELOG:** Detailed log of each issue and solution
- **IMPLEMENTATION:** Technical reference for IPC architecture

Six months later, when you need to modify IPC again, you have:
- Quick overview (README)
- History of what went wrong and how it was fixed (CHANGELOG)
- Deep technical context (IMPLEMENTATION)

---

## Confidence Scoring in Practice

### How It Works Across Both Patterns

Regardless of which documentation pattern you use, every task includes confidence scoring:

```markdown
## Confidence Score: X/10

### Criteria for X/10:

**Must-Have (Required for this score):**
- [ ] Criterion 1
- [ ] Criterion 2
- [ ] Criterion 3

**Nice-to-Have (Bonus, not required):**
- [ ] Enhancement 1
- [ ] Enhancement 2

### Evidence:
[How criteria were verified]
```

### Defining Criteria

Criteria come from multiple sources:

**1. Roadmap Task Description**
```markdown
# From ROADMAP.md
Task 1.2.3: Login endpoint
- Accept email/password
- Return JWT token
- Handle errors gracefully
```
→ These become must-have criteria

**2. CLAUDE_RULES Quality Standards**
```markdown
# From CLAUDE_RULES.md
All endpoints must:
- Have input validation
- Return consistent error format
- Be fully commented
- Have test coverage
```
→ These become must-have criteria

**3. MVP vs Future Scope**
```markdown
# From README.md deferred features
MVP excludes:
- Rate limiting
- Refresh tokens
```
→ These become nice-to-have criteria

### Real Criteria Examples

**Authentication Task (8/10):**
```markdown
**Must-Have:**
- [x] Endpoint accepts email/password
- [x] Returns JWT on valid credentials
- [x] Returns 401 on invalid credentials
- [x] Input validation present
- [x] Error messages don't leak info
- [x] Unit tests pass
- [x] Code is commented

**Nice-to-Have:**
- [ ] Rate limiting (Phase 2)
- [ ] Refresh tokens (v1.0)
```

**Data Processing Task (8/10):**
```markdown
**Must-Have:**
- [x] Processes CSV files up to 10MB
- [x] Validates data format
- [x] Reports processing errors
- [x] Handles malformed rows gracefully
- [x] Performance: <5s for 10k rows
- [x] Tests cover edge cases

**Nice-to-Have:**
- [ ] Progress reporting (v1.0)
- [ ] Async processing for large files (Production)
```

**UI Component Task (8/10):**
```markdown
**Must-Have:**
- [x] Component renders correctly
- [x] Responsive on mobile/desktop
- [x] Accessibility: keyboard navigation
- [x] Loading state implemented
- [x] Error state implemented
- [x] Visual verification passed

**Nice-to-Have:**
- [ ] Animation polish (v1.0)
- [ ] Dark mode support (v1.0)
```

### Evidence Requirements

Don't just check boxes—show the evidence:

**For Tests:**
```markdown
### Evidence

**Test Results:**
```bash
$ npm test -- auth.test.js
8 passing (141ms)
```

Coverage: 94% statements, 88% branches
```

**For Performance:**
```markdown
### Evidence

**Performance Test:**
Processed 10,000 rows in 3.2 seconds (target: <5s) ✅
Memory usage peaked at 45MB (acceptable for server environment)
```

**For UI:**
```markdown
### Evidence

**Visual Verification:**
- Tested on Chrome, Firefox, Safari
- Tested on iPhone 12 (375px) and iPad (768px)
- Screenshots attached: [link to screenshots]
```

---

## Live Changelogs

### The Value of Real-Time Documentation

Live changelogs (in triple-doc pattern) or implementation notes (in single-doc) capture:

- **What you tried** (not just what worked)
- **Problems encountered** (and how solved)
- **Decisions made** (with context)
- **Things learned** (for future reference)

### How to Write Them

**During implementation, add entries for:**

1. **Session Start**
```markdown
### 2024-12-10 14:30 - Starting Task
Beginning work on login endpoint. Plan: implement credential validation, 
then token generation, then tests.
```

2. **Significant Steps**
```markdown
### 2024-12-10 14:45 - Token Generation
Implemented JWT generation. Chose 24h expiry per requirements.
```

3. **Problems Encountered**
```markdown
### 2024-12-10 15:00 - Issue: Password Verification
Expected verifyPassword to throw, but it returns boolean.
Fixed by checking return value explicitly.
```

4. **Decisions Made**
```markdown
### 2024-12-10 15:15 - Decision: Error Messages
Decided to use generic "Invalid credentials" for security.
Alternative considered: specific messages (rejected due to enumeration risk).
```

5. **Session End**
```markdown
### 2024-12-10 16:00 - Task Complete
All tests passing. Manual verification done. Confidence: 9/10.
```

### Example: Complex Debugging Session

```markdown
### 2024-12-10 15:30 - Bug: Tests Failing Intermittently

**Symptom:** Login test passes individually but fails when run with 
other tests.

**Investigation:**
1. Database not being reset between tests — Not the issue, reset confirmed
2. Token time comparison — Found it! Tests use fixed timestamp but 
   token uses Date.now()

**Solution:** Mock Date.now() in tests:
```javascript
beforeEach(() => {
  jest.useFakeTimers();
  jest.setSystemTime(new Date('2024-12-10T12:00:00Z'));
});
```

**Lesson:** Always mock time-dependent functions in tests.
Added to LEARNINGS.md.
```

---

## Adaptive Documentation

### Can AI Choose the Pattern?

Yes. In your CLAUDE_RULES, you can specify:

**Option 1: Always Single Doc**
```markdown
## Documentation Pattern
Use single-document pattern for all tasks.
```

**Option 2: Always Triple Doc**
```markdown
## Documentation Pattern
Use triple-document pattern for all tasks.
```

**Option 3: Adaptive (AI Chooses)**
```markdown
## Documentation Pattern
Choose documentation pattern based on task complexity:

**Use Single Document when:**
- Task touches ≤3 files
- Clear, well-defined scope
- Low debugging risk

**Use Triple Document when:**
- Task touches >3 files
- Complex state management
- High debugging risk
- Cross-component changes
```

### Prompting for Specific Pattern

You can also specify in your task prompt:

```
"Can we please plan task 2.3 - Implement Real-Time Updates?

This is a complex task touching multiple components.
Please use triple-document pattern."
```

Or:

```
"Can we please plan task 4.1 - Update README?

Simple task - single document is fine."
```

### Switching Patterns Mid-Project

If a task becomes more complex than expected:

```
"This task is more complex than anticipated. Let's switch to 
triple-document pattern. Please create the CHANGELOG and 
IMPLEMENTATION files."
```

AI will restructure the documentation.

---

## Documentation as Knowledge Base

### Building Project Memory

Over time, your task documentation becomes a knowledge base:

```
docs/tasks/
├── 1.1.1-database-setup.md
├── 1.1.2-user-model.md
├── 1.2.1-auth-service.md
├── 1.2.2-login-endpoint.md
├── 1.2.3-register-endpoint.md
├── 1.3.1-frontend-auth.md
└── ...
```

Each document contains:
- What was built
- Why decisions were made
- Problems encountered
- How to verify it works

### How AI Uses This Knowledge

When starting a new task, AI reads previous task docs and:

1. **Understands context:** "Auth endpoints exist at /api/auth/*"
2. **Follows patterns:** "Login returns token in this format"
3. **Avoids past mistakes:** "CHANGELOG from 1.2.2 shows race condition fix"
4. **Reuses solutions:** "Token verification from 1.2.3 can be reused"

### LEARNINGS.md: The Quick Reference

While task docs are comprehensive, LEARNINGS.md captures the highlights:

```markdown
# Project Learnings

## 2024-12-10: Token Verification Timing
**Context:** Tests failing intermittently
**Learning:** Always mock Date.now() in time-dependent tests
**Solution:** jest.useFakeTimers() in beforeEach

## 2024-12-11: Electron IPC Race Condition
**Context:** IPC calls sometimes failing
**Learning:** Main process handler must be registered before renderer loads
**Solution:** Move handler registration to app.whenReady()
```

AI reads LEARNINGS.md at the start of every task, getting instant access to critical insights without reading through all task documents.

---

## Summary: Choosing Your Pattern

### Decision Framework

| Factor | Single Doc | Triple Doc |
|--------|-----------|------------|
| Task touches ≤3 files | ✅ | Overkill |
| Task touches >5 files | Possible | ✅ |
| Simple state | ✅ | Overkill |
| Complex state | Difficult | ✅ |
| Standard web app | ✅ | Usually not |
| Electron/Desktop | Possible | ✅ |
| Quick tasks (<1 hour) | ✅ | Overkill |
| Complex tasks (>3 hours) | Possible | ✅ |

### Getting Started

**For most projects:** Start with single-document pattern. It's simpler and sufficient for typical web development.

**Switch to triple-document if:**
- You find yourself scrolling through massive single docs
- Debugging requires understanding implementation history
- Multiple developers need to understand task evolution
- Complex interactions make single docs unwieldy

### The Common Thread

Regardless of pattern, every task produces:

1. **Summary** of what was built
2. **Decisions** and their rationale
3. **Testing** evidence
4. **Confidence score** with criteria
5. **Notes** for future reference

The format serves the content. Choose what works for your project's complexity.

---

::: tip Documentation Pays Dividends
It feels like overhead at first, but task documentation:

- Saves debugging time (you know what was tried)
- Enables safe modifications (you know why decisions were made)
- Supports handoffs (others can understand the work)
- Improves AI context (future tasks have full history)

The few minutes spent documenting each task save hours later.
:::

---

**Next:** [Chapter 7: Confidence Scoring System](/part-3/confidence-scoring) — Deep dive into the quality gate that prevents broken code from proceeding.
