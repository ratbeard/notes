http://mechanical-sympathy.blogspot.com/2013/02/cpu-cache-flushing-fallacy.html
CPU caches don't "flush".
...


http://martinfowler.com/articles/lmax.html
lmax "disuptor" architecture for real time trading.

Ring buffer data structure - lock free way for producers/consumers to
maintain something queue-like.  Used in router.  Actor model had too
much overhead in queue locks.

Uses RAM with multiple machines to provide redundancy.  1 is master
at a time.

Single-threaded domain logic processor. Gets fed tasks from a pool of
input disruptors, sends results to output disruptors.  If decision
requires external call, send an outgoing event and will get a new
input event with the result in the future.



http://highscalability.com/blog/2013/5/13/the-secret-to-10-million-concurrent-connections-the-kernel-i.html
C10M - 10 million concurrent connection problem.
Separate control and data planes.  Data plane - packet handling - should be done outside of kernel.

Comment saying they achieved 10M websocket connections w/ an unmodified kernel.



http://lwn.net/Articles/476263/
XFS: the filesystem of the future
Used for huge data sizes.
Slower on small files, writing metadata.
Some data stability issues in the comments.
Fierce debate about fsync handling in comments.  Developers used to ext3's bad performance w/ fsync and relying on rename being an atomica operation.  Do new FS need to honor that even though not required by POSIX?  At least they should acknowledge it and explain the tradeoffs.


http://lwn.net/Articles/531381/
Namesspaces in operation pt 2 - the namespace api


http://www.toptal.com/java/the-trie-a-neglected-data-structure
Trie - neglected data structure

Organize data in tree structure based on pieces of your "word".
Works well for strings and language as many words share common
prefixes.  Each leaf indicates letter, and if it terminates in a
valid word.  Fast lookup and fast 'quit' if prefix becomes invalid
and not worth continued checking.

More memory requirements than trees/hash as each letter needs to
store a pointer, much larger than a char.



http://www.infoq.com/articles/story-cards-limit-agility
Write story cards direct from the user, or adopt a "We believe ..." stance, along with a "To verify we will...".
