---
name: writing-docs
description: "Writes and rewrites documentation that people understand on the first read: READMEs, tutorials, how-to guides, reference pages (commands, configuration, APIs), and the prose of design docs and plans a person reviews. Gives a standard from plain-language guidance, Diátaxis and Google's developer documentation style guide (one reader and one task a page, the point first, short active sentences, every term defined once), the order of a README, a script that counts long and crowded sentences, a reader test by a fresh agent that sees only the page, and checks of every command, flag, key and link against the code. Use when writing, rewriting or reviewing a README or any Markdown page for people, when a change adds user-visible behavior to document, when docs are called hard to read, dense, too long or stale, or when asked for clearer or human-readable text. Not for code comments, commit messages, UI strings, or agent instructions (CLAUDE.md, AGENTS.md, SKILL.md)."
---

# Writing docs people understand

A page works when a reader who was not in the conversation can do the task, or answer the
question, from the page alone, on the first read. Agents fail this test in a known way. They
write for themselves: compressed, in the words of the code and of the conversation, with every
fact they found and no order. This skill is the standard for every Markdown page a person reads,
and the two tests that show whether a page meets it.

**Do not copy the prose around you.** Text already in a project was rarely written to this
standard, and a README that grew by appended sections least of all ([readme.md](readme.md)).

**The project's own rules come first** where they differ: CLAUDE.md, AGENTS.md, CONTRIBUTING.md,
a style guide, a docs linter's config. They decide where pages live, the project's terms, the
wrapping and the templates. This skill fills in the rest.

## Who reads what

Find the project's pages and name each one's reader before changing any of them.

| Page | Its reader | Kind (below) |
|---|---|---|
| README | Someone deciding whether to use the project, then installing and trying it | A short explanation, a tutorial (the quick start), links to the rest |
| Getting started | A new user who wants a first result | Tutorial |
| User guides | A user with one task: deploy, set up a feature, run it in CI | How-to guide, one task a page |
| Commands, options, configuration, environment variables, APIs, file formats | A user looking one thing up | Reference |
| Architecture, how it works | A user or contributor who needs the model before acting on it | Explanation |
| Design docs, plans, decision records | A person reviewing a design they did not write | Explanation, in the project's template if it has one |

A page with a template keeps it. The sentence and word rules below apply to it in full.

## One kind of page at a time (Diátaxis)

| Kind | The reader asks | It holds | It leaves out |
|---|---|---|---|
| Tutorial | "Can I get it working?" | One path, from nothing to a visible result; every step tested | Options, alternatives, reasons |
| How-to guide | "How do I do X?" | Numbered steps to one goal, conditions first, what the reader sees after each step | Teaching, internals |
| Reference | "What exactly does X do?" | Every command, flag or key, each with the same fields: what it does, its default, its limits | Steps, opinions |
| Explanation | "Why does it work this way?" | The model, the trade-offs, the design | Steps, full option lists |

Mixing kinds is the usual cause of a long, hard page: a how-to that stops to explain a cache, a
reference row that tells a story. Split the page and link the parts.

## Before writing

```
- [ ] 1. Name the reader and their task in one sentence ("A developer who has never used the
         tool wants to run it on their own repository")
- [ ] 2. Pick the kind of page
- [ ] 3. Write down 5 to 10 questions the reader has, in their words. They become the
         headings and the reader test
- [ ] 4. Find each fact in the code or in a real run, not in a plan, an issue or an older doc
- [ ] 5. Write the outline, headings only. Read it on its own. Does it answer the questions in
         the order the reader has them?
```

Step 4 comes from a real mistake. A README printed a sample output copied from a plan. Nothing
regenerated it, and the tool had since changed what it printed.

## Pages and sections

- **The point first.** The page, each section and each paragraph open with what the reader most
  needs: what it is, or what to do. Details, exceptions and history come after.
- **Headings say what the reader finds there**, in the reader's words. A how-to's heading is a
  task with a verb ("Deploy to staging"); a reference's is a noun ("Configuration keys").
  Sentence case, three levels at most. "Its settings" says nothing on its own; "Settings for a
  scheduled job" does.
- **Paragraphs hold one topic**, in 80 words or fewer. Wrap the source as the project's other
  Markdown is wrapped. Before wrapping by hand, check whether a formatter rewrites `*.md`
  (Prettier's `proseWrap`, markdownlint's line length).
- **Numbered lists for steps in order**: one action a step, then what the reader sees. **Bullets
  for items in no order.** Introduce each list with a full sentence. Start every item the same
  way (all verbs, or all nouns). Reasons and trade-offs stay prose.
- **Tables for many items with the same fields** (options, keys, error codes). A cell holds a
  phrase or one short sentence; anything longer gets a section and a link.
- **Conditions before instructions**: "To open it in a browser, add `--browser`", not "Add
  `--browser` to open it in a browser".
- **The common case first.** Edge cases, platform notes and internals go in their own section
  or page, linked from where the reader would look for them.
- **Examples are real**: a command and the output it printed, run for the page. A screenshot
  shows the state the text describes.
- **Edit in place.** A new behavior goes where the reader needs it, and the section is reread as
  a whole. An appended paragraph keeps every fact and loses the order. That is how one README
  grew to 1,221 lines, with 28 % of its sentences over 25 words.

## Sentences

Aim for 15 to 20 words a sentence on average. Split any sentence over 25 words, unless it is a
list or a definition that cannot be split.

- **One idea a sentence.** A colon introduces a list, an example or a definition. A semicolon is
  rare. Neither stands in for "and", "so", "because" or "then".
- **Name the actor, in the active voice**: "The tool writes the report to …", not "the report is
  written to …".
- **Talk to the reader as "you"**, in the present tense, and use the imperative for steps.
- **Repeat the noun.** Use "it", "its", "they" or "one" only when the noun it stands for is in the
  same sentence. Undo chains of possessives: "the job's runner's first message" becomes "the
  first message the runner sends for the job".
- **Keep the small words.** Do not drop articles, verbs or "that" to save space. Telegraphic
  prose is the agents' habit and the reader's main obstacle.
- **One aside a sentence, in brackets or between dashes**, a few words long. Never brackets inside
  brackets. A longer aside is a sentence of its own.
- **Say a condition with "if"**, and the other case with "otherwise" or "if not". "Else" is code.
- **Be exact with numbers**: digits and units ("about 5 s", "100 MB"), measured, not adjectives.
- **No filler or hype**: "simply", "just", "easily", "seamless", "powerful", "robust". None of
  the habits that mark machine-written text: "it's not X, it's Y", triplets for rhythm, a closing
  line that repeats the section, emoji in headings.

In these examples, `acme` stands for the project's tool.

| Before | After | Rule |
|---|---|---|
| Its timeout is the job file's when its `limits` sets one, else the runner's own. | The runner stops a job after the `timeout` set in its job file. If the job file sets none, the runner stops the job after 10 minutes. | Name the actor; "if" for the condition; no possessive chain |
| A failed check does not block the merge: the page lists which commands passed; the log has their output. | You can merge even when a check fails. The page lists the commands that passed and failed, and the log shows their output. | One idea a sentence; no colon or semicolon for "and" |
| Records live in `data/items/` (`data/features/` before M25, see RFC-17). | Records are in `data/items/`. (Older versions: one line in an "Upgrading" section.) | No internal IDs in user docs |
| The list comes from the API's `/models` answer, cached for a day. (In a how-to.) | Pick a model from the list. It shows the models your account can use. | A how-to says what the reader does and sees; internals go elsewhere |
| The reconciler fixes it. (First mention.) | A background job, the *reconciler*, compares each record with its source every 5 minutes and fixes any difference. | Define a term where the reader first meets it |
| Add `--browser` to use a browser tab instead of the app's window, when the desktop app is installed. | If you installed the desktop app, `acme view` opens in its window. To use a browser tab instead, add `--browser`. | Condition first; the common case first |

## Words

- **Plain words**: "use", not "utilize"; "to", not "in order to"; "before", not "prior to";
  "for example", not "e.g."; "that is", not "i.e."; "through" or "with", not "via".
- **Define each term where the reader first meets it**, or link to its definition. List the
  project's own terms before writing (its concepts, components, roles and states). Its authors
  no longer see them as terms, so they are the ones left undefined.
- **One word for one thing**, everywhere. Projects rename things, and the old word survives in
  places: one project still said "feature" in its docs long after renaming it "workspace". Find
  the current word in the code and the interface, and keep it. Do not switch to a synonym for
  variety.
- **No internal IDs in user docs.** Milestone IDs, ticket, pull request and decision numbers mean
  nothing to a user: say what changed, or leave it out. Plans and design docs may use IDs, with
  a few words of what each is the first time.
- **Formatting has one meaning each.** `Code` for commands, flags, paths, keys, variables and
  output; **bold** for an on-screen label, as the screen writes it (**Save changes**); keys as
  written on the keyboard (Ctrl+Enter, Esc). Link text names its target ("the
  [configuration reference](docs/reference/configuration.md)"), never "here".

## Check every fact against the code

A page can follow every rule above and still be wrong. Check each kind of fact where the code
defines it, and keep the commands or the script you used, so the next rewrite can run them again.

- **Commands and flags**: build, then run each command's `--help`, or read the argument parser.
- **Configuration keys and environment variables**: find where the code reads each one, with its
  default (`grep -rn 'APP_TOKEN' src`). A documented key the code never reads is stale. A key
  the code reads and the page leaves out is a gap.
- **Labels on screen** (buttons, tabs, menus): against the components, as the screen writes them.
- **CI**: an action's inputs against its `action.yml`, a CI template's variables against the
  template.
- **What it writes and what it sends**: the files by a grep for writes, the network by a grep for
  its calls (`fetch`, the HTTP client, `git push`).
- **Install steps**: run them as written, from a clean clone. Run any line meant for a shell
  profile from another folder. One alias line worked in the checkout and, pasted into a profile,
  pointed at whatever folder the shell started in.
- **Sample output**: a real run, pasted as printed.
- **Links and anchors**: each relative link points to a file that exists, and each `#anchor` to
  a heading. GitHub makes an anchor from a heading in lowercase, spaces as hyphens, punctuation
  dropped: "The app's window" is `#the-apps-window`.
- **Text that points into the docs**: error messages and help text in the code that name a
  section or a docs URL. Moving or renaming the section breaks them: `grep -rn README src`, and
  the tests that assert those messages.
- **Screenshots**: at one fixed size (1440 × 900 is common) from a fresh build, retaken when the
  view changes. Nothing personal in them: user names in paths, emails, tokens, private
  repository names.

## Measure the prose

[readability.mjs](readability.mjs) counts what the rules above are about. It runs on Node 18 or
later, with no packages. It leaves out code, inline code, tables, link targets and front matter.
In the commands below, `<skill>` is this skill's folder.

```sh
node <skill>/readability.mjs README.md docs/guide/*.md
node <skill>/readability.mjs README.md --outline           # the headings, indented
git show main:README.md | node <skill>/readability.mjs -   # another revision's, to compare
```

For each file: words a sentence (average, median, 90th percentile), the sentences over `--max`
words (default 25), sentences with two or more asides in brackets, three or more possessives,
or two or more colons and semicolons inside, and paragraphs over 80 words. Then the longest
sentences with their line numbers (`--top`, default 15).

Targets: an average of 20 words or fewer; no sentence over 40. Every sentence the script
lists is one to reread, not an automatic fix. The script measures length, not sense. The reader
test decides. For scale, one README rewritten to these rules went from 20.1 words a sentence
(the longest 94, 28 % over 25) to 12.2 (the longest 32, 4 sentences over 25).

## Reader test

This is Anthropic's "reader testing", from the `doc-coauthoring` skill in its public skills
repository. A fresh agent reads the page with no other context, the way a person meets it. It
catches what the fact check misses. In one rewrite, every flag and key had been checked against
the code, and both rounds of the test still found claims that were true word by word and wrong
for the reader, and terms used before their definitions.

1. **Take the reader's questions** from "Before writing", step 3. Write down the right answer to
   each, from the code.
2. **Ask a fresh agent**: a subagent, or a new session that has not seen the work. Paste the
   page into its prompt and tell it to use no tools, so that it answers from the page and not
   from the code:

   ```
   You are reading a page of a project's documentation for the first time. Use no tools, and
   nothing you know about the project beyond this page. For each question, answer from the page
   and quote the sentence you used; if the page does not say, answer "guessed" with what you
   assumed, or "not on the page". Then list every term the page uses before it explains it,
   every sentence you had to read twice (quote it), and what you would do first after reading.

   Questions:
   1. …

   The page:
   <the page's text>
   ```

3. **Score it.** A wrong answer or a guess means the sentence it quoted misleads: rewrite that
   sentence. "Not on the page", for a question the reader has, means the page is missing it. Each
   term used before it is explained gets a definition. Each sentence read twice gets rewritten.
4. **Test again with a new agent** after the fixes: the first one has learned the page. The page
   passes when every answer is right and quoted.
5. **Skim test**: read only the headings and the first sentence of each paragraph
   (`--outline` for the headings). They should tell the page's story on their own.

Then give the page to the person, with the questions, the test's results and the numbers.

## Checklist (writing or rewriting a page)

```
- [ ] 1. Before writing: the reader, the kind of page, the questions, the facts, the outline
- [ ] 2. Measure the current page (readability.mjs), if there is one
- [ ] 3. Write it: pages and sections, sentences, words (above)
- [ ] 4. Check every fact against the code; links, anchors, and messages that name a section
- [ ] 5. Measure again; reread every sentence it lists
- [ ] 6. Reader test until every answer is right; skim test
- [ ] 7. Record it where the project records work (a journal, a changelog, the pull request):
         the numbers before and after, the reader test's questions and results, what was
         not verified
```

## Sources

The rules above are condensed from these, which say more:

- Diátaxis, the four kinds of documentation: diataxis.fr
- Google developer documentation style guide: developers.google.com/style
- Microsoft Writing Style Guide: learn.microsoft.com/style-guide
- Plain-language guidance: the US Federal Plain Language Guidelines (plainlanguage.gov), and
  GOV.UK's content design guidance (gov.uk/guidance/content-design), which keeps sentences
  to 25 words
- Anthropic's skills repository, `doc-coauthoring` (reader testing): github.com/anthropics/skills
- standard-readme, the sections of a README: github.com/RichardLitt/standard-readme
- Wikipedia's "Signs of AI writing", for the habits of machine-written text
