# Contributing Guidelines

## Steps to Contribute

### Step 1: Fork Repository
**What:** Create a personal copy of the repository under your GitHub account.
**Why:** This allows you to work independently without affecting the main repository. You'll have full control over your fork.
**How:** Click the "Fork" button on the GitHub repository page. This creates an exact copy of the repository in your account.

### Step 2: Clone Fork
**What:** Download the forked repository to your local machine.
**Why:** You need a local working directory to make changes and test your work before submitting.
**How:** Run `git clone https://github.com/YOUR-USERNAME/repository-name.git` in your terminal, then navigate to the directory with `cd repository-name`.

### Step 3: Create Branch
**What:** Create a new branch for your specific contribution.
**Why:** Branches keep features isolated and organized. This allows multiple people to work on different features simultaneously without conflicts.
**How:** Run `git checkout -b branch-name` (use a descriptive name like `add-authentication-docs` or `fix-typo-readme`). The branch name should reflect the work you're doing.

### Step 4: Add Documentation
**What:** Write or edit documentation files following the project standards.
**Why:** Good documentation helps others understand and use the project effectively.
**How:** Create or modify `.md` files in the relevant directories. Ensure your content follows the Documentation Rules (see below). Test links and code examples locally if possible.

### Step 5: Commit Changes
**What:** Save your changes to your local git history with a descriptive message.
**Why:** Commits create a record of what changed and why. Good commit messages help reviewers understand your work.
**How:** Run `git add .` to stage changes, then `git commit -m "Your descriptive message"`. Use clear, present-tense messages like "Add authentication guide" or "Fix typo in README".

### Step 6: Push Branch
**What:** Upload your branch with all commits to your forked repository on GitHub.
**Why:** This makes your work available online for review before merging into the main project.
**How:** Run `git push origin branch-name`. Your branch will now appear on GitHub under your forked repository.

### Step 7: Create Pull Request
**What:** Open a request to merge your changes into the main repository.
**Why:** Pull requests enable code review, discussion, and quality checks before merging.
**How:** Go to the original repository on GitHub. You'll see a prompt to create a Pull Request from your branch. Fill in the title and description explaining your changes, then submit. Wait for maintainers to review and provide feedback.

---

# Documentation Rules

### Rule 1: Use Markdown
**What:** All documentation should be written in Markdown format (`.md` files).
**Why:** Markdown is easy to read, write, and render across different platforms. It's the standard for documentation in most projects.
**How:** Use proper Markdown syntax:
- `# Heading 1`, `## Heading 2`, `### Heading 3` for headings
- `**bold**` for emphasis
- `_italic_` for secondary emphasis
- Use code blocks with triple backticks: ` ``` ` for code examples
- Use `-` or `*` for bullet lists and `1.` for numbered lists

### Rule 2: Keep Language Simple
**What:** Write in clear, straightforward language that's easy to understand.
**Why:** Documentation should be accessible to developers of all skill levels. Overly complex language creates barriers to understanding.
**How:** 
- Use short sentences and paragraphs
- Avoid jargon or explain technical terms when first used
- Write in active voice (e.g., "You create a branch" instead of "A branch is created")
- Re-read for clarity and simplify where possible

### Rule 3: Add Real-World Examples
**What:** Include practical, working examples that readers can follow.
**Why:** Examples demonstrate concepts concretely and help users understand how to apply the information in their own work.
**How:** 
- Provide code snippets with context
- Include command-line examples with expected output
- Use realistic scenarios that match common use cases
- Ensure examples are tested and work as written

### Rule 4: Avoid Duplicate Content
**What:** Don't repeat information that's already documented elsewhere in the project.
**Why:** Duplicates create maintenance headaches. When one copy is updated and the other isn't, readers get conflicting information.
**How:** 
- Search existing documentation before writing
- Link to existing sections instead of rewriting
- If duplication exists, consolidate into one location with clear links
- Use includes or references to avoid repeating large blocks of information