
# 2014-03-11

To search through all content in the chrome inspector:

		cmd+option+f

Redirect stderr to stdout:

		echo hi 2>&1

To edit crontab:

		crontab -e

# 2014-03-10

In less, you can half page up/down w/ just `u` and `d`, no ctrl required.

Raspi temperature demo at MadJS by no0:

1 wire
avahi-daemon raspberry pi - find pi's on network
sparkfun.com
adafruit.com
alliedelec.com
maximimintegrated.com

# 2014-03-10

To exit a stalled ssh session press `Enter ~ .`


# 2014-03-09

git push assumes id_rsa key.

sudo lxc-attach -n <containerid>

lsb_release -a
See ubuntu version

"Cat cut your tongue"

Credit cards

Visa and Mastercard use an older, more open, transaction system. Discover and Amex are newer and process the transations themselves, charging more, ~half the adoption in stores.
1 point = 1 mile = 1 cent.
Cards with an anual fee tend to waive it the first year.
Airlines have their own miles which give a much better benifet.  Some cards let you tranfer generic miles to airline miles for a specific ticket, getting much better deal.

Specific airline cards like Visa Delta gold have gotten worse over times, as
airlines' benifets and miles have gotten worse.  Tied to just that airline.
Looks like the companion $100 ticket deal ended as well.  The main benefit
is getting good perks like priority boarding, $200 checked bag credit, etc.

Amex Blue Cash Everyday
6% on groceries, 3% on gas, makes it best for non travelers.  Accepted at
costco?

Chase Saphire Premium
best intro bonus 45,000 miles
Great customer support
Generic miles that can move miles to specific airlines to get much better usage
get bonus back when using miles and each year
$95/year.  Theres also a free version w/ worse benifits
Got this one!

Capital One Venture
Similar to CSP, but earns 2x points on *everything*.
Airline miles aren't as flexible though.
Harder to get, worse customer service.

Barclaycar Arrival World MasterCard
best of both worlds - 2x on everything, 40,000 intro bonus
Can't move miles around though which is where big savings are


# 2014-03-06
Reactive Programing
http://www.infoq.com/presentations/reactive-programming-netflix?utm_source=infoq&utm_medium=videos_homepage&utm_campaign=videos_row2

Treat an event source like a collection.
Advantages: Composable, retry(), timeout(), are easy.
Autocomplete example is good.
Visualizing time w/ async events slides is good.



# 2014-03-05
Old vim notes:

		[I				show current word in all files
		^]				goto definition
		:vne <name>		new file in vertical split
		^w r			move pane right
		:!date 		run external command
		:.!date 	and insert as text
		ZZ				close file
		:g/div 		yank all lines w/ div into a buffer
		g;				jump to last change
		:cd %:h		change pwd to current file 
		gqq				format 80 chars
		'         jump to last edit
		`
    :.,64d		delete current to 64
		guu				lowercase line
		^O        retrace steps
		^I				

Global replace:

		:args **/*.coffee
		:argdo :%s/foo/bar/ge | up


2014-03-05
==========
Installed htop, its sweet.

		# Snaggle on install.  brew gives great debugging help:
		brew link --replace automake 
		brew install htop


To ping microsoft.com, since they drop ICMP packets:

		nmap -p 80 microsoft.com

2014-03-04
==========
Installed httpie, its sweet.  Didn't work on my linux laptop :(

		# Apparently I should have done: sudo instal pip; pip install httpie
		sudo easy_install httpie

		# Adds json content type header, assumes localhost by defaul
		http --json :7777

		# Upload an image simulating an html form
		http -f POST :7777 name="pema" image@pema.png

2014-03-01
==========
## TotalSpace2
In overviewmode mode, hold shift when hovered over a screen to blow it up.
In overviewmode mode, hold alt when dragging to place window in same position in new screen.
Just switched this behavior:

		defaults write com.binaryage.TotalSpaces2 placeWindowsAsDroppedByDefault NO
		
Changed the menu icon color:

		defaults write com.binaryage.TotalSpaces2 menuBarIconColor "094be5"

## Bower
Bower has a bower.json file like package.json

		bower init
		bower install angular --save
		bower list --main  # show main entry scripts

Theres a gulp package to build a src from you main entry scripts:

		bowerFiles = require("gulp-bower-files")
		bowerFiles().pipe(gulp.dest("build"))

2014-02-28
==========
Jasmine watch syntax:

		jasmine-node spec --autotest --coffee --watch lib

Jasmine debug:

		node debug node_modules/jasmine-node/lib/jasmine-node/cli.js --coffee spec

2014-02-27
==========
Configured ,P to clear ctrlp cache in vim, since F5 key on my linux laptop doesn't work.

2014-02-23
==========

## Debug a nodejs process

Builtin command line debugger:

		node debug cool.js

		# Useful commands:
		repl, list(9), cb(10), n, c

Get fancy with `node-debug` using a web inspector GUI 

		npm install -g node-debug
		node-debug cool.js

Attach to an existing process:

		# Start a inspector server process
		node-inspector

		# Run your app w/ debug flag in another window:
		node --debug cool.js

		# OR attach to a running node process
		pgrep -l node
		kill -s USR1 <pid>


Find a pid by name:

		pgrep -l node
		

Setup vim-snippets.
Theres a couple different snippet engines, using vim-snippet.  It simply looks
inside folders named `snippets` in your rtp (vim path).  `_.snippets` are global.
I forked the repo as these sorts of things should be heavily customized I.M.OHHH.
It was a little tricky to get Vundle setup to use a local repo as I don't want to
push/pull constantly, still a few kinks to work out.  Need to use an absolute path,
wasn't able to get local git repo to work :(

		Bundle 'file:///Users/admin/code/vim-snippets'

After editing a snippets file, to gain access need to:

- commit in the snippets repo
- run `:BundleInstall!`.  Don't see a way to only refresh a single plugin :(
- reload? I forget

Mirroring placeholders seems broken, looking at `req` in the coffee snippet file.


Installed tabularize vim plugin.  Type `Tab` in visual mode, or in normal: `:Tab /=`


## Gulp

gulpif seems broken.  TODO make a bug...
uglify is so schlow
my nodemon was pretty out of date, not supports nodemon.json and exclude files list
karma is slamming.  gulp-karma doesn't pass along `files` option, instead files
should be streamed in `src` to it.

## stream-adventure

Finished node's `stream-adventure` today:

		stream-adventure                      # list files
		stream-adventure verify program.js    # check answer
		stream-adventure run program.js       # debug program

## vim-gist

		:Gist         # Gists whole file.  Can select in visual mode.
		:Gist -a      # anonymous
		:Gist -p      # private
		:Gist -l      # list your gists

I configured it to open browser after posting.
Pretty cool you can pull down and manage gists.  Requires investigation

## run local irc server

Methinks it will be faster to dev node bots connecting to a local irc server.

		brew install ngircd irssi
		ngircd
		irssi -c localhost

Hmm, works but can't use in limechat w/o some dns'n methinks.
How do I see whos in an irc room!?

http://blog.tremily.us/posts/Local_IRC_server/

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


