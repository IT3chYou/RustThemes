# VS Code Theme Extension — From Scratch

A step-by-step guide to creating, packaging, and installing a custom **Visual Studio Code theme extension** from scratch.

This guide covers everything from creating the project files to generating a `.vsix` package and installing it in VS Code.

---

## 📋 Requirements

Before starting, make sure you have:

* [Visual Studio Code](https://code.visualstudio.com/)
* Node.js and npm
* A terminal
* A text editor such as VS Code or Nano

---

## 📁 Project Structure

Your theme project will contain the following files:

```text
my-neon-theme/
├── package.json
└── my-neon-theme.json
```

---

## 1. Create the Project Folder

Open a terminal and create a folder for your theme:

```bash
mkdir my-neon-theme
cd my-neon-theme
```

`mkdir` creates the project directory, while `cd` moves into it.

All of the following commands should be executed inside this directory.

---

## 2. Create the Required Files

Create the two files required for the theme:

```bash
touch package.json
touch my-neon-theme.json
```

The files have different purposes:

* `package.json` — contains the extension metadata and configuration.
* `my-neon-theme.json` — contains the theme definition and colors.

---

## 3. Configure `package.json`

Open `package.json` with VS Code, Nano, or another text editor and add:

```json
{
  "name": "my-neon-theme",
  "displayName": "My Awesome Neon Theme",
  "description": "My first custom dark theme",
  "version": "1.0.0",
  "publisher": "your_name",
  "engines": {
    "vscode": "^1.60.0"
  },
  "categories": [
    "Themes"
  ],
  "contributes": {
    "themes": [
      {
        "label": "My Neon Theme",
        "uiTheme": "vs-dark",
        "path": "./my-neon-theme.json"
      }
    ]
  }
}
```

### What does `package.json` do?

VS Code uses this file to understand the extension.

For example:

* `"categories": ["Themes"]` tells VS Code that this is a theme extension.
* `"uiTheme": "vs-dark"` specifies that the theme is based on the dark VS Code interface.
* `"path"` tells VS Code where the theme definition is located.
* `"version"` specifies the extension version.

---

## 4. Configure the Theme

Open:

```text
my-neon-theme.json
```

and add:

```json
{
  "name": "My Neon Theme",
  "type": "dark",
  "colors": {
    "editor.background": "#0d0d0d",
    "editor.foreground": "#00ffcc",
    "activityBar.background": "#000000",
    "sideBar.background": "#1a1a1a"
  }
}
```

These settings control the basic appearance of VS Code.

| Setting                  | Description             |
| ------------------------ | ----------------------- |
| `editor.background`      | Editor background       |
| `editor.foreground`      | Main editor text color  |
| `activityBar.background` | Activity bar background |
| `sideBar.background`     | Sidebar background      |

You can change the hexadecimal color values to customize the appearance of your theme.

---

## 5. Package the Theme

Once your files are ready, package the extension:

```bash
npx @vscode/vsce package
```

This creates a `.vsix` package that can be installed by VS Code.

For example:

```text
my-neon-theme-1.0.0.vsix
```

### Why use `npx`?

`npx` allows you to run the VS Code extension packaging tool without permanently installing it globally.

If `vsce` warns that `README.md` is missing, confirm with:

```text
y
```

and press **Enter**.

> **Note:** This README file itself can be used as the project's `README.md`, so once you add it to the repository, that warning should no longer occur.

---

## 6. Install the Theme

After generating the `.vsix` file, install it with:

```bash
code --install-extension my-neon-theme-1.0.0.vsix
```

VS Code will install the theme as an extension.

After installation, open the VS Code theme selector:

```text
Ctrl + Shift + P
```

Then search for:

```text
Preferences: Color Theme
```

and select:

```text
My Neon Theme
```

---

## 7. Modify the Theme

Want to change the colors?

Simply edit:

```text
my-neon-theme.json
```

For example:

```json
"editor.background": "#101010"
```

Change the value to whatever color you want.

---

## 8. Create a New Version

When you make changes, update the version inside `package.json`.

For example:

```json
"version": "1.0.1"
```

Then package the extension again:

```bash
npx @vscode/vsce package
```

A new file will be generated:

```text
my-neon-theme-1.0.1.vsix
```

Install the updated version with:

```bash
code --install-extension my-neon-theme-1.0.1.vsix --force
```

The `--force` option forces VS Code to overwrite the existing installation.

---

## 🔄 Development Workflow

The basic workflow is:

```text
Edit theme
   ↓
Update version
   ↓
Package with vsce
   ↓
Generate .vsix
   ↓
Install with VS Code
   ↓
Test the theme
   ↓
Repeat
```

---

## 📦 Final Project Structure

After adding the README, your repository can look like this:

```text
my-neon-theme/
├── README.md
├── package.json
└── my-neon-theme.json
```

After packaging, you may also have:

```text
my-neon-theme/
├── README.md
├── package.json
├── my-neon-theme.json
└── my-neon-theme-1.0.0.vsix
```

---

## 🚀 Quick Commands

For quick reference:

```bash
# Create project
mkdir my-neon-theme
cd my-neon-theme

# Create files
touch package.json
touch my-neon-theme.json

# Package extension
npx @vscode/vsce package

# Install extension
code --install-extension my-neon-theme-1.0.0.vsix

# Package a new version
npx @vscode/vsce package

# Force update
code --install-extension my-neon-theme-1.0.1.vsix --force
```

---

## Preview

![My Neon Theme Preview](preview.png)
