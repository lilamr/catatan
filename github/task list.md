You can use task lists to break the work for an issue or pull request into smaller tasks, then track the full set of work to completion.

**Note:** For more information about the new iteration of tasklists, which is currently in beta, see "[Creating a tasklist](https://docs.github.com/en/issues/tracking-your-work-with-issues/about-tasklists)."

## [About task lists](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/about-task-lists#about-task-lists)

A task list is a set of tasks that each render on a separate line with a clickable checkbox. You can select or deselect the checkboxes to mark the tasks as complete or incomplete.

You can use Markdown to create a task list in any comment on GitHub. If you reference an issue, pull request, or discussion in a task list, the reference will unfurl to show the title and state.

## [About issue task lists](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/about-task-lists#about-issue-task-lists)

If you add a task list to the body of an issue, the list has added functionality.

- To help you track your team's work on an issue, the progress of an issue's task list appears in various places on GitHub, such as a repository's list of issues.
- If a task references another issue and someone closes that issue, the task's checkbox will automatically be marked as complete.
- If a task requires further tracking or discussion, you can convert the task to an issue by hovering over the task and clicking

- in the upper-right corner of the task. To add more details before creating the issue, you can use keyboard shortcuts to open the new issue form. For more information, see "[Keyboard shortcuts](https://docs.github.com/en/get-started/accessibility/keyboard-shortcuts#issues-and-pull-requests)."
- Any issues referenced in the task list will specify that they are tracked in the referencing issue.

![Screenshot of a GitHub issue showing a task list under the header "Features." Some items are checked as done, others unchecked as undone. Three list items link to other GitHub Issues.](https://docs.github.com/assets/cb-127417/images/help/writing/task-list-rendered.png)

## [Creating task lists](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/about-task-lists#creating-task-lists)

To create a task list, preface list items with a hyphen and space followed by `[ ]`. To mark a task as complete, use `[x]`.

```markdown
- [x] #739
- [ ] https://github.com/octo-org/octo-repo/issues/740
- [ ] Add delight to the experience when all tasks are complete :tada:
```

![Screenshot showing the rendered version of the markdown. The references to issues are rendered as issue titles.](https://docs.github.com/assets/cb-64626/images/help/writing/task-list-rendered-simple.png)

**Tip:** You cannot create task list items within closed issues or issues with linked pull requests.

## [Reordering tasks](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/about-task-lists#reordering-tasks)

You can reorder the items in a task list. First, click or hover to the left of a task's checkbox until a grid of six dots appears. Then, drag and drop the grid to move the task to a new location.

You can reorder tasks across different lists in the same comment, but you cannot reorder tasks across different comments.

![Screenshot of a GitHub issue showing two tasks in a task list. A grid of six dots to the left of the second task is outlined in dark orange.](https://docs.github.com/assets/cb-26414/images/help/writing/task-list-reorder.png)

## [Converting tasks into issues](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/about-task-lists#converting-tasks-into-issues)

You can also convert tasks into issues. First, hover over one of the items in your task list and then click

.

![Screenshot of a GitHub issue showing two tasks. The"Convert to issue" icon is highlighted with an orange outline.](https://docs.github.com/assets/cb-47821/images/help/writing/convert-task-lists-into-issues.png)

## [Navigating tracked issues](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/about-task-lists#navigating-tracked-issues)

Any issues that are referenced in a task list specify that they are tracked by the issue that contains the task list. To navigate to the tracking issue from the tracked issue, click on the tracking issue number in the **Tracked in** section next to the issue status.

![Screenshot of a GitHub issue named "Create relationships between issues" and numbered issue 3. A button below the issue title reading "Tracked by issue #2" is outlined in dark orange.](https://docs.github.com/assets/cb-111881/images/help/writing/task-list-tracked.png)

## [Further reading](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/about-task-lists#further-reading)

- "[Tracking code scanning alerts in issues using task lists](https://docs.github.com/en/code-security/code-scanning/managing-code-scanning-alerts/tracking-code-scanning-alerts-in-issues-using-task-lists)"