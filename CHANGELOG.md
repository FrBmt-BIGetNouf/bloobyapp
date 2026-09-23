# Changelog

Everything that changed in Blooby, newest first.
Blooby updates itself, so you normally land on the latest version on your own.

## 1.30.42 (2026-09-14)

### New

- **macos**: Blooby is now built and published for macOS. The release ships a universal app that runs on both Apple Silicon and Intel Macs.

### Fixed

- **sessions**: On a Mac, the Sessions tab lists one entry per Claude Code session. A single conversation opened in the Claude desktop app was showing up as five, one for each of the app's background processes. A session now also says whether it was opened in a terminal or in the desktop app.
- **sessions**: The scan trace says how many processes it looked at and how many of them were not sessions, so a short list comes with a reason.

## 1.29.40 (2026-09-14)

### Fixed

- **hooks**: The warning no longer comes back right after you repair the firewall. Blooby now checks that the connection actually works, instead of waiting for Claude Code to do something before believing the repair succeeded.
- **hooks**: After a repair, Blooby tells you whether it can now be reached, rather than leaving you to guess whether granting the administrator prompt served any purpose.

## 1.29.38 (2026-09-13)

### New

- **hooks**: When Claude Code is working but nothing reaches Blooby, Blooby now says so instead of looking healthy. If a Windows Firewall rule is what blocks it, Blooby names that rule and offers to remove it for you, in one click.

### Fixed

- **settings**: The note under the hooks badge now sits on its own line, across the full width, on a tinted background. It used to be squeezed into a narrow column in a pale orange that was hard to read.
- **settings**: When something is wrong, the message now reads on its own lines under the title, with its action button at the end, instead of being crammed beside the heading.
- **hooks**: Repairing the firewall now actually lets the hooks through. Blooby adds the permission it needs instead of only removing the rule that blocked it, which left Windows refusing the connection anyway.
- **hooks**: Blooby now tests the route from WSL before blaming the firewall, and tells you whether a rule is blocking it or whether nothing allows it in. It used to list possible causes without checking any of them.

## 1.28.34 (2026-09-12)

### New

- **settings**: The Dock tab now previews real mascots: you can see where they sit on screen for each of the twelve anchor points, and how the panel wraps around them at your chosen size and spacing.

### Fixed

- **tray**: The Blooby icon in the system tray is legible again at the size Windows actually draws it.
- **dock**: With the dock on the left or right edge, the bottom mascot and the bottom of the panel are no longer cut off. Each mascot was being pushed down a little further than the last.
- **dock**: A mascot whose artwork reaches beyond its frame, like Blooby Patron and its crown, is no longer clipped or crowded by its neighbour.
- **dock**: A mascot you do not own is drawn as Blooby, and the dock now reserves the room Blooby actually needs instead of the room the locked mascot would have taken.

## 1.27.30 (2026-09-06)

### New

- **hooks**: You can now tick more than one platform at once. A terminal session and a WSL one read different files, so if you work on both, both get mascots instead of you having to choose.
- **mascot**: When a project has several sessions running, its mascot now shows the one that needs you rather than whichever moved last, and clicking it takes you there. Right click to see every session of the project, each with its own state and a way to jump to it.

### Performance

- **sessions**: Blooby no longer runs a background shell every few seconds on Windows to see which sessions are alive.

### Fixed

- **sessions**: The Sessions tab lists your Windows sessions properly. It used to show ten of the Claude desktop app's background processes for one real session, and it now names the project each session is working in.
- **sessions**: A session card is readable again: the command line is folded away, and where the session runs (a terminal, the Claude desktop app, or a WSL distribution) is shown as a badge at the top.
- **sessions**: Closing a Claude session on Windows now removes its mascot, instead of leaving it on the dock until you restarted Blooby.
- **sessions**: Your mascots no longer disappear when Blooby cannot check on your sessions. A scan that was unable to look was being read as every session having ended.
- **sessions**: Two sessions in the same folder each show their own state in the Sessions tab, instead of both reporting the project's.
- **hooks**: Blooby no longer overwrites a Claude Code settings file it could not read, and the backup it keeps is the state of that file before Blooby ever touched it.
- **hooks**: Hooks are removed from the platform they were installed on when Blooby quits, instead of possibly cleaning a different one and leaving the first in place.
- **settings**: A platform you had ticked that is no longer on the machine can be unticked again, instead of leaving an error you had no way to clear.
- **settings**: Copy config now gives you the hook for the platform you are actually on.

## 1.25.20 (2026-09-05)

### New

- **hooks**: Settings now offers the platform you are actually on, macOS or Linux, alongside Windows and WSL, and installs a hook command those systems can run. Running Blooby outside Windows is new ground, so expect rough edges.
- **sessions**: The Sessions tab now looks for your live claude sessions on macOS, on Linux and on Windows itself, not only inside WSL. A session launched natively on Windows appears without a project, because Windows does not let one program read another's working directory.
- **settings**: When something is wrong, Blooby now tells you. Problems appear at the top of General, the hooks badge admits when it has never received a single event, and a Copy diagnostics button gathers everything worth pasting into a bug report.

### Fixed

- **hooks**: The hook command installed on Windows now parses under PowerShell, not just under Git Bash. Without Git Bash on the machine, PowerShell rejected it outright and no event ever reached Blooby.
- **hooks**: Blooby no longer rewrites a settings.json it could not parse. A stray comma in your Claude Code settings would previously see the file replaced with Blooby's own hooks, with only a backup left behind.
- **sessions**: Off Windows, a mascot could disappear on its own about fifteen seconds after appearing: the session scan reported nothing because it had not looked at anything, and that was read as the session having died.
- **sessions**: A Windows machine without WSL no longer reports a permanent error in the Sessions tab. Having no WSL is not a fault, and the tab now says which sources it tried instead.

## 1.22.16 (2026-09-02)

### New

- **sound**: Your mascots now speak. Each project has a note of its own, so when two sessions move at once you can hear which one it was: setting to work, finishing, asking for you, erroring, falling asleep, opening a subagent or ticking off a todo.
- **dock**: The dock now has a voice of its own when it slides out of the way and when it comes back.
- **settings**: A new Sound section in General switches sounds on or off and sets the volume, with a button to hear the level while you set it. A project you would rather not hear can be muted from its card in Projects.

## 1.19.16 (2026-08-28)

### New

- **settings**: Your account, credit balance and sign out now sit at the bottom of the Settings sidebar, so you can check your credits or switch account from any tab instead of only the Mascots one
- **settings**: Mascots now sits on its own button above the tabs, so the place you spend credits reads as a shop rather than as one more settings page
- **settings**: The Settings tabs are grouped now, with Projects and Sessions side by side, so the ones you use daily read in one glance
- **mascots**: Choosing a project's mascot now shows the creatures themselves: a searchable list of previews, both in Settings and when you right click a mascot
- **tray**: The tray menu is shorter now: your running sessions are no longer listed there (the dock already shows them all), and the update entry leads the menu, naming the version that is waiting
- **updater**: Checking for updates from the tray now tells you what it found, instead of answering into a menu you have already closed, and Blooby looks for a new version every hour rather than every six

### Fixed

- **settings**: The in-app help is tidy again: its close button sits in the corner where it belongs, and the text no longer runs over the panel's rounded edges
- **settings**: The in-app help now matches what Blooby actually does, with sections on the reworked Settings sidebar, the mascot shop and its credits, your projects, the tray menu and updates
- **tray**: Help in the tray menu now opens the help panel; before it only brought up Settings and left you on whichever tab you were reading

## 1.13.13 (2026-08-21)

### New

- **mascot**: Mascot animations now draw a fresh random value every time they start, so characters built to use it stop replaying the exact same sequence over and over

### Fixed

- **mascot**: Mascots that pair a body animation with a particle effect now keep the two in step, so an effect no longer fires without the movement that triggers it

## 1.12.12 (2026-08-17)

### Fixed

- **hooks**: Your mascots now react when Claude Code runs inside WSL, whatever your WSL network setup; before, this only worked if you had switched WSL to mirrored networking, and it failed silently otherwise

## 1.12.11 (2026-08-16)

### New

- **mascot**: Your mascot now shows how many Claude sessions and subagents are running on a project, alongside the open-task count, all in one small badge under its feet

### Fixed

- **mascot**: Your mascot no longer stays awake forever when a subagent ends without notice; it dozes off as it should

## 1.11.10 (2026-08-15)

### Fixed

- **mascots**: Your collection now lists the packs in the right order, the same one the site uses

## 1.11.9 (2026-08-14)

### New

- **mascots**: Mascots are now unlocked one at a time with credits instead of by pack. Every mascot shows its own price, so you only pay for the ones you actually want
- **mascots**: You can now spend your credits without leaving Blooby: click the price on a locked mascot, confirm, and it is yours and ready to use straight away. Buying credits still happens on blooby.me
- **account**: Your credit balance now sits next to your account in Settings, with a shortcut to top up

### Fixed

- **dock**: Mascots you unlock while Blooby is running now reach your dock right away, instead of staying on Blooby until the next restart
- **mascots**: A brand new project is no longer given a mascot you do not own

## 1.8.7 (2026-07-30)

### New

- **sessions**: A new Sessions tab lists every live Claude Code session on your machine, with its project, how long it's been running and how long since its last message; you can jump to a session's terminal or stop it, and sessions Blooby isn't receiving events for are flagged
- **sessions**: Your mascots now track your real sessions: they appear as soon as Blooby starts (even for sessions already running) and vanish on their own when a session ends or crashes, instead of lingering asleep
- **dock**: You can auto-hide mascots for sessions that have been idle for a while (Settings, General, Idle & sleep), so the dock only shows what you're working on now

## 1.5.7 (2026-07-26)

### Fixed

- **dock**: The dock no longer occasionally slips behind other windows; it now reliably stays on top, even after a fullscreen app or a remote session takes over
- **stats**: The Statistics tab now updates live while it's open, instead of only refreshing when you switch tabs
- **dock**: Switching a project's mascot now re-spaces the dock right away, instead of leaving the old spacing until something else refreshes it

## 1.5.4 (2026-07-25)

### New

- **mascot**: Your mascots now track more of what Claude Code is doing (permission prompts, MCP input requests, context compaction, errors, subagents) and stay in sync more reliably
- **stats**: A new Statistics tab in Settings shows how often each Claude Code event has fired, overall and per project

### Fixed

- **mascot**: Your mascot no longer gets stuck or flips to the wrong state while Claude Code is compacting its context

## 1.3.3 (2026-07-21)

### New

- **mascot**: The Mascots gallery now previews each mascot with your outline and eye-blink settings applied

## 1.2.3 (2026-07-19)

### New

- **mascot**: You can now turn off the white outline around your mascots (body and accent bubbles) from Settings > General

### Fixed

- **mascot**: Mascot outlines look crisper and keep an even thickness at every size

## 1.1.2 (2026-07-18)

### New

- **mascot**: Some animations can vary from one trigger to the next

### Fixed

- **mascot**: Some mascots now show their accent bubbles on the right activity states instead of hiding every accent

## 1.0.1 (2026-07-14)

### Fixed

- **popover**: The right-click mascot panel now matches the theme you picked in Settings

## 1.0.0 (2026-07-13)

### New

- Initial release
