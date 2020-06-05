# Commit messages
A commit message should give a clear and succinct description of code changes to be applied and provide enough context for developers in the future to understand the reason(s) behind the changes.


## Subject line

**DO**

- Summarise the changes in less than 50 characters
- Use active voice - try and finish the sentence “This commit will…”
- Include a JIRA issue number at the beginning of the message
- Start the summary with a capital letter

**DON’T**

- End the summary with a full stop

**EXAMPLE**


    Bump app version to 2.0.1
    GALAXY-123 Fix click events in carousel card
    GALAXY-789 Add layouts for carousel card


## Body paragraph

**DO**

- Separate the description from the summary with a line break
- Focus on the reasons *why* the change was required
- Use bullet points where appropriate

**DON’T**

- Repeat the list of file changes - developers can see which files are affected in the diff


## Notes
- Using the active voice in the subject line matches up with commit messages generated by commands like `git merge` and `git revert`.
- Adding a commit body shouldn’t usually be necessary as long as the JIRA issue number has been included in the subject line and the code changes relate directly to the ticket.


## Further reading
[The art of the commit](https://alistapart.com/article/the-art-of-the-commit/)

[On the importance of commit messages](https://americanexpress.io/on-the-importance-of-commit-messages/)

[Writing good commit messages: a practical guide](https://www.freecodecamp.org/news/writing-good-commit-messages-a-practical-guide/)

[Which commit message convention do you use at work?](https://hashnode.com/post/which-commit-message-convention-do-you-use-at-work-ck3e4jbdd00zyo4s1h7mc7e0g)