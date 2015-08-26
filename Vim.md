##Notes

###Motion

* In many cases `/` is the fastest way to get from point a to b

# shortcuts

Function up down left right


escape 1234567890-=\`
escape !@#$%^&*()_+|~

# vim

hjkl

left downup right

$ end of line
0 beginning of line

^ shift 6 move to first character on line

gg Move to first line of file

G Move to last line of file

w move forward to next word
b move backward to next word
e move forward to next word, with cursor on last character
ge move backward to next word, with cursor on last character

H
M
L

head middle last line of current visible window

* search forward for word under cursor
# search backwards for word under cursor

# Deletion

x delete character forward
r replace single character under cursor
s delete character under cursor and switch to insert mode

D delete entire line
dd delete current link

# INSERT mode
i
I
a
A

# Visual mode
v 
V

# Undo
u Undo
U undo all changes on current line

Text Entry Commands (Used to start text entry)
a Append text following current cursor position
A Append text to the end of current line
i Insert text before the current cursor position
I Insert text at the beginning of the cursor line
o Open up a new line following the current line and add text there
O Open up a new line in front of the current line and add text there
The following commands are used only in the commands mode.
Cursor Movement Commands
h Moves the cursor one character to the left
l Moves the cursor one character to the right
k Moves the cursor up one line
j Moves the cursor down one line
nG or :n Cursor goes to the specified (n) line
(ex. 10G goes to line 10)
^F (CTRl F) Forward screenful
^B Backward screenful
^f One page forward
^b One page backward
^U Up half screenful
^D Down half screenful
$ Move cursor to the end of current line
0 (zero) Move cursor to the beginning of current line
w Forward one word
b Backward one word
Exit Commands
:wq Write file to disk and quit the editor
:q! Quit (no warning)
:q Quit (a warning is printed if a modified file has not been saved)
ZZ Save workspace and quit the editor (same as :wq)
: 10,25 w temp
write lines 10 through 25 into file named temp. Of course, other line
numbers can be used. (Use :f to find out the line numbers you want.
 
Text Deletion Commands
x Delete character
dw Delete word from cursor on
db Delete word backward
dd Delete line
d$ Delete to end of line
d^ (d caret, not CTRL d) Delete to beginning of line
