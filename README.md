# VS Code Settings

This is a personal Visual Studio Code user-settings collection. It includes editor, formatting, file icon, Git, terminal, and a few extension preferences. This is not an app or project, so there is nothing to build or run.

## Before You Apply It

These are personal preferences, so review them against your own setup and comfort level. In particular:

- `security.workspace.trust.untrustedFiles: "open"` opens files from untrusted workspaces without prompting. You can set it to `"prompt"` if you want a confirmation before opening them.
- `git.confirmSync: false` disables the confirmation before Git sync.
- `explorer.confirmDelete: false` and `explorer.confirmDragAndDrop: false` disable Explorer safety prompts.
- `chat.editing.confirmEditRequestRemoval: false` disables a chat editing confirmation.
- Auto Save runs after one second, and Format on Save may rewrite files when they are saved.

If a setting does not match your workflow or security preference, remove it or change it to your own value.

## Apply the Settings

1. Open VS Code and press `Ctrl+Shift+P`.
2. Choose **Preferences: Open User Settings (JSON)**.
3. Review the settings in [`settings.json`](settings.json).
4. Merge the values you want into your own VS Code user settings file. Do not replace the entire file unless you want to remove your previous settings. If the same key already exists, decide which value you want to keep.
5. Save the file. Most settings apply immediately. If a theme or extension setting does not apply, reload the VS Code window.

This `settings.json` file includes comments for section labels. VS Code supports JSONC for settings files, so these comments are valid there.

## Install the Required Extensions

The main shortcut for running code depends on **Code Runner**. Other extensions are optional and support the theme, icons, and related features. Install them from the VS Code Extensions view or via the terminal:

```sh
code --install-extension formulahendry.code-runner
code --install-extension esbenp.prettier-vscode
code --install-extension pkief.material-icon-theme
code --install-extension Equinusocio.vsc-material-theme
code --install-extension ritwickdey.liveserver
code --install-extension wallabyjs.console-ninja
code --install-extension anthropic.claude-code
```

If an extension is not installed, its settings will usually be ignored. The settings file does not install extensions automatically. If you use Code Runner for compiled languages, you also need the corresponding compiler or runtime installed on your machine.

## Run Code with Ctrl+R

VS Code keybindings cannot be stored inside `settings.json`. The shortcut is shown below so you can add it to your own user `keybindings.json` file.

1. Press `Ctrl+Shift+P`.
2. Select **Preferences: Open Keyboard Shortcuts (JSON)**.
3. Add the following object to your user keybindings file. If the file already contains `[]`, insert the object inside the array. If other keybindings already exist, separate them with a comma.

```json
{
  "key": "ctrl+r",
  "command": "code-runner.run",
  "when": "editorTextFocus && !editorReadonly && !inDebugMode"
}
```

4. Save the file, then focus any editable code file and press `Ctrl+R`.

This shortcut overrides the normal `Ctrl+R` behavior in the editor context only. In other places, the previous shortcut remains unchanged.

## What This Settings File Includes

- Editor: smooth cursor, word wrap, two-space indentation, Auto Save, and format on save/paste/type.
- Prettier: quote style, trailing comma, line width, and tab preference.
- File recognition and custom Material Icon Theme mappings for common JavaScript/TypeScript files and folders.
- Workbench, Git, Explorer, terminal, and a few extension-related preferences.
- Code Runner: save and run the active file in the integrated terminal.

This repository does not include extension packages, snippets, project-specific settings, or workspace files.

## Repository Maintenance

Update [`settings.json`](settings.json) for shared preferences. Keep the keybinding snippet in your own VS Code `keybindings.json`, because that file is separate from the settings file. Before syncing or publishing changes, review them and avoid including machine-specific or personal data in the public repository.
