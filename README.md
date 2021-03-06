# VimLab 
VimLab replicates MATLAB's support for code sections in Vim. It uses
tmux to maintain a MATLAB session from within vim.

This is a fork of dajero/VimLab with personally preferred modifications.
Original VimLab is (c) Jeroen de Haas.

## Requirements
VimLab relies on tmux and screen.vim which are used to set up and communicate
with a MATLAB session. It expects the `matlab` command to be on your `$PATH`.

### tmux
VimLab requires vim to run inside a tmux session. Linux users may find a tmux
package is provided by their favorite distribution. For OS X users, it is recommended to
install tmux using [homebrew](http://brew.sh). 

### screen.vim
VimLab uses [screen.vim](https://github.com/ervandew/screen) to manage a MATLAB
session within tmux.
 
## Installation
[Vundle](https://github.com/gmarik/vundle) is recommended for installing VimLab.
Add the following lines to your .vimrc file:
```vim
Plugin "ervandew/screen"
Plugin "kinnala/VimLab"
```
Next, either quit and relaunch vim or source `.vimrc` from within your current
vim session. Finally, issue the `:PluginInstall` command to vim to install
VimLab and its dependencies.

## Usage

VimLab automatically creates a few key mappings when you enter a MATLAB buffer.
These mappings are prefixed by your leader, which defauls to `\`.

* `\mm` starts MATLAB
* `\ms` run the current **s**ection in MATLAB (in normal mode).
* `\md` open the **d**ocumentation browser for the current word
* `\mh` show **h**elp for the current word
* `\me` **e**valuate the current word (or visual selection) in command interpreter
* `\mb` add a **b**reakpoint with *dbstop in file at line* (note that by default MATLAB opens its built-in editor on break, this functionality can be disabled from MATLAB preferences.)
* `\mB` remove all **b**reakpoints (*dbclear all*).
* `\mr` **r**un the file in MATLAB as a script
* `\mx` run "close all" (click **x** on all figures)
* `\mc` **c**heck the code with *mlintrpt*
* `gn`  go to the next section
* `gN`  go to the previous section

VimLab also provides two commands to quickly open the documentation or help for
a function:
* `:Mdoc my_function` opens the documentation for *my_function*
* `:Mhelp my_function` shows help for *my_function*

Other added features
* *TODO*. Section highlighting, maybe through custom m-file highlighting.
* Removes html-clutter in help outputs

## Configuration
By default, VimLab splits your tmux window horizontally to create a pane for
MATLAB. If instead, you prefer the panes to be arranged vertically, set the
varible `g:matlab_vimlab_vertical` to `1`, e.g. add the following line to your
`.vimrc`:
```vim
let g:matlab_vimlab_vertical=1
```
