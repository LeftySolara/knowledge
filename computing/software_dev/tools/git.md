# Git

[Git](https://git-scm.com/) is a distributed version control system, mostly used for programming projects.

## Common/Useful Commands

Create a new repository:

```text
git init
```

Clone a repository:

```text
git clone <url>
```

Stage a change for the current commit:

```text
git add <file>
```

Stage all changes for the current commit:

```text
git add -A
```

Commit staged changes \(the `-m` flag is optional\):

```text
git commit -m <message>
```

Show changes that aren't yet staged:

```text
git diff
```

Unstage a file, but preserve its changes:

```text
git reset <file>
```

Undo all commits after the one specified, preserving changes locally.

```text
git reset <commit>
```

List all the files that have yet to be committed:

```text
git status
```

Undo all non-committed changes on staged files:

```text
git checkout .
```

Remove all non-committed fies:

```text
git clean -f
```

## General Tips

- Consider creating a global `.gitignore` if necessary
- Remember to squash commits in situations where it makes sense
- Use aliases for common `git` commands \(if using the cli\)
- Git hooks are your friend
- Create separate branches when working on new features or bugs
- Pull before you push
- Clean out stale \(local\) branches from time to time

## Commit Message Conventions

Over the years I've alternated between many different styles of commit messages. Like with coding style, I'll use what everyone else does for an existing project. For my own projects, I want something that's concise and to the point. Here is the style I'm using right now, based on various pieces of advice I've come across over time:

For most commits, the corresponding message has a one-line header, then an empty line followed by a body \(if necessary\). The entire message is width limited to 80 characters.

If there is an issue/ticket number associated with a commit, it goes in the header.

Some people like to add subject tags as prefixes to their messages. For example, when adding a new feature one might use the message

```text
Add: button for accepting input
```

Here is a list of prefixes I like to use:

- **Add**: Add something new \(e.g., a feature, test, dependency, etc.\)
- **Remove**: Remove something \(e.g., a feature, test, file, etc.\)
- **Fix**: Fix an issue \(e.g., a bug, typo, accident, misstatement\)
- **Bump**: Increase the version of something \(e.g., dependency\)
- **Make**: Change the build process or tooling
- **Start**: Begin doing something \(e.g., create a feature flag\)
- **Stop**: End doing something \(e.g., remove a feature flag\)
- **Refactor**: A code change that is just a refactoring
- **Reformat**: A change of formatting \(e.g., omit whitespace\)
- **Optimize**: A change in performance \(e.g., speed up code\)
- **Document**: A change in documentation \(e.g., help files, readme\)

## Links

- [GitLab Tips and Tricks](https://about.gitlab.com/blog/2016/12/08/git-tips-and-tricks/)
- [HN discussion on commit prefixes](https://news.ycombinator.com/item?id=21289827)
- [How to fast-forward one commit](https://stackoverflow.com/questions/45155486/git-fast-forward-one-commit)
- [Commands for deleting branches](https://gist.github.com/cmatskas/454e3369e6963a1c8c89)
- [How to revert a commit](https://gist.github.com/gunjanpatel/18f9e4d1eb609597c50c2118e416e6a6)
