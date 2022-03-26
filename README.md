# Obsidian-Alfred-Workflow

An Alfred workflow for Obsidian that fits my need.

## Motivation

Automation helps to reduce friction in workflows. Alfred provides a sandbox environment for building highly-customisable workflows. There are already workflows for obsidians out on GitHub like [obsidian-utilities](https://github.com/macedotavares/obsidian-utilities) and [obsidian-alfred](https://github.com/hauselin/obsidian-alfred). However, I personally find them a bit overcomplicated, so I decided to create my own with simplicity and expandability in mind. 

![Pasted image 20220318094844](https://user-images.githubusercontent.com/38693485/160223112-5eef4423-d95b-4220-b945-710ebb152cb2.png)

## Features

- `o` to open your vault
- `o` + `⌘⏎` to open vault in VSCode (or your preferred editor)
- Any number of capture actions that appends something to a note, with a customisable template. For example:
	- `oi` to append an idea to an idea inbox and adds a timestamp
	- `os` to append an item to a shopping list and adds a `- [ ]` checkbox in front of it
- Any number of capture actions that appends something to a heading in a note, with a customisable template. For example:
	- `oj` to add a journal entry with a timestamp and the tag `#journal` under the `### Journal` heading in today's note
	- `ot` to add a task under the `### Inbox` heading in today's note

## How it works

Opening the vault is pretty straightforward with Alfred's built-in Launch Apps and Open File actions. 

Append is also done using Alfred's built-in Write Text File action.

The append to heading feature is based on [obsidian-utilities](https://github.com/macedotavares/obsidian-utilities) but with a script modified to be more customisable. Basically, the workflow reads a file, pass the text content to a python script that adds an insertion under a particular heading using regular expression, and write the new content to file.

## How to use

==Backup your vault first!==

There might be untested edge cases that would cause the script to break something. The last thing you want is to lose your work.

###### 1. Specify the vault path in the workflow's environmental variables

![Pasted image 20220318102733](https://user-images.githubusercontent.com/38693485/160223179-52ea8db8-2601-4e64-aa75-fd41541ebe27.png)

###### 2. Create capture and append actions keywords by duplicating the capture template

Duplicating the first two nodes are sufficient. Specify the keyword in the Keyword node and add a description.

![Pasted image 20220318103022](https://user-images.githubusercontent.com/38693485/160223188-6edb19e2-087d-4efe-b242-a449ed0c3292.png)

Configure the insertion action using the FORMAT & SETUP node.

- Use the Argument field to format the inserted content. A timestamp can be created this way.
- The `filepath` variable needs to be the path to your markdown file

Example:

![Pasted image 20220318103256](https://user-images.githubusercontent.com/38693485/160223192-172f7ccf-3161-423e-b3c0-f701ee2878c7.png)

###### 3. Set up append under heading

We do the same thing of duplicating the first two nodes and connecting them all to the third node in the template sequence. Once again, specify the keyword.

![Pasted image 20220318103744](https://user-images.githubusercontent.com/38693485/160223204-9a966a4d-b3bc-4500-905b-8239c1a336f0.png)

The FORMAT & SETUP node needs a slightly different setup:

- Format the inserted content in the Argument field
- Set the `filepath` variable to the path to your markdown file
- Set the `heading` variable to the heading under which the insertion takes place. Include the octothorpes.

![Pasted image 20220318103849](https://user-images.githubusercontent.com/38693485/160223209-32260102-b15b-4984-9ffa-9436104c4917.png)

That's it. Enjoy :).
