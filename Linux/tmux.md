#on/linux/terminal #on/tmux

prefix key: `^b`

| Command                    | Key Sequence                          |
| -------------------------- | ------------------------------------- |
| Split horizontal           | `^b %`                                |
| Split vertical             | `^b "`                                |
| Switch pane                | `^b `$\leftarrow$, `^b` $\rightarrow$ |
| Close pane                 | `exit` or `^d`                        |
| Create window              | `^b c`                                |
| Next/Prev Window           | `^b n`, `^b p`                        |
| Window by number           | `^b `*n*                              |
| Detach                     | `^b d`                                |
| Choose sessions and detach | `^b D`                                |
| List sessions              | `tmux ls`                             |
| Attach                     | `tmux attach -t `*n*                  |
| Name session               | `tmux new -s `*sessionname*           |
| Toggle pane full-screen    | `^b z`                                |
| Reize Pane                 | `^b C-`*arrow*                        |
| Rename window              | `^b ,`                                |
|                            |                                       |


---
# Sources
[A Quick and Easy Guide to tmux](https://www.hamvocke.com/blog/a-quick-and-easy-guide-to-tmux/)

# See Also
[Making tmux Pretty and Usable - A Guide to Customizing your tmux.conf](https://www.hamvocke.com/blog/a-guide-to-customizing-your-tmux-conf/)
[tmux 2: Productive Mouse-Free Development by Brian P. Hogan](https://pragprog.com/titles/bhtmux2/tmux-2/)
[tmux 2: Productive Mouse-Free Development - YouTube](https://www.youtube.com/watch?v=2HbAMg9k6J0)
[2012 UTOSC - Screen vs. tmux faceoff - Jon Jensen - YouTube](https://www.youtube.com/watch?v=QxTse5Elq8s)
[[GNU Screen]]
