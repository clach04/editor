# Syntax Highlighting

## Selection
The type of highlighting is selected by file extension. Files with
`.c`, `.cc`, `.c++`, `.cxx`, `.m`, `.h`, `.js`, `.java`, `.py`
extensions will be highlighted with 'C' style highlighting. Files with
`.htm`, `.html` extensions will be highlighted as HTML. Files with
`.cs`, `.css` extensions will be highlighted as CSS.

## Parsing
The algorithm makes no attempt at parsing. The text is scanned for
relevent keywords, classes, constants, strings and comments and
highlighted accordingly. Therefore it will not be exactly correct, but
good enough for a simple text editor.

### C type
Keywords are matched from a list of C/C++/Objective
C/Java/Javascript/Python keywords. Classes are capitalised
words. Constants are all caps, underscore and digit words. Strings are
in double quotes. Single quotes are ignored because apostrophes break
the algorithm. Both `/* */` and `// ` C style comments are recognised.

### HTML
HTML keywords are matched from a list. Double quoted arguments are
highlighted. As above, single quotes are ignored. HTML comments `<!--
-->` are recognised.

### CSS
CSS style names are matched from a list. Double quoted arguments are
highlighted. As above, single quotes are ignored. C style comments are
recognised.

## Limitations
Because scanning and highlighting a large file can be quite slow,
making the app unresponsive, only the text currently in view is
scanned and highlighted. Therefore as the text is edited or scrolled,
the new region in view will be scanned and highlighted after a short
delay to allow for user typing without the highlighting running
constantly.

### Scrolling
After the text is highlighted, the android view system will re-layout
the views whether they need it or not. That causes the current cursor
position to be scrolled back into view, which can be extremely
annoying. So the cursor is moved if necessary to keep it within the
visible region.

### Horizontal scrolling
On devices running android versions less than Marshmallow M (23),
horizontal scrolling will scroll back again. Make the text size
smaller or rotate the device to avoid this. Or turn the highlighting
off.