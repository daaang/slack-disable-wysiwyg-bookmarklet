# Slack Disable WYSIWYG Bookmarklet

*Disables the WYSIWYG editor in Slack.*

## Motivation

On 2019-11-20 Slack rolled out a new version of the editor. This editor features
[WYSIWYG](https://en.wikipedia.org/wiki/WYSIWYG) functionality, which shows all
message formatting inline in the text box.

As of this time, Slack does not allow users to disable this functionality and
revert back to the plaintext markdown editor. Until Slack implements this
functionality, you can use this bookmarklet to temporarily disable all
WYSIWYG A/B tests, which should restore the old editor functionality.

## Usage

### In the browser

1. Copy the contents of `index.js`
2. Paste into the URL field of a browser bookmark
3. Navigate to a Slack workspace in that browser
4. Execute the bookmarklet to disable the WYSIWYG editor
5. Repeat each time you reload slack

### In the desktop app

1. Open the slack app in Developer mode
    * On Mac: `export SLACK_DEVELOPER_MENU=true && open -a /Applications/Slack.app`
    * On PC in a Powershell window (per user install): `$env:SLACK_DEVELOPER_MENU="true"; & "$($env:LOCALAPPDATA)\Slack\slack.exe"`
    * On PC in a Powershell window (machine wide install): `$env:SLACK_DEVELOPER_MENU="true"; & "$($Env:ProgramFiles)\Slack Deployment\slack.exe"`
    * On PC with slack managed by the Windows 10 App Store: uninstall slack, [download the exe](https://slack.com/downloads/windows), and follow one of the above instructions
    * On other OS's: ensure the `SLACK_DEVELOPER_MENU` environment variable is set to `true` before opening the Slack app.
2. Right-click in the app and _Inspect element_
3. Copy the contents of `index.js`
4. Paste into the Console tab
5. Repeat each time you reload slack or switch to a team for the first time

### In Franz

[Franz](https://github.com/meetfranz/franz) is an Electron-based messaging aggregator application.

1. With Slack opened inside Franz, use the keyboard shortcut to open up the inspector:
   - Mac: <kbd>⌘ command</kbd> + <kbd>⌥ option</kbd> + <kbd>I</kbd>
   - Windows/Linux: <kbd>⌃ ctrl</kbd> + <kbd>⇧ shift</kbd> + <kbd>I</kbd>

2. Open up the console tab, and run the following to open up the current Slack instance's dev console:

   ```js
   $(".app__service .is-active webview").openDevTools()
   ```

3. In the newly opened console window, paste in the script from `index.js` without the `javascript:` prefix.
