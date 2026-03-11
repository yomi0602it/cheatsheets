# Vim Cheatsheet

> Press `Esc` to return to Normal mode from any other mode.

## Modes

| Mode | Enter With | Description |
|------|-----------|-------------|
| Normal | `Esc` | Default mode for navigation and commands |
| Insert | `i`, `a`, `o` | For inserting/editing text |
| Visual | `v`, `V`, `Ctrl+v` | For selecting text |
| Command | `:` | For entering ex commands |
| Replace | `R` | Overwrite characters |

## Exiting

```
:q          Quit (fails if unsaved changes)
:q!         Quit and discard changes
:w          Save (write)
:w <file>   Save as a specific file
:wq         Save and quit
:x          Save and quit (only writes if changed)
ZZ          Save and quit (Normal mode shortcut)
ZQ          Quit without saving
```

## Navigation (Normal Mode)

```
h / j / k / l     Move left / down / up / right
w                  Move to start of next word
W                  Move to start of next WORD (space-delimited)
b                  Move to start of previous word
e                  Move to end of current word
0                  Move to start of line
^                  Move to first non-blank character of line
$                  Move to end of line
gg                 Go to first line of file
G                  Go to last line of file
:<n>               Go to line n (e.g., :42)
<n>G               Go to line n (e.g., 42G)
Ctrl+f             Page down
Ctrl+b             Page up
Ctrl+d             Half page down
Ctrl+u             Half page up
%                  Jump to matching bracket
(  )               Move to start of previous/next sentence
{  }               Move to start of previous/next paragraph
H / M / L          Move to top / middle / bottom of screen
```

## Inserting Text

```
i          Insert before cursor
I          Insert at start of line
a          Append after cursor
A          Append at end of line
o          Open new line below and insert
O          Open new line above and insert
s          Delete character and insert
S          Delete line and insert
```

## Editing

```
x          Delete character under cursor
X          Delete character before cursor
dd         Delete (cut) current line
dw         Delete from cursor to end of word
d$         Delete from cursor to end of line
d0         Delete from cursor to start of line
dG         Delete from cursor to end of file
D          Delete to end of line (same as d$)
yy         Yank (copy) current line
yw         Yank word
y$         Yank to end of line
p          Paste after cursor
P          Paste before cursor
cc         Change (delete and insert) current line
cw         Change word
c$         Change to end of line
C          Change to end of line (same as c$)
r<char>    Replace character under cursor
R          Enter Replace mode
u          Undo
Ctrl+r     Redo
.          Repeat last change
~          Toggle case of character
gU<motion> Uppercase text (e.g., gUw)
gu<motion> Lowercase text (e.g., guw)
>>         Indent line
<<         Un-indent line
==         Auto-indent line
```

## Visual Mode

```
v          Start visual mode (character)
V          Start visual mode (line)
Ctrl+v     Start visual block mode
o          Toggle cursor to other end of selection
d          Delete selected text
y          Yank selected text
c          Change selected text
>          Indent selection
<          Un-indent selection
~          Toggle case of selection
:          Enter command on selection
```

## Search & Replace

```
/pattern        Search forward
?pattern        Search backward
n               Next match
N               Previous match
*               Search for word under cursor (forward)
#               Search for word under cursor (backward)
:noh            Clear search highlighting

:%s/old/new/g   Replace all occurrences in file
:%s/old/new/gc  Replace with confirmation
:s/old/new/g    Replace in current line
:10,20s/old/new/g  Replace in lines 10-20
```

## Working with Multiple Files

```
:e <file>      Open a file
:bnext / :bn   Next buffer
:bprev / :bp   Previous buffer
:bd            Close buffer
:ls / :buffers List open buffers
:sp <file>     Open file in horizontal split
:vsp <file>    Open file in vertical split
Ctrl+w h/j/k/l Move between splits (left/down/up/right)
Ctrl+w +/-     Resize split height
Ctrl+w >/<     Resize split width
Ctrl+w =       Make splits equal size
Ctrl+w q       Close current split
:tabnew <file> Open file in new tab
:tabn / gt     Next tab
:tabp / gT     Previous tab
:tabclose      Close current tab
```

## Marks & Jumps

```
m<a-z>     Set mark (lowercase: file-local)
m<A-Z>     Set mark (uppercase: global)
`<mark>    Jump to mark (exact position)
'<mark>    Jump to start of mark's line
``         Jump to last position
''         Jump to start of last position's line
Ctrl+o     Jump to older position
Ctrl+i     Jump to newer position
```

## Useful Commands

```
:set number    Show line numbers
:set nonumber  Hide line numbers
:set nu        Shorthand for number
:set rnu       Relative line numbers
:set wrap      Enable line wrap
:set nowrap    Disable line wrap
:set hlsearch  Highlight search results
:set ignorecase  Case-insensitive search
:set smartcase   Case-sensitive if uppercase used
:set tabstop=4   Set tab width
:set expandtab   Use spaces instead of tabs
:set autoindent  Auto-indent new lines
:syntax on     Enable syntax highlighting
:colorscheme <name>  Change colorscheme
:!<command>    Run a shell command
:r !<command>  Insert shell command output
qa             Start recording macro in register a
q              Stop recording macro
@a             Play macro from register a
@@             Replay last macro
```
