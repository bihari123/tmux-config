# tmux-config
my tmux config


## copy the content into your ~/.tmux.conf

# List of plugins
set -g default-terminal "screen-256color"
# Set status bar position to top
set-option -g status-position top
# Center the status bar
set -g status-justify centre
# Set the status bar length
set -g status-left-length 30
set -g status-right-length 30

# Dracula Color Palette
white='#f8f8f2'
gray='#44475a'
dark_gray='#282a36'
light_purple='#bd93f9'
dark_purple='#6272a4'
cyan='#8be9fd'
green='#50fa7b'
orange='#ffb86c'
red='#ff5555'
pink='#ff79c6'
yellow='#f1fa8c'

# Set the status bar style (Dracula theme)
set -g status-style bg=$gray,fg=$white

# Set the content of the status bar
set -g status-left "#[fg=$dark_gray,bg=$green] #S #[fg=$green,bg=$gray]"
set -g status-right "#[fg=$pink,bg=$gray]#[fg=$dark_gray,bg=$pink] %Y-%m-%d %H:%M "

# Set the center status (assuming you're using tmux-pomodoro-plus plugin)
set -g status-interval 1
set -g status-centre "#[fg=$light_purple,bg=$gray] #{pomodoro_status} "

# Window status
set-window-option -g window-status-style fg=$white,bg=$gray
set-window-option -g window-status-current-style fg=$dark_gray,bg=$light_purple

# Pane border
set -g pane-border-style fg=$gray
set -g pane-active-border-style fg=$light_purple

# Message text
set -g message-style bg=$gray,fg=$white

# Modes
setw -g mode-style bg=$yellow,fg=$dark_gray

# Enable pane borders
set -g pane-border-status top

# Set pane border format (includes pane index and name)
set -g pane-border-format "#[fg=$dark_gray,bg=$light_purple] #P: #T "

# Key binding to rename pane
bind-key r command-prompt -p "Rename pane:" "select-pane -T '%%'"

set -g @plugin 'tmux-plugins/tpm'
set -g @plugin 'tmux-plugins/tmux-sensible'
set -g @plugin 'jaclu/tmux-menus'
set -g @plugin 'tmux-plugins/tmux-sidebar'
set -g @plugin 'tmux-plugins/tmux-pain-control'
set -g @plugin "tmux-plugins/tmux-battery"
set -g @plugin "olimorris/tmux-pomodoro-plus"
set -g status-right "#{pomodoro_status}"
set -g @pomodoro_granularity 'on'
set -g status-interval 1                       # Refresh the status line every second

# Other examples:
# set -g @plugin 'github_username/plugin_name'
# set -g @plugin 'github_username/plugin_name#branch'
# set -g @plugin 'git@github.com:user/plugin'
# set -g @plugin 'git@bitbucket.com:user/plugin'

# Initialize TMUX plugin manager (keep this line at the very bottom of tmux.conf)
run '~/.tmux/plugins/tpm/tpm'
