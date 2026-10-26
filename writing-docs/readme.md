# The README

The README has two jobs. First, a visitor decides within a minute whether the project is for
them. Second, they get to a first result within five minutes. Everything else is a link to a
guide or a reference page. The order below follows standard-readme and GitHub's guidance on
READMEs, with Diátaxis' kinds of page (SKILL.md) deciding what moves out.

## Its order

1. **The name and one sentence**: what the project is, and who it is for.
2. **Why**: the problem it solves, in two or three sentences, and one screenshot or a short
   sample of the result.
3. **Requirements**: the operating systems, the runtime and package manager versions, and any
   service or account it needs.
4. **Install**: commands to copy and paste, tested from a clean clone (or a clean machine, for a
   published package).
5. **Quick start**: the shortest path to the first success, and what the reader sees then. For a
   library, the smallest program that uses it, with its output.
6. **What you can do**: four to seven tasks, each in one or two sentences with a link to its
   guide.
7. **Documentation**: links to the guides and the reference pages.
8. **Limits**: what it supports (languages, platforms, versions it is tested on), and what it
   does not do.
9. **Development**, for contributors (commands, the layout of the code, where the design docs
   are), and the **license**.

Name, sentence, picture and install fit the first screen. Reference tables (commands, options,
configuration keys, environment variables, keys, error codes) and how-tos longer than a few
steps belong on their own pages.

## Pages beside it

Propose this layout to the person and **ask before creating it**. Where user docs live is their
decision, and links from the code and from other sites depend on it.

- `docs/guide/`: one how-to guide a task, named by the task (`deploy-to-staging.md`).
- `docs/reference/`: commands and options, configuration, environment variables, APIs, file
  formats.
- An explanation page for each model the reader needs before acting: how it works, what it
  stores, what it sends.
- A page others link to stays where it is, or leaves a pointer behind. Look for links from the
  code, CI templates, package metadata (a `homepage` field) and published URLs (a schema's `$id`).

## The reader's questions (for the reader test)

Start from these, and replace them with the project's own, in its reader's words:

1. What does it do, and does it work for me (languages, platforms, versions)?
2. What do I need installed, and how do I install it?
3. How do I get a first result?
4. What does the output mean, and what should I do about it?
5. How do I do each of the two or three main tasks?
6. How do I configure it, and where is the configuration kept?
7. What files does it write in my project, and do I commit them?
8. What does it send over the network?
9. How do I run it in CI?
10. How do I turn off what I do not want?

## Rewriting it

```
- [ ] 1. Measure the current README (readability.mjs, --outline); keep the numbers
- [ ] 2. Inventory every fact it states (commands, flags, keys, variables, paths, behaviors):
         for each, kept in the README, moved to a page (which), or dropped (why). Nothing is
         lost without a reason
- [ ] 3. Check each fact kept or moved against the code (SKILL.md, "Check every fact")
- [ ] 4. Agree the layout of the pages with the person (above)
- [ ] 5. Write the README in its order, then the pages, each to SKILL.md's rules
- [ ] 6. Links: every relative link and anchor; the messages in the code that name a README
         section or a docs URL (grep -rn README src, and their tests); links from other docs
- [ ] 7. Screenshots retaken if the views they show changed
- [ ] 8. Measure again; reader test with the questions above, on the README and each page
- [ ] 9. Record it (the numbers before and after, the inventory's drops, the reader test's
         results, what was not verified)
```
