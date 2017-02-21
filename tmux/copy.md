# tmux.conf

```bash
setw -g mode-keys vi
set-option -g default-command "reattach-to-user-namespace -l bash"
bind-key -t vi-copy v begin-selection
unbind -t vi-copy Enter
```

# Start copy mode

Prefix key-[

# Start to select

Space

# Execute copy

y

