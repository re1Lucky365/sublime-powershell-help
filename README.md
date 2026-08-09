# PowerShell Help syntax

Syntax highlighting for PowerShell help pages (`Get-Help <command-name>`). It
recognizes help sections, command signatures, parameters, .NET types, examples,
links, and Markdown formatting. PowerShell code blocks use `bat`'s built-in
PowerShell syntax.

This was mainly created for use with [`bat`](https://github.com/sharkdp/bat)
and hasn't been tested with Sublime Text.

<p align="center">
  <img src="sample.png" alt="PowerShell help rendered with bat">
</p>
<p align="center">
  <em>Actual colors will depend on your <code>bat</code> theme</em>
</p>

## Installation

Clone the repository directly into `bat`'s `syntaxes` directory, then rebuild the syntax cache. You could also copy just the `pshelp.sublime-syntax` file.

### Using PowerShell

```powershell
$syntaxDir = Join-Path (bat --config-dir) syntaxes
New-Item -ItemType Directory -Force $syntaxDir | Out-Null
Set-Location $syntaxDir
# Clone the repo; bat checks subdirs
git clone --depth=1 https://github.com/syntactic-spice/sublime-powershell-help
bat cache --build
```

### Using Bash

```sh
syntax_dir="$(bat --config-dir)/syntaxes"
mkdir -p "$syntax_dir"
cd "$syntax_dir"
# Clone the repo; bat checks subdirs
git clone --depth=1 https://github.com/syntactic-spice/sublime-powershell-help
bat cache --build
```

### Confirm installation

```console
bat --list-languages
```
Look for `PowerShell Help Page`

## Usage

To use it once, pipe `help` output to `bat`:

```powershell
help gci | bat -l pshelp
```

To make `bat` the default pager for help pages, add this to your
PowerShell profile (`vim $profile`):

```powershell
$env:PAGER = 'bat --language=pshelp'
```
Restart PowerShell
