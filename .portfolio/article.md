## What it is

Claude Crab is a small extension for VS Code (the code editor) that puts an animated pixel crab in a panel next to your work. Claude Code, the AI assistant that does the typing, normally works out of sight, and the only way to follow along is to watch a stream of text go past. The crab turns that into a glance. When a file is being read the crab looks down at a page below it. When a file is being written a yellow pencil sweeps across that page. When a command is running the crab turns to face a small beige computer and green text types itself across the screen. When the assistant stops, the crab either grins with sparkles and a green tick, or crosses its eyes and pulls a frown, which is a nod to the losing face in Minesweeper.

![The error pose](media/02-error.webp)

## How it works

Claude Code can be told to run a command of your choice whenever something happens: a session starts, a tool is about to run, a tool has finished, the assistant has stopped. The extension writes those entries into Claude Code's settings file for you, and each one posts the event, as JSON, to a small web server the extension runs on a fixed port on your own machine. That is the whole bridge, and nothing leaves the computer. The extension reads the event, works out which pose it means (a read becomes the reading pose, a shell command becomes the terminal pose) and, when the assistant signs off, skims the last message for words like "done" or "failed" to choose between the happy and unhappy endings.

## The interesting part

There are no image files. Every frame is drawn square by square in code on a grid 36 wide and 36 tall, from a fixed palette of about twenty colours, three of which are read from your active VS Code theme so the paper, the code lines and the crab's eyes match the editor you are already using. An animation is just a list of those grids with a number of frames each, so the bobbing idle, the typing terminal and the building thought bubble are all the same mechanism. Keeping it that tiny is the point: at 36 pixels across there is no room for detail, so each pose has to be readable from a squint, which is exactly how it gets looked at.

## Where it is up to

It works and it has been packaged into an installable file, but it was never published to the VS Code Marketplace, so installing it means building it yourself, and it has not been touched since May 2026. The README is also behind the code: it describes a "Set up hooks" command in the command palette, but that command is only registered internally now, and the extension instead offers to write the hooks for you the first time it starts.
