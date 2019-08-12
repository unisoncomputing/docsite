# Three-minute quickstart guide

This short guide will have you downloading and installing Unison and running your first program (a toy distributed mergesort implementation). There isn't much exposition here and the focus is on getting you up and running as quickly as possible. 🏎 

More in-depth guides follow this one.

If you have any trouble with the process, or have ideas about how to improve this document, [come talk to us in the #alphatesting Slack channel][slack]! Also this document is [on GitHub][on-github].

[slack]: https://join.slack.com/t/unisonlanguage/shared_invite/enQtNzAyMTQ4ODA0MDM4LWYxZTNkMGUxMDEzNTg3NTMxNjMxOGM2Zjg4ODFjM2RhNGY0OGU2NTMzYmQ1YWIwN2Y0YTc1NjQ1NjgzYzEzOWI
[mac-dl]: https://github.com/unisonweb/unison/releases/download/release%2FM1c/unison-osx.tar.gz
[linux-dl]: https://github.com/unisonweb/unison/releases/download/release%2FM1c/unison-linux64.tar.gz
[windows-dl]: todo
[on-github]: https://github.com/unisonweb/docsite/edit/gh-pages/_includes/quickstart.markdown
[guide]: unisontour.html
[homebrew]: https://brew.sh/

### Step 1: Install Unison

Note: This alpha release is for Mac OS X and 64-bit Linux only. Windows users, there will be a Unison release for you some day soon.

#### Option 1: Using Nix (OSX & linux)

First [install nix]: https://nixos.org/nix/manual/#ch-installing-binary if you haven't already.

Then, from the command line, enter or paste this command:
```
nix-env -i unison-ucm
```

This will install the Unison codebase manager executable `ucm`.  As new versions are released and the package is updated, repeating the above command will update the install.

#### Option 2: Using Homebrew

First [install homebrew][homebrew] if you haven't already.

Then from the command line enter these commands (or better yet, paste them into your console):

```
brew tap unisonweb/unison
brew install unison-language
```

This will install the Unison codebase manager executable `ucm`. If you're upgrading from a previous version, just do `brew upgrade unison-language`.

Note: if you get prompted for a GitHub username and password at this point, make sure you spelled `unisonweb/unison` correctly.

#### Option 3: Install manually

Download the Unison tarball for [Mac][mac-dl] or [Linux][linux-dl], decompress the tarball to find the delicious `ucm` binary inside, and then optionally copy or link `ucm` somewhere on your path.

### Step 2: Create your Unison codebase

Create a new directory, `unisoncode` (or any name you choose), then run the `ucm` binary from within that directory. You'll see a note about "No codebase exists here so I'm initializing one..." and a welcome screen.
<script id="asciicast-dvwP7oXFwf0qwQWds1ShFXMP8" src="https://asciinema.org/a/dvwP7oXFwf0qwQWds1ShFXMP8.js" data-speed="1.4" data-cols="65" async></script>

### Step 3: Fetch and run a distributed mergesort example

__Prerequisites for this step:__ you'll need to have Git installed and on your path.

At the Unison `.>` prompt, before doing anything else, do:

```
.> pull https://github.com/unisonweb/unisonbase.git
``` 

to fetch a base library with the first example. You'll see some output from `git` in the background, and once that's done you can do:

```
.> edit quickstart.dsort
```

to add the `dsort` distributed mergesort function to the top of a newly created _scratch file_, `scratch.u`:

<script id="asciicast-o9lfrfetnmUT4ArqdDFMXZkr9" src="https://asciinema.org/a/o9lfrfetnmUT4ArqdDFMXZkr9.js" data-speed="1.4" data-rows="30" data-cols="65" async></script>

Open that file and add the following _watch expression_ (a line starting with `>`) to the top, then save the file:

```
> runLocal '(quickstart.dsort (<) [8,2,3,1,4,5,6,7])
```

<script id="asciicast-aTn8qIa3DHaxhspsZJmXodfO7" src="https://asciinema.org/a/aTn8qIa3DHaxhspsZJmXodfO7.js" data-speed="1.4" data-t="1.5" data-autoplay="0" async></script>

You should see your watch expression evaluate to a sorted list. You are now up and running!

_Disclaimer:_ This example is a toy that simulates execution locally and does no error handling. It's just meant to be suggestive of the general idea of being able to test Unison distributed programs locally (perhaps with simulated latency and failures injected) and then run them unchanged atop an actual elastic source of distributed compute. This _will_ be something you'll be able to do in Unison in not too long (see [the roadmap](roadmap.html)).

### What next?

* Come [say hello in Slack][slack], tell us what you thought about this guide, and ask questions. 👋
* A [more leisurely guide][guide] to the Unison language and the `ucm` command line tool. (25 minutes)
