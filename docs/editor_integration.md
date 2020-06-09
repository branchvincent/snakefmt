# Editor Integration

If your favourite editor is not listed here, we would love to receive a PR with how to
include it.

**Unless otherwise specified, all instructions assume you have `snakefmt` installed
already.**

[TOC]: #

# Table of Contents
- [PyCharm/JetBrains IDEA](#pycharmjetbrains-idea)


## PyCharm/JetBrains IDEA

1. Locate the path to your `snakefmt` executable.

```sh
# linux and macOS
$ which snakefmt
/usr/local/bin/snakefmt  # just an example

# windows
$ where snakefmt
%LocalAppData%\Programs\Python\Python36-32\Scripts\snakefmt.exe  # just an example
```

2. Open External tools in PyCharm/IntelliJ IDEA

- On macOS: `PyCharm -> Preferences -> Tools -> External Tools`

- On Windows / Linux / BSD: `File -> Settings -> Tools -> External Tools`

3. Click the `+` icon to add a new external tool with the following values:

   - Name: Snakefmt
   - Description: The uncompromising Snakemake code formatter
   - Program: result of `which/where snakefmt` from step 1
   - Arguments: `"$FilePath$"`

4. Format the currently opened file by selecting `Tools -> External Tools -> Snakefmt`.

   - Alternatively, you can set a keyboard shortcut by navigating to
     `Preferences/Settings -> Keymap -> External Tools -> External Tools - Snakefmt`. We
     use <kbd>Alt</kbd>+<kbd>s</kbd>

5. Optionally, run `snakefmt` on every file save:

   1. Make sure you have the
      [File Watchers](https://plugins.jetbrains.com/plugin/7177-file-watchers) plugin
      installed.
   2. Go to `Preferences or Settings -> Tools -> File Watchers` and click `+` to add a
      new watcher:
      - Name: Snakefmt
      - File type: Python
      - Scope: Project Files
      - Program: result of `which/where snakefmt` from step 1
      - Arguments: `$FilePath$`
      - Output paths to refresh: `$FilePath$`
      - Working directory: `$ProjectFileDir$`

   - Uncheck "Auto-save edited files to trigger the watcher" in Advanced Options
