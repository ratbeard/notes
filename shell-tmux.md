
`[d]` indicates a shortcut of `prefix d`.  
My prefix - 
Wefault prefix - `ctrl+b`

Sessions

		tmux new -s fun     						# new session
		tmux ls													# list sessions
		tmux a -t fun										# attach to session.  Last used if no -t.
		tmux detach 	 					 				# [d] detach from session
		tmux kill-session -t fun 				# kill session


Windows (tabs)

		tmux new-window									# [c] new window
		tmux list-windows								# list windows
		tmux select-window -t :0-9      # [0-9] switch to window
		tmux rename-window cool					# [,] rename current window

Panes

		tmux split-window						# ["] vertical split
		tmux split-window -h				# [%] horizontal split
		tmux swap-pane -[UD]				# [{ or }] move pane
		tmux select-pane -[UDLR]		# select pane
		tmux kill-pane							# [x]
		tmux select-pane -L					# [left,right,up,down]
		tmux resize-pane -L					# [meta+left,right,up,down]

Info
	
		tmux list-keys
		tmux list-commands
		tmux info
		tmux source ~/.tmux.conf


http://www.drbunsen.org/the-text-triumvirate/#tmux
[1]: http://robots.thoughtbot.com/post/2641409235/a-tmux-crash-course "Good Intro"
[2]: http://www.drbunsen.org/the-text-triumvirate/#tmux "Setup, clipboard, Powerline config"

