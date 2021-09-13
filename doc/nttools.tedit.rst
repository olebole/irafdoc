.. _tedit:

tedit — Edit a table.
=====================

**Package: nttools**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  tedit -- Edit a table.
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  tedit table
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  This task is a screen editor for STSDAS tables. You edit a table by
  moving the cursor around the screen with the cursor keys and typing in
  the new value of the table element. The screen scrolls both sideways
  and up and down as you move the cursor, so all elements of the table
  can be reached. Other editing commands are entered on the command
  line. To switch from table editing mode to command line mode, you
  press the EXIT key (usually Control-Z, however, you can change this). After
  performing your command, the editor returns to table editing mode,
  unless the command exits the editor. The most important commands in
  command mode are `help', `exit', and `quit'. The `help' command
  displays all the editing key bindings and the command line commands.
  The `exit' command will get you out of the editor and automatically
  save the edited table. The `quit' command will get you out of the
  editor after asking you whether you want to save the table. By
  default, the editor modifies a copy instead of the original table, so
  if you quit without saving the table, the original table is still
  there without any modifications.
  <P>
  If you try to edit a table that does not exist, the editor will ask if
  you want to create the table. If you answer "<TT>no</TT>", the editor will
  exit.  If you answer "<TT>yes</TT>", the editor will ask you for each column
  name, type, unit, and print format. When you have finished entering
  all the columns, press the return key instead of entering another
  column name. The editor will create the table and put you in table
  editing mode.
  <P>
  To add a new, blank line to the end of a table, press the return key
  while you are on the last line of the table. You can add blank lines
  anywhere in the table with the `add row' command, which will be
  described later.
  <P>
  Some editing commands are entered from the command line in command
  mode. To get to command line mode, press the exit key. This key is
  bound to Control-Z by default. If you enter a blank line, the editor will
  return to table editing mode. Some commands take arguments. They can
  be included when the command is entered, or if they are omitted, the
  editor will prompt you for their values. If the argument has embedded
  blanks, the argument should be enclosed in quotes if passed on the
  command line. No quotes should be used if the argument is entered
  interactively. When the editor interactively prompts you for a command
  argument it will also display a default value for the argument.
  Pressing the return key gets the default value. Some command names are
  two words long, for example, "<TT>add row</TT>". Usually the second word is
  optional and modifies the meaning of the first, for example "<TT>copy
  append</TT>". If the second word is not optional and you omit it, the
  editor will prompt you for it. All command names can be abbreviated to
  one or more letters. If the command name is two words long, both words
  can be abbreviated to one or more letters.
  <P>
  The following is a list of the available commands:
  <P>
  <DL>
  <DT><B>add column &lt;name&gt; &lt;type&gt; &lt;format&gt; &lt;units&gt;</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='add' Line='add column &lt;name&gt; &lt;type&gt; &lt;format&gt; &lt;units&gt;'>
  <DD>Add a new column to the table with the specified name and data type.
  </DD>
  </DL>
  <DL>
  <DT><B>add row &lt;row&gt; &lt;number&gt;</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='add' Line='add row &lt;row&gt; &lt;number&gt;'>
  <DD>Add new, blank rows after row number &lt;row&gt;. The legal range of &lt;row&gt; is
  0 to the number of rows in the table. The number of blank rows to add is 
  &lt;number&gt;.
  </DD>
  </DL>
  <DL>
  <DT><B>copy &lt;first&gt; &lt;last&gt;</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='copy' Line='copy &lt;first&gt; &lt;last&gt;'>
  <DD>Copy the rows between &lt;first&gt; and &lt;last&gt; into the paste buffer. The 
  current contents of the paste buffer are destroyed before the copy.
  The table is not modified by this command. The contents of the paste 
  buffer can be put back into the table by the 'insert' command.
  </DD>
  </DL>
  <DL>
  <DT><B>copy append &lt;first&gt; &lt;last&gt;</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='copy' Line='copy append &lt;first&gt; &lt;last&gt;'>
  <DD>Copy the rows between &lt;first&gt; and &lt;last&gt; into the paste buffer. The 
  current contents of the paste buffer are preserved and the new rows
  are inserted after them.
  </DD>
  </DL>
  <DL>
  <DT><B>delete &lt;first&gt; &lt;last&gt;</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='delete' Line='delete &lt;first&gt; &lt;last&gt;'>
  <DD>Delete the rows between &lt;first&gt; and &lt;last&gt;. The deleted rows are placed
  into the paste buffer and the current contents of the paste buffer are
  destroyed.
  </DD>
  </DL>
  <DL>
  <DT><B>delete append &lt;first&gt; &lt;last&gt;</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='delete' Line='delete append &lt;first&gt; &lt;last&gt;'>
  <DD>Delete the rows between &lt;first&gt; and &lt;last&gt;. The deleted rows are appended 
  to the paste buffer.
  </DD>
  </DL>
  <DL>
  <DT><B>exit</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='exit' Line='exit'>
  <DD>Exit the table editor, saving any changes made to the table.
  </DD>
  </DL>
  <DL>
  <DT><B>find &lt;expression&gt;</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='find' Line='find &lt;expression&gt;'>
  <DD>Find the next row in the table which makes &lt;expression&gt; true and move
  the cursor to that row. The expression has the same syntax as an
  expression in a Fortran if statement.  The variables in the expression
  are column names. For more information on the syntax of the
  expression, read the help for 'tselect'. The direction of the search depends 
  upon previous 'find' commands. By default the search direction is forward;
  however, if a "<TT>find backwards</TT>" command has been executed previously, 
  searches will be done in a backwards direction until a "<TT>find forward</TT>"
  command is executed.
  </DD>
  </DL>
  <DL>
  <DT><B>find forward &lt;expression&gt;</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='find' Line='find forward &lt;expression&gt;'>
  <DD>Find the next row in the table which makes &lt;expression&gt; true and move the
  cursor to that row. The search is done in the forwards direction.
  </DD>
  </DL>
  <DL>
  <DT><B>find backwards &lt;expression&gt;</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='find' Line='find backwards &lt;expression&gt;'>
  <DD>Find the next row in the table which makes &lt;expression&gt; true and move the
  cursor to that row. The search is done in the backwards direction.
  </DD>
  </DL>
  <DL>
  <DT><B>goto &lt;row&gt; &lt;column&gt;</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='goto' Line='goto &lt;row&gt; &lt;column&gt;'>
  <DD>Move the cursor to &lt;row&gt; and &lt;column&gt;.
  </DD>
  </DL>
  <DL>
  <DT><B>help</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='help' Line='help'>
  <DD>Display online help information for the table editor. The help includes 
  a brief description of each command line command and the key bindings 
  for table editing commands.
  </DD>
  </DL>
  <DL>
  <DT><B>insert &lt;row&gt;</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='insert' Line='insert &lt;row&gt;'>
  <DD>Insert the contents of the paste buffer after row number &lt;row&gt;. The 
  contents of the paste buffer are not changed.
  </DD>
  </DL>
  <DL>
  <DT><B>lower &lt;column&gt;</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='lower' Line='lower &lt;column&gt;'>
  <DD>Convert &lt;column&gt; to lower case. Only string columns can be converted.
  </DD>
  </DL>
  <DL>
  <DT><B>next</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='next' Line='next'>
  <DD>Repeat the previous find command, using the same expression and search 
  direction that was used with it.
  </DD>
  </DL>
  <DL>
  <DT><B>next forward</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='next' Line='next forward'>
  <DD>Repeat the previous find command, changing the search direction to 
  forwards.
  </DD>
  </DL>
  <DL>
  <DT><B>next backwards</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='next' Line='next backwards'>
  <DD>Repeat the previous find command, changing the search direction to 
  backwards.
  </DD>
  </DL>
  <DL>
  <DT><B>quit</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='quit' Line='quit'>
  <DD>Exit the table editor. If the table has been changed, the table editor 
  will ask you whether to save it before exiting.
  </DD>
  </DL>
  <DL>
  <DT><B>set &lt;column&gt; &lt;expression&gt;</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='set' Line='set &lt;column&gt; &lt;expression&gt;'>
  <DD>Set a column equal to an expression. If the column is a string column,
  the expression must be a constant. If the column is numeric, the
  expression can either be a constant or a Fortran-like expression. For
  the exact syntax of the expression, see the help file for tcalc.
  </DD>
  </DL>
  <DL>
  <DT><B>substitute &lt;column&gt; &lt;target&gt; &lt;replacement&gt;</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='substitute' Line='substitute &lt;column&gt; &lt;target&gt; &lt;replacement&gt;'>
  <DD>Search for and replace text patterns in a column.  The syntax for the
  target and replacement pattern strings largely follows that used in
  the substitute command by the Unix text editors `ed' and `ex'. The
  pattern consists of a sequence of ordinary characters, which match
  themselves, and meta-characters, which match a set of characters. A
  meta-character can be matched as if it were an ordinary character by
  preceding it with the escape character, <TT>`\'</TT>. For example, the escape
  character itself is indicated in a pattern by `\\'. The meta-characters
  which can be used in the target pattern are:
  <P>
  <PRE>
  beginning of string	^	end of string		$
  white space		#	escape character	\<BR>
  ignore case		{	end ignore case		}
  begin character class	[	end character class	]
  not, in char class	^	range, in char class	-
  one character		?	zero or more occurrences *
  begin tagged string	\(	end tagged string	\)
  </PRE>
  <P>
  A set of characters is indicated in the target string by the character
  class construct. For example, punctuation could be indicated by
  `[,;.!]'.  A range of characters contiguous in the underlying
  character set can be abbreviated by the range construct. For example,
  `[a-z]' matches any lower case character. The complement of a
  character set is indicated by making <TT>`^'</TT> the first character in a
  class. For example, `[^0-9]' matches any non-digit. Repetition of a
  character or character class is indicated by the following it with the
  <TT>`*'</TT> meta-character. Thus, zero or more occurrences of a lower case
  character is indicated by `[a-z]*'. The tagged string meta-characters
  have no effect on the match, they only serve to identify portions of
  the matched string for the replacement pattern. The meta-characters
  which are used in the replacement pattern are the following:
  <P>
  <PRE>
  entire string		&amp;	tagged string		\n
  capitalize		\u	upper case		\U
  lower case		\L	end case conversion	\e \E
  </PRE>
  <P>
  The ditto meta-character, <TT>`&'</TT>, indicates that the entire portion of the
  string that was matched by the target pattern. The tag meta-character
  indicates that the n-th tagged string.  For example, `\1' indicates
  the first tagged string and `\2' the second. The remaining
  meta-characters affect the case of the output string. The
  capitalization meta-character only affects the immediately following
  meta-character, but the upper and lower case meta-characters must be
  turned off explicitly with `\e' or `\E'.
  </DD>
  </DL>
  <DL>
  <DT><B>upper &lt;column&gt;</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='upper' Line='upper &lt;column&gt;'>
  <DD>Convert &lt;column&gt; to upper case. Only string columns can be converted.
  </DD>
  </DL>
  <P>
  The bindings to the table editing keys are read from the edcap file.
  This is the same file which is used to define the key bindings for the
  parameter editor and history editor. The edcap file defines key
  bindings which resemble those of commonly used text editors. Three
  edcap files are distributed with IRAF. They define key bindings which
  resemble EDT, Emacs, and vi. These edcap files are located in the 'dev$'
  directory and have the extension '.ed'. The appropriate file is chosen
  according to the value of the environment variable 'EDITOR'. If you
  want to customize the key bindings of the table editor, copy the
  appropriate edcap file from the 'dev$' directory to your 'home$' directory
  and edit the second column of the file. The table editor searches your
  home directory first for the edcap file and if it does not find it,
  then it searches the 'dev$' directory.
  <P>
  The table editor also uses the termcap file to determine the screen
  size and the escape sequences used to modify the screen. There are
  entries in the termcap file for almost all terminal types. The proper
  entry is selected according to the environment variable 'TERMINAL'. To
  change your terminal type or the screen size, use the IRAF 'stty'
  command. 
  <P>
  The 'tread' task can also be used to view a file in readonly mode.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>table [string]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='table' Line='table [string]'>
  <DD>The name of the table to be edited. The editor checks for the
  existence of the table and its access mode before editing. If the 
  table does not exist, the editor will ask whether you want to create
  a new table. If you do not have write access to a table you can only
  edit it by setting 'rdonly=yes'.
  </DD>
  </DL>
  <DL>
  <DT><B>(columns = "<TT></TT>") [string]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(columns = "") [string]'>
  <DD>The names of the columns to be edited.
  A null or blank string means edit all columns.
  A column template consists of a list of either
  column names or column patterns containing the usual pattern matching
  meta-characters.  The names or patterns are separated by commas or
  white space.  The list can be placed in a file and the name of the
  file preceded by an "<TT>@</TT>" given in its place.
  If the first character in the column template is a bang (!),
  all columns NOT named will be displayed.
  <P>
  The 'tlcol' task (with the 'nlist' parameter set to 1)  may be used to generate 
  a list of
  column names so there is no question about spelling.  This list may be
  edited to rearrange or delete the names, and then the list
  file is given preceded by an <TT>'@'</TT> sign, for example:
  <P>
  <PRE>
  tt&gt; tedit junk columns=@colnames.lis
  </PRE>
  </DD>
  </DL>
  <DL>
  <DT><B>(silent = no) [boolean]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(silent = no) [boolean]'>
  <DD>Turn off the bell indicating warning messages? 
  </DD>
  </DL>
  <DL>
  <DT><B>(rdonly = no) [boolean]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(rdonly = no) [boolean]'>
  <DD>View a table without modifying it?  This parameter prevents you from 
  executing
  any command that would modify the file.
  </DD>
  </DL>
  <DL>
  <DT><B>(inplace = no) [boolean]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(inplace = no) [boolean]'>
  <DD>Replace existing table?  If 'rdonly' is
  set to "<TT>yes</TT>" the table is always edited in place.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Make a copy of the table 'm12b.tab' (if it exists) and edit the copy. 
  If the table does not exist
  then a temporary table is created, and you will be prompted for the
  name of the first column to be created.  In either case, if you
  exit (rather than quitting) the temporary table will be renamed to
  'm12b.tab'.
  <P>
  <PRE>
  tt&gt; tedit m12b
  </PRE>
  <P>
  2. Display the columns 'SHARP' and 'ROUND' in an existing table. Rows may 
  be added or deleted, and columns may be added.  
  <P>
  <PRE>
  tt&gt; tedit m12b columns="SHARP,ROUND"
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  </UL>
  <! EndSection:   'BUGS'>
  <H3>References</H3>
  <! BeginSection: 'REFERENCES'>
  <UL>
  This task was written by Bernie Simon.
  </UL>
  <! EndSection:   'REFERENCES'>
  <H3>See also </H3>
  <! BeginSection: 'SEE ALSO '>
  <UL>
  tread, tprint, tselect, stty
  <P>
  Type "<TT>help tables opt=sys</TT>" for a description of the 'tables' package.
  </UL>
  <! EndSection:    'SEE ALSO '>
  
  <! Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'PARAMETERS' 'EXAMPLES' 'BUGS' 'REFERENCES' 'SEE ALSO '  >
  
