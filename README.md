# Mini Shell in C

A lightweight command-line tool written in C that mimics a Unix shell prompt and reimplements the `ls` command using low-level directory system calls.

## Features

- Displays a personalized shell-style prompt (`yourname$`)
- Supports `ls` — lists files in the current directory, excluding hidden files
- Supports `ls -a` — lists all files, including hidden ones (dotfiles)

## How It Works

The program uses POSIX directory functions (`opendir`, `readdir`, `closedir` from `dirent.h`) to read directory entries directly, rather than shelling out to the system's actual `ls` binary — this is a from-scratch reimplementation of that listing behavior.

## Tech Used

- C
- POSIX APIs (`dirent.h`)

## How to Run

**Note:** This only works on Linux and macOS (uses POSIX-specific headers not available on Windows).

```bash
gcc Bottle.c -o mini_shell
./mini_shell
```

Enter your name when prompted, then type `ls` or `ls -a` at the prompt.

## Notes

Currently handles one command per run before exiting. Any input other than `ls` or `ls -a` is silently ignored.

## Future Improvements

- Wrap the prompt in a loop to support multiple commands per session
- Add more shell commands (`pwd`, `cd`, `mkdir`)
- Handle unrecognized commands with an error message instead of silent exit
- Remove compiled binaries (`a.out`) from version control and add a `.gitignore`
