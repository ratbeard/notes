2014-02-22
==========
Installed tabularize vim plugin.  Type `Tab` in visual mode, or in normal: `:Tab /=`

Setting up some vim snippets.
`_` is global snippets

2014-02-22
==========
!publish
Making lots of edits to your gulpfile?  Add this task so you can run `gulp` with nodemon:

		# Hack to be able to run gulp under nodemon via:  nodemon --exec gulp gulpfile.coffee
		task "gulpfile.coffee", ['development']

!doc(sh)
To have less like tail -f

		less +F file

!check
Angular style guides:
- Not too much useful, mainly relating to closure compiling.  Interesting, always prefer controller as syntax, I'm kind of leaning that way myself
	https://google-styleguide.googlecode.com/svn/trunk/angularjs-google-style.html
- Good.  Limit events to app-wide things.  Use directive controllers to communicate between directives.  Break app components into modules.
	https://github.com/angular/angular.js/wiki/Best-Practices
- Directory structure / file naming.  Name file after type of thing in it.
  https://docs.google.com/document/d/1XXMvReO8-Awi1EZXAXS4PzDzdNvV6pGcuaF4Q9821Es/pub
- http://briantford.com/blog/huuuuuge-angular-apps.html

2014-02-20
==========


2014-02-19
==========
- You don't need to `$().off()` registered events in an angular directive,
	`$().remove()` handles removing them for you (though the native DOM function
	doesn't).  Since angular uses `$().remove()`, sa'll good.

- gulp seems to not be able to handle dependency trees.  Using a sync rmrf
	function seems to get around it in my case.
- zsh sets `bindkey -v` (vim mode) automatically based on your $EDITOR.  It
	doesn't have ctrl+r configured!  Real tricky tracking down as EDITOR was only
	being set the second time the zshrc was loaded, which `rbenv init` was doing
	on my laptop, but not my work computer.
- zsh `path` variable is an array and a lot nicer to work with than $PATH.
- `vw` and `vh` units in css are pretty buggy in ios atm (I read)

2014-02-18
==========
- `<input autofocus>` sets focus on page load, OR when the element is inserted into the DOM.
- Coffee watch deletes .js files when the .coffee file is deleted.  `coffee -cw src -o dest`
- osx's sed is POSIX compliant, and sucks (\t, \s no work).  To replace leading spaces in a file:

		sed -i -E "s/^[[:space:]]*//"

- You can't replace a file with std redirection, e.g. `tr "a" "b" < $1 > $1`.
	Need a temporary file.

2014-02-14
==========
Tweaking that config:

- Install visor for a seperate system-wide HUD terminal.  Useful for always having ~/notes open in vim, etc
  It extends Terminal.app, ctrl+ctrl to toggle it when focused.  I set it to run terminal in the background
	so it doesn't show in the cmd+tab list.
- Set hotkeys:
  - cmd+opt+shift+3 - terminal (visor)
	- cmd+opt+5 - itunes
	- cmd+opt+shift+5 - sonos
	- cmd+opt+0 - activity monitor
	- cmd+opt+shift+0 - system preferences
- Changed prompt to just the cwd in zsh config.  You send an escape sequence to
	tell the terminal program to set the title.  The string is formatted to
	expand with certain variables.  Man this thing is too slow and complicated, I
	gotta tweak it!
- Turn off rbenv on startup, soo much faster to launch a terminal session.  eval "$(rbenv init -)"
- aliased `gll` to the advanced logging prompt.  Add `glp` to `git log -p`


Most buffer overflow attacks exploit string or array handing code that misses a
length check, and overwrite the return address pointer.  A way to prevent these
attacks is to insert a random integer before the return address on the stack,
and check that this 'canary value' hasn't changed when the function returns.
Turning this on for all functions is unnecisary, a heuristic of only enabling
for functions use char arrays larger than 8 bytes on the stack has been
expanded by the chrome OS team at google to target other attacks such as
functions using arrays inside structs, local register variables, or access a
local variables address.
http://lwn.net/Articles/584225/


There are no plans to make the `node_modules` file name configurable.  Assuming
a hardcoded name allows npm to not be required at run time is the main reason.
https://www.npmjs.org/doc/faq.html#node_modules-is-the-name-of-my-deity-s-arch-rival-and-a-Forbidden-Word-in-my-religion-Can-I-configure-npm-to-use-a-different-folder


