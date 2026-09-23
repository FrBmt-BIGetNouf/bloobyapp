<div align="center">

<img src="https://blooby.me/media/github/logo.png" alt="Blooby" width="344">

### Your Claude Code sessions, as creatures that live on the edge of your screen.

Every project you run Claude Code in gets a small animated familiar.
It works when the agent works.
It looks up at you when the agent needs a permission.
It falls asleep when you walk away.

[![Download](https://img.shields.io/badge/Download-blooby.me-4f7cff?style=for-the-badge)](https://blooby.me/download)
&nbsp;
[![Platforms](https://img.shields.io/badge/Windows%20%7C%20macOS-333?style=for-the-badge)](#platform-support)

[Website](https://blooby.me) &nbsp;·&nbsp; [Changelog](./CHANGELOG.md) &nbsp;·&nbsp; [Report a bug](https://github.com/FrBmt-BIGetNouf/bloobyapp/issues/new/choose)

<img src="https://blooby.me/media/github/hero.gif" alt="Five Claude Code sessions, each with its own mascot, each in a different state" width="800">

</div>

---

## Why

You start Claude Code, you go read something else, and you come back to find it has spent most of that time waiting for you to approve a single file write.

With three projects open at once it gets worse: something wants you, and you have no idea which window it is in.

Blooby puts that where you cannot miss it.
A row of creatures along the edge of your screen, one per project, each animated according to what its agent is doing right now.

<img src="https://blooby.me/media/github/permission.gif" alt="A session stops on a permission prompt and its mascot looks up" width="800">

## What a mascot tells you

One mascot is one **project**, not one session.
Three Claude Code sessions in the same repository share a creature, and it shows you whichever state needs you most.

| Two creatures, one state | | |
|:--:|---|---|
| <img src="https://blooby.me/media/github/state-working.gif" alt="working" width="72" height="72"> <img src="https://blooby.me/media/github/state-working-alt.gif" alt="" width="72" height="72"> | **Working** | Running tools, editing, thinking |
| <img src="https://blooby.me/media/github/state-waiting.gif" alt="waiting" width="72" height="72"> <img src="https://blooby.me/media/github/state-waiting-alt.gif" alt="" width="72" height="72"> | **Waiting on you** | Stopped on a permission, or on a question it needs answered |
| <img src="https://blooby.me/media/github/state-idle.gif" alt="idle" width="72" height="72"> <img src="https://blooby.me/media/github/state-idle-alt.gif" alt="" width="72" height="72"> | **Idle** | Done, and waiting for your next instruction |
| <img src="https://blooby.me/media/github/state-done.gif" alt="done" width="72" height="72"> <img src="https://blooby.me/media/github/state-done-alt.gif" alt="" width="72" height="72"> | **Done** | It just finished something |
| <img src="https://blooby.me/media/github/state-compacting.gif" alt="compacting" width="72" height="72"> <img src="https://blooby.me/media/github/state-compacting-alt.gif" alt="" width="72" height="72"> | **Compacting** | Folding the conversation down to make room |
| <img src="https://blooby.me/media/github/state-error.gif" alt="error" width="72" height="72"> <img src="https://blooby.me/media/github/state-error-alt.gif" alt="" width="72" height="72"> | **Error** | Something failed |
| <img src="https://blooby.me/media/github/state-asleep.gif" alt="asleep" width="72" height="72"> <img src="https://blooby.me/media/github/state-asleep-alt.gif" alt="" width="72" height="72"> | **Asleep** | Nothing has happened there for a while |

Click a mascot and the terminal that owns the session comes back to the front.
Right click it to rename the project, swap the creature or tint it.
Drag it to reorder the row.

## The roster

Creatures come in packs: animals, food, things off your desk, gym gear, the solar system, tech, fantasy.
There is also a dragon that hatches and grows through eight stages as you bring other people in.
New packs land regularly.

<img src="https://blooby.me/media/github/roster.gif" alt="A grid of mascots, each on its own colour" width="1000">

Each one is vector art animated in pure CSS, so it stays sharp at any size and costs your machine close to nothing to run.

Plenty of them are free and need no account at all.
The rest unlock one at a time.
Every paid pack has one mascot given away at its head, so you can always see what a pack looks like before paying for anything in it.

## How it works

Claude Code can announce what it is doing.
Blooby sets that up for you the first time it starts, listens locally, and moves the right creature.
There is nothing to configure and nothing to keep in sync.

It is a native app rather than a browser in a costume, so a row of mascots costs you a few megabytes, not a few hundred.

And if you run Claude Code inside **WSL** while Blooby runs on Windows, that works too, in both mirrored and NAT networking, with no `.wslconfig` to edit.
Your Windows and WSL sessions share the same dock.

<details>
<summary><b>What it does to your machine, precisely</b></summary>

<br>

Blooby watches Claude Code through its hooks, which means it adds a few entries to your Claude Code settings and listens on a local port. Both of those deserve a straight answer.

- **It only listens.** Blooby answers every event and has no say in what Claude Code does next. It cannot approve, block or delay a tool call, and it is not able to.
- **It cannot get in your way.** Each hook call is capped at two seconds and swallows its own failure, so when Blooby is closed or busy, Claude Code carries on without ever seeing an error.
- **It does not trample your settings.** Its hooks are merged into your existing `~/.claude/settings.json`, the original is backed up before anything is written, and if that file has a syntax error Blooby refuses to touch it rather than risk your permissions and MCP config.
- **It cleans up after itself.** The hooks go in when Blooby starts and come back out when you quit it, so your settings are not left littered with something you are not running.
- **Nothing is exposed.** The listener is bound to loopback and never to `0.0.0.0`, so nothing else on your network can reach it.
- **Your sessions stay yours.** Blooby contacts `blooby.me` for two things only: fetching a creature's artwork the first time you use it, and syncing your collection if you choose to sign in.

</details>

## Install

1. [Download Blooby](https://blooby.me/download) and run the installer.
2. Launch it. It sets up its hooks and sits in the tray.
3. Run `claude` anywhere. A creature appears. Sessions you already had open are picked up too.

<img src="https://blooby.me/media/github/install.gif" alt="Blooby is launched from the desktop, and the mascot of the session already running appears" width="800">

**You need** Claude Code, and `curl` wherever `claude` runs (it already ships with Windows 10, Windows 11 and macOS).
On Windows you also need WebView2, which is already installed on Windows 10 and 11.
You need a connection the first time, to fetch the artwork. After that Blooby works offline.

> **On macOS**, the first launch is refused: Blooby is signed, but not yet notarized by Apple.
> Open **System Settings > Privacy & Security**, find the message about Blooby and click **Open Anyway**.
> You only have to do this once.

## Making it yours

- **Where it sits.** Twelve anchor points: any of the four screen edges, aligned to the start, the middle or the end.
- **How big.** Half size up to double size.
- **A panel behind the row**, if you want it to read as one object: background, border, corner radius, padding, and an optional gap from the screen edge.
- **Sound.** Every cue is synthesized live rather than played from a file, and each creature has its own note, so you can hear *which* one just finished. Adjustable, or off entirely, and mutable per project.
- **Sleep.** How long before a mascot goes idle, how long before it sleeps, whether sleeping mascots hide themselves, and whether they eventually leave the dock altogether.
- **A global shortcut** to hide and show the whole dock at once.
- **Launch at startup**, optionally with the dock already hidden.

It also does three things you will only notice by their absence.
It never steals focus from your editor.
Your clicks pass straight through it everywhere except on a mascot itself.
And it stays on top without ever fighting your other windows for it.

## Beyond the dock

- **Sessions.** Every live Claude Code session on the machine, including the ones not reporting to Blooby, with its project, uptime, how long it has been idle and where it was started from. Jump to one, or kill it.
- **Statistics.** A live count of every kind of Claude Code event, overall and per project. A fairly honest picture of how you actually work.
- **Updates.** Blooby updates itself from a signed manifest, one click from the tray.

## Platform support

| Platform | Support |
|---|---|
| **Windows 10 and 11** | Fully supported. This is what Blooby is built for. |
| **macOS**, Apple Silicon and Intel | Published as a universal app. The mascots, the tray, the settings and the sounds all work. A few dock interactions are still Windows only: clicking a mascot, hovering it, and jumping back to its terminal. Not yet notarized, so the first launch takes one extra step. |
| **Linux** | Builds, but is neither published nor tested. |

## Getting help

- Something is broken: [open an issue](https://github.com/FrBmt-BIGetNouf/bloobyapp/issues/new/choose).
- An idea, or a creature you want to see added: same place, there is a template for each.
- A security problem: [SECURITY.md](./SECURITY.md), and please not a public issue.

If Blooby is running but no creature appears, open Settings.
The hooks section tells you exactly where it is stuck, and on Windows it can repair a blocking firewall rule for you in one click.

## About

Blooby is made by [BIG et Nouf](https://blooby.me).

This repository is the app's public home: its README, its changelog and its issue tracker.
The source code is not published. See [LICENSE](./LICENSE).

Blooby is an independent project.
It is not affiliated with, endorsed by, or sponsored by Anthropic.
