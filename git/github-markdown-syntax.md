###### [Writing on GitHub](https://help.github.com/categories/writing-on-github) / Basic writing and formatting syntax

### 마크다운 문법 참고하자!

## Basic writing and formatting syntax

Create sophisticated formatting for your prose and code on GitHub with simple syntax.

### Headings

To create a heading, add one to six `#` symbols before your heading text. The number of `#` you use will determine the size of the heading.

```
# The largest heading
## The second largest heading
###### The smallest heading

```

![Rendered H1, H2, and H6 headings](https://help.github.com/assets/images/help/writing/headings-rendered.png)

### Styling text

You can indicate emphasis with bold, italic, or strikethrough text.

| Style           | Syntax            | Keyboard shortcut   | Example                                  | Output                             |
| --------------- | ----------------- | ------------------- | ---------------------------------------- | ---------------------------------- |
| Bold            | `** **` or`__ __` | command/control + b | `**This is bold text**`                  | **This is bold text**              |
| Italic          | `* *` or `_ _`    | command/control + i | `*This text is italicized*`              | *This text is italicized*          |
| Strikethrough   | `~~ ~~`           |                     | `~~This was mistaken text~~`             | ~~This was mistaken text~~         |
| Bold and italic | `** **`and `_ _`  |                     | `**This text is _extremely_ important**` | **This text isextremelyimportant** |

### Quoting text

You can quote text with a `>`.

```
In the words of Abraham Lincoln:

> Pardon my French
```

![Rendered quoted text](https://help.github.com/assets/images/help/writing/quoted-text-rendered.png)

**Tip:** When viewing an issue or pull request, you can automatically quote text in a reply by highlighting the text, then typing`r`. For more information, see "[Using keyboard shortcuts](https://help.github.com/articles/using-keyboard-shortcuts/)."

### Quoting code

You can call out code or a command within a sentence with single backticks. The text within the backticks will not be formatted.

`Use `git status` to list all new or modified files that haven't yet been committed.`

![Rendered inline code block](https://help.github.com/assets/images/help/writing/inline-code-rendered.png)

To format code or text into its own distinct block, use triple backticks.

```
Some basic Git commands are:
​```
git status
git add
git commit
​```

```

![Rendered code block](https://help.github.com/assets/images/help/writing/code-block-rendered.png)

For more information, see "[Creating and highlighting code blocks](https://help.github.com/articles/creating-and-highlighting-code-blocks)."

### Links

You can create an inline link by wrapping link text in brackets `[ ]`, and then wrapping the URL in parentheses `( )`. You can also use the keyboard shortcut `command + k` to create a link.

`This site was built using [GitHub Pages](https://pages.github.com/).`

![Rendered link](https://help.github.com/assets/images/help/writing/link-rendered.png)

**Tip:** GitHub automatically creates links when valid URLs are written in a comment. For more information, see "[Autolinked references and URLS](https://help.github.com/articles/autolinked-references-and-urls)."

### Lists

You can make a list by preceding one or more lines of text with `-` or `*`.

```
- George Washington
- John Adams
- Thomas Jefferson

```

![Rendered unordered list](https://help.github.com/assets/images/help/writing/unordered-list-rendered.png)

To order your list, precede each line with a number.

```
1. James Madison
2. James Monroe
3. John Quincy Adams

```

![Rendered ordered list](https://help.github.com/assets/images/help/writing/ordered-list-rendered.png)

You can create nested lists by indenting lines by two spaces.

```
1. Make my changes
  1. Fix bug
  2. Improve formatting
    * Make the headings bigger
2. Push my commits to GitHub
3. Open a pull request
  * Describe my changes
  * Mention all the members of my team
    * Ask for feedback

```

![Rendered nested list](https://help.github.com/assets/images/help/writing/nested-list-rendered.png)

### Task lists

You can create [task lists](https://github.com/blog/1375%0A-task-lists-in-gfm-issues-pulls-comments) by prefacing list items with `[ ]`. To mark a task as complete, use `[x]`.

Task lists render with checkboxes in all comments and Markdown files. Select or unselect the checkboxes to mark them as complete or incomplete.

```
- [x] Finish my changes
- [ ] Push my commits to GitHub
- [ ] Open a pull request

```

![Rendered task list](https://help.github.com/assets/images/help/writing/task-list-rendered.png)

You can reorder task lists by clicking to the left of a task's checkbox, dragging it to a new location, and dropping it. If you have multiple lists within a comment, you can reorder tasks across them. You can't add or reorder tasks in other comments.

![Reordered task list](https://help.github.com/assets/images/help/writing/task-list-reordered.gif)

### Mentioning users and teams

You can mention a user or [team](https://help.github.com/articles/setting-up-teams/) on GitHub by typing `@` plus their username or team name to trigger a[notification](https://help.github.com/articles/about-notifications) and bring their attention to an issue or pull request. People will also receive a notification if you edit a comment to mention their username or team name.

`@github/support What do you think about these updates?`

![Rendered @mention](https://help.github.com/assets/images/help/writing/mention-rendered.png)

Typing an `@` symbol will bring up a list of people or teams on a project. The list filters as you type, so once you find the name of the person or team you are looking for, you can use the arrow keys to select it and hit either tab or enter to complete the name. For teams, just enter the @organization/team-name and all members of that team will get subscribed to the issue.

The autocomplete results are restricted to repository collaborators and any other participants on the thread.

### Referencing issues and pull requests

You can bring up a list of suggested Issues and Pull Requests within the repository by typing `#`. Type the issue or PR number or title to filter the list, then hit either tab or enter to complete the highlighted result.

For more information, see "[Autolinked references and URLs](https://help.github.com/articles/autolinked-references-and-urls)."

### Using emoji

You can add emoji to your writing by typing `:EMOJICODE:`.

`@octocat :+1: This PR looks great - it's ready to merge! :shipit:`

![Rendered emoji](https://help.github.com/assets/images/help/writing/emoji-rendered.png)

Typing `:` will bring up a list of suggested emoji. The list will filter as you type, so once you find the emoji you're looking for, press **Tab** or **Enter** to complete the highlighted result.

For a full list of available emoji and codes, check out [emoji-cheat-sheet.com](http://emoji-cheat-sheet.com/).

### Paragraphs and line breaks

You can create a new paragraph by leaving a blank line between lines of text.

### Ignoring Markdown formatting

You can tell GitHub to ignore (or escape) Markdown formatting by using `\` before the Markdown character.

`Let's rename \*our-new-project\* to \*our-old-project\*.`

![Rendered escaped character](https://help.github.com/assets/images/help/writing/escaped-character-rendered.png)

For more information, see Daring Fireball's "[Markdown Syntax](https://daringfireball.net/projects/markdown/syntax#backslash)."

### Further reading

- "[About writing and formatting on GitHub](https://help.github.com/articles/about-writing-and-formatting-on-github)"
- "[Working with advanced formatting](https://help.github.com/articles/working-with-advanced-formatting)"
- "[Mastering Markdown](https://guides.github.com/features/mastering-markdown/)"
- "[Markdown Tutorial](http://markdowntutorial.com/)"


- [ Contact a human](https://github.com/contact)

[![The GitHub Logo](https://help.github.com/assets/images/site/invertocat.png)](https://github.com/)© 2016 GitHub Inc. All rights reserved.[Terms of Service](https://help.github.com/terms-of-service)[Privacy](https://help.github.com/privacy-policy)[Security](https://help.github.com/security)[Support](https://github.com/contact)