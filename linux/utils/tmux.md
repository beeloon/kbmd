# tmux
In Tmux, you will be working with sessions, windows and panes.
 - Sessions define the general task at hand. For example, if you are testing something, stick to a single session for all activities related to your test.
 - Windows are for specific activities or projects within a session.
 - Panes help you create multiple views within one window. For example, you might be working something in one pane, and using the other to track error logs.

Your system may not have a tmux.conf file by default. To create custom changes for a single user, create the file in the user’s home directory ~/.tmux.conf.  To create system-wide changes, create the file in the system directory /etc/tmux.conf.

## Keybindings
### Panes
| Command          | Action                                                                  |
| ---------------- | ----------------------------------------------------------------------- |
| ctrl + b %       | create new pane                                                         |
| ctrl + b o       | create new pane                                                         |
| ctrl + b ←/→     | switch between panes                                                    |
| ctrl + b q [0-9] | will display the numbers, then quickly pressing 1 will switch to pane 1 |

### Windows

| Command               | Action                                                               |
| --------------------- | -------------------------------------------------------------------- |
| ctrl + b c            | create new window                                                    |
| ctrl + b ,            | rename window                                                        |
| ctrl + b , [p/n]      | switch to previous/next window                                       |
| ctrl + b $window_name | change between windows, as example $window_name might be from 0 to 9 |
| ctrl + b w            | display an interactive list of windows                               |
| ctrl + b &            | close window (or type exit command)                                  |


### Sessions
[ctrl + b, d] - detach session from 
```bash
# list all sessions
tmux ls

# start a new name session
tmux new -s $session_name

# attach to session, with $session_name (see in ls command)
tmux [attach|a] -t $session_name

# rename session (see ls command)
tmux rename-session -t $old_session_name $new_session_name

# kill session with $session_name
tmux kill-session -t $session_name

# kill all sessions, except attached one 
tmux kill-session -a
```