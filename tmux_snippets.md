# Tmux Snippets

## Copy paste 
You use space bar for the beginning of the selection and enter for the end.

copy:

```
Ctrlb[
"space"
"enter"
```

paste:

```
Ctrlb]
```

## Move window 

```
move-window -t other_session:
```


## Swap panes 
To let window number 3 and window number 1 swap their positions.

```
CTRL B
swap-window -s 3 -t 1
```

To move the current window to the top, do:
```
swap-window -t 0
```

break-pane
