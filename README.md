# VimLab 
VimLab replicates MATLAB's support for code sections in Vim. It uses
tmux to maintain a MATLAB session from within vim.

This is a fork of dajero/VimLab with personally preferred modifications.
Original VimLab is (c) Jeroen de Haas.

## Requirements
VimLab relies on tmux and screen.vim which are used to set up and communicate
with a MATLAB session. It expects the `matlab` command to be on your `$PATH`.
Code analysis, similar to that offered by MATLAB's editor, is provided by the
excellent Syntastic plugin. If `mlint` is on your path as well, Syntastic will
automatically analyze your MATLAB code when it's saved.

### tmux
VimLab requires vim to run inside a tmux session. Linux users may find a tmux
package is provided by their favorite distribution. For OS X users, I recommend
installing tmux using [homebrew](http://brew.sh). 

For a well written introduction to tmux, please take a look at the book ["tmux:
Productive Mouse-Free Development"](http://pragprog.com/book/bhtmux/tmux) by
Brian P. Hogan. 

### screen.vim
VimLab uses [Screen.vim](https://github.com/ervandew/screen) to manage a MATLAB
session within tmux.

### Syntastic (Optional)
Install [Syntastic](https://github.com/scrooloose/syntastic) if you wish to have
your MATLAB code automatically analyzed when it is saved. 
 
## Installation
I recommend installing VimLab using [Vundle](https://github.com/gmarik/vundle).
Add the following lines to your .vimrc file:
```vim
Plugin "ervandew/screen"
Plugin "kinnala/VimLab"
"Optional, if you desire automatic code analysis
Plugin "scrooloose/syntastic"
```
Next, either quit and relaunch vim or source `.vimrc` from within your current
vim session. Finally, issue the `:PluginInstall` command to vim to install
VimLab and its dependencies.

## Usage
VimLab automatically creates a few key mappings when you enter a MATLAB buffer.
These mappings are prefixed by your leader, which defauls to `\`. If you set
your mapleader to a different character, please mentally substitute the
backslash by the `mapleader` of your choice. 

* `\mm` starts MATLAB
* `\ms` sends the current section to MATLAB and (*TODO*) in visual mode send selection to MATLAB.
* `\md` open the documentation browser for the current word
* `\mh` show help for the current word
* `\mv` show the variable the cursor is on
* `gn`  go to the next section
* `gN`  go to the previous section
* `\mb` (*TODO*) add/remove a breakpoint
* `\mr` (*TODO*) run the file in MATLAB

VimLab also provides two commands to quickly open the documentation or help for
a function:
* `:mdoc my-function` opens the documentation for my-function
* `:mhelp my-function` shows help for my-function

*TODO*. Section highlighting, maybe through custom m-file highlighting.
*TODO*. Parse the html-tags in help-command outputs somehow. Maybe implement through custom matlab startup script.

## Configuration
By default, VimLab splits your tmux window horizontally to create a pane for
MATLAB. If instead, you prefer the panes to be arranged vertically, set the
varible `g:matlab_vimlab_vertical` to `1`, e.g. add the following line to your
`.vimrc`:
```vim
let g:matlab_vimlab_vertical=1
```
