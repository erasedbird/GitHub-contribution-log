# Contribution 204: Add compatibility test for $bitOr (second pass)

**Contribution Number:** 1 
**Student:** Ruth L
**Issue:** [GitHub issue link](https://github.com/documentdb/functional-tests/issues/204)
**Status:** Phase 1 (In Progress)

---

## Why I Chose This Issue

One area I want to improve on is better understanding how to write good tests. I've oven written code to pass tests, but I'm not as good as writing thorough test cases. DocumentDB functional-tests seems like a pretty good place to start because they have a lot of structured tests and resources I can consult while working on writing my own, and logical operators are a good place to start since they're pretty simple.

---

## Understanding the Issue

### Problem Description

BitOr tests are missing.

### Expected Behavior

Should test BitOr, which performs a bitwise or update on a field. 

### Current Behavior

No bitor test exists.

### Affected Components

BitOr command cannot be tested.

---

## Reproduction Process

Branch: [My fork here](https://github.com/erasedbird/functional-tests)

### Environment Setup

Setup instructions from DocumentDB:

`pip install pymongo`
`pip install dnspython`

```
   # Remove any existing DocumentDB image
   docker image rm -f ghcr.io/documentdb/documentdb/documentdb-local:latest || echo "No existing documentdb image to remove"

   # Pull the latest DocumentDB Docker image
   docker pull ghcr.io/documentdb/documentdb/documentdb-local:latest

   # Tag the image for convenience
   docker tag ghcr.io/documentdb/documentdb/documentdb-local:latest documentdb

   # Run the container, setting a username and password
   docker run -dt -p 10260:10260 --name documentdb-container documentdb --username <YOUR_USERNAME> --password <YOUR_PASSWORD>
```

Save the name and password chosen.

Setup instructions for functional-tests: 
```
# Clone the repository
git clone https://github.com/documentdb/functional-tests.git
cd functional-tests

# Install dependencies
pip install -r requirements.txt
```

### Steps to Reproduce

Note: Key challenge was that to run pytest, I had to cd into documentdb-tests for it to work, which is not written in the repo.

1. `cd documentdb-tests`
2. `pytest --connection-string "mongodb://hello:there@localhost:10260/?authMechanism=SCRAM-SHA-256&tls=true&tlsAllowInvalidCertificates=true" --engine-name documentdb` Feel free to add -x to get it to stop after the first error, or -m [string] so it only runs a certain type of test.
3. Tests do not include BitOr.

### Reproduction Evidence

- **Commit showing reproduction:** Test log saved into results.log in this repo.

---

## Solution Approach

### Analysis

Missing BitOr tests.

### Proposed Solution

Write BitOr tests, with 5 normal cases and 2-3 edge case behaviors.

### Implementation Plan

Using UMPIRE framework (adapted):

**Understand:** There is not BitOr tests.

**Match:** Contributions.md links to example tests and test format guide.

**Plan:** 
1. Read over MongoDB BitOr documentation carefully to understand expected behavior + edge cases.
2. Read over example tests to understand how to contribute.
3. Add base tests and check if it works.
4. Add edge case tests.

**Implement:** [Link to your branch/commits as you work]

**Review:** [Self-review checklist - does it follow the project's contribution guidelines?]

**Evaluate:** [How will you verify it works?]

---

## Testing Strategy

### Unit Tests

- [ ] Test case 1: [Description]
- [ ] Test case 2: [Description]
- [ ] Test case 3: [Description]

### Integration Tests

- [ ] Integration scenario 1
- [ ] Integration scenario 2

### Manual Testing

[What you tested manually and results]

---

## Implementation Notes

### Week 4 Progress

Decide which tests to include, reach out to the Discord to learn about contribution requirements, read the Contributing.md files.

### Week 5 Progress

Wrote the first tests, began testing by comparing results to mongosh.

### Code Changes

- **Files modified:** Changed bitOr folder in bitwise operators folder.
- **Key commits:** [Links to important commits]
- **Approach decisions:** [Why you chose certain approaches]

---

## Pull Request

**PR Link:** [GitHub PR URL when submitted]

**PR Description:** [Draft or final PR description - much of the content above can be adapted]

**Maintainer Feedback:**
- [Date]: [Summary of feedback received]
- [Date]: [How you addressed it]

**Status:** [Awaiting review / Iterating / Approved / Merged]

---

## Learnings & Reflections

### Technical Skills Gained

[What you learned technically]

### Challenges Overcome

[What was hard and how you solved it]

### What I'd Do Differently Next Time

[Reflection on your process]

---

## Resources Used

- [Link to helpful documentation]
- [Tutorial or Stack Overflow post that helped]
- [GitHub issues or discussions that helped]
