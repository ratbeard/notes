# learn

## angular

http://www.thinkster.io/pick/GUIDJbpIie/angularjs-tutorial-learn-to-build-modern-web-apps
	fantasy football example

http://egghead.io/

## docker / deployment

http://coreos.com/
https://github.com/flynn/flynn-spec
http://www.packer.io/
http://blog.scoutapp.com/articles/2013/08/28/docker-git-for-deployment

https://github.com/chovy/node-startup
https://github.com/cvee/node-upstart
	nodejs init.d scripts
	also, forever npm

## grunt

http://www.brianchu.com/blog/2013/07/11/grunt-by-example-a-tutorial-for-javascripts-task-runner/
http://blog.ideahaven.co/post/56446899047/seed-repo-angular-bootstrap-coffee-script-d3
	starter app repo
https://github.com/blai/grunt-express
	meh
http://newtriks.com/2013/06/11/automating-angularjs-with-yeoman-grunt-and-bower/
http://briantford.com/blog/angular-express.html

## d3

https://github.com/mbostock/d3/wiki/Gallery
	tons of examples
https://github.com/mbostock/d3/wiki/API-Reference
	api
http://bl.ocks.org/mbostock/6123708
	drag and zoom
http://www.danielepennati.com/d3/linea2.html

## vim

http://yannesposito.com/Scratch/en/blog/Learn-Vim-Progressively/
http://rayninfo.co.uk/vimtips.html

## tmux

https://gist.github.com/MohamedAlaa/2961058
	cheatsheet

https://gist.github.com/simme/1297707
	mouse

http://www.drbunsen.org/the-text-triumvirate/#tmux
	tips


# watch

http://www.infoq.com/presentations/HTTP-Performance?utm_source=infoq&utm_medium=videos_homepage&utm_campaign=videos_row2
	pushing bits is a solved problem, http delivery performance is a solved problem for the near term.  For the long term, a different protocol will be needed.
	idea - framework to analyze rendered html, after the fact (use case - see if served a page with broken links,
	see how much I sent, see user agent?, 
	Encypt only sensitive parts of message - reveal address but nothing else
	Can not route 1TB/sec.  Probably won't get much better in the future unless we burn http into the chip (interesting idea - hard to do fpga program for non-fixed length fields).
	Cookies are bad idea - store sensitivish data in untrusted platform.  can't cache w/ it has cookie since you dont know what it means.  hashed to large string that cant be compressed.
		Should be - client sends id to server, so their in (better) control .  Many cookies on pub lib computer - fun to play with.  Facebook saves massive storage by having client store cookies.  Helps with problem of sharing settings between devices.

	3 unpleasant facts about privacy
			Legislation trumps privacy - in UK, if you get arrested and can't tell password to unencrypt file, can be jailed two years and rereviewed.
			Not all people have privacy - children, prisoners, criminals, employees (no unconditional - http check for outgoing docs), foreigners
			Android stock app has full system acess can't be disabled.  If its not a backdoor, it better not have any exploits

	Use same connection for http{,s}
	Snowden had full access to all computers NSA had access to. Criminal botnets - 300,000 to 1mil - attack rarely.  
	Help prevent DOS - make client do more work than server.  Have server send to challenege for new conection (only turned on when under attack).  useful for spam email prevention.  Need to design protocols to handle bad guys (http was designed that only good guys).
	IP6 solved wrong problem - what a NAT gateway can do.  Didn't give multihoming (multiple isps)
	http/20 solving wrong problems - major focus compress headers, multiplexing/pipelining, server push.  Will be much easier to DoS, doesn't solve root speed issue.
	Will be okay for about 5 years for the big sites (bandwidth grows 140% year).
	http2 - criteria was set to develop protocol + test impl in 3 months - noone but speedy could do.
	Varnish cannot do ssl better than nginx so doesn't implement it.
	Didn't get his last answer on political vs encryption - seems like he ignored actual benefits (today), not hypothetical

http://www.youtube.com/watch?v=Te17gy4vPN4#t=48
	Computers do not look like cpu <-> ram <-> disk.
	cpu cors w/ caches <-> Virtual Page Cache (formerly cache) <-> remote object storage
	memory widths - 128bits today.  Lose 1000's instructions for locking, etc.
	Reading statistics doesn't affect its running - shared memory
	125K different user agents seen on a server - don't vary: it!
	<esi includes> - cache different parts of page on different lifetimes
	can splice together compressed chunks for esi by laying out gzip file cleverly
	No ssl - add 500% more code for barely better than what pound could do.

http://queue.acm.org/detail.cfm?id=2349257
	influx of IT prof from dotcom error has led to poor technical quality.  
	autconf tests for many things not relevant for 20 years




https://www.varnish-cache.org/trac/wiki/ArchitectNotes
https://news.ycombinator.com/item?id=6354396
http://queue.acm.org/detail.cfm?id=1814327
http://www.amazon.com/The-Design-Essays-Computer-Scientist/dp/0201362988
http://oldblog.antirez.com/post/what-is-wrong-with-2006-programming.html
