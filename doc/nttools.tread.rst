.. _tread:

tread — Browse through a table.
===============================

**Package: nttools**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  tread -- View a table (read only).
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  tread table
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The 'tread' task is a read-only version of 'tedit', the screen editor for STSDAS
  tables.  'tread' lets you view a table by moving the cursor around the
  screen with the cursor keys.  The screen scrolls both sideways and up
  and down as you move the cursor, so all elements of the table can be
  reached. Other editing commands are entered on the command line. To
  switch from table editing mode to command line mode, you press the
  exit key (generally bound to Control-Z, though this can be changed).  
  When your 
  command is completed, the editor returns to table editing mode, unless
  the command exits the editor. The most important commands in command
  mode are `help' and `exit'. The `help' command displays all the
  editing key bindings and the command line commands. The `exit' command
  will get you out of the editor.
  <P>
  Some editing commands are entered from the command line in command
  mode. To get to command line mode, press the exit key (Control-Z). 
  If you enter a 
  blank line, the editor will
  return to table editing mode. Some commands take arguments. They can
  be included when the command is entered, or if they are omitted, the
  editor will prompt you for their values. If the argument has embedded
  blanks, the argument should be enclosed in quotes if passed on the
  command line. No quotes should be used if the argument is entered
  interactively. When the editor interactively prompts you for a command
  argument it will also display a default value for the argument.
  Pressing the return key gets the default value. Some command names are 
  two
  words long, for example, "<TT>find forward</TT>". Usually the second word is
  optional and modifies the meaning of the first.  If the second word is
  not optional and you omit it, the editor will prompt you for it. All
  command names can be abbreviated to one or more letters. If the
  command name is two words long, both words can be abbreviated to one
  or more letters.
  <P>
  The following commands are used by 'tread':
  <DL>
  <DT><B>exit</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='exit' Line='exit'>
  <DD>Exit the table editor.
  </DD>
  </DL>
  <DL>
  <DT><B>find &lt;expression&gt;</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='find' Line='find &lt;expression&gt;'>
  <DD>Find the next row in the table which makes &lt;expression&gt; true and move
  the cursor to that row. The expression has the same syntax as an
  expression in a Fortran if statement.  The variables in the expression
  are column names. For more information on the syntax of the
  expression, read the help for the 'tselect' task. The direction of the search 
  depends 
  upon previous find commands. By default the search direction is forward;
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
  <DD>Exit the table editor.
  </DD>
  </DL>
  <P>
  The bindings to the table editing keys are read from the edcap file.
  This is the file that defines key bindings for the
  parameter editor and history editor. The edcap file defines key
  bindings that resemble those of commonly used text editors. Three
  edcap files are distributed with IRAF. They define key bindings which
  resemble EDT, Emacs, and vi. These edcap files are located in the 'dev$'
  directory and have the extension '.ed'. The appropriate file is chosen
  according to the value of the environment variable 'EDITOR'. If you
  want to customize the key bindings of the table editor, copy the
  appropriate edcap file from the 'dev$' directory to your 'home$' directory
  and edit the second column. The table editor searches your
  home directory first for the edcap file and if it does not find it,
  searches the 'dev$' directory.
  <P>
  The table editor also uses the termcap file to determine the screen
  size and the escape sequences used to modify the screen. There are
  entries in the termcap file for almost all terminal types. The proper
  entry is selected according to the environment variable terminal. To
  change your terminal type or the screen size, use the IRAF 'stty'
  command. 
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>table [string]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='table' Line='table [string]'>
  <DD>Name of the table to be edited. The editor checks for the
  existence of the table and its access mode before editing. The table
  must exist in order to edit it with 'tread'.
  </DD>
  </DL>
  <DL>
  <DT><B>(columns = "<TT></TT>") [string]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(columns = "") [string]'>
  <DD>Names of the columns to be edited.
  A null or blank string means edit all columns.
  A column template consists of a list of either
  column names or column patterns containing the usual pattern matching
  meta-characters.  The names or patterns are separated by commas or
  white space.  The list can be placed in a file and the name of the
  file preceded by an "<TT>@</TT>" character.
  If the first character in the column template is a bang (!),
  all columns NOT named will be displayed.
  <P>
  The 'tlcol' task (with the 'nlist' parameter set to 1) may be used to generate a 
  list of
  column names so there is no question about spelling.  This list may be
  edited to rearrange (or delete) the names, and then pass the list to this task 
  by preceding the its file name with an "<TT>@</TT>", for example,  
  <P>
  tt&gt; tedit junk columns=@colnames.lis
  </DD>
  </DL>
  <DL>
  <DT><B>(silent = no) [boolean]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(silent = no) [boolean]'>
  <DD>Turn off the bell indicating warning messages?
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Display only the columns 'SHARP' and 'ROUND' from the table 'm12b.tab':
   
  <PRE>
  tt&gt; tread m12b columns="SHARP,ROUND"
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
  tedit, tprint, tselect, stty
  <P>
  Type "<TT>help tables opt=sys</TT>" for a description of the 'tables' package.
  </UL>
  <! EndSection:    'SEE ALSO '>
  
  <! Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'PARAMETERS' 'EXAMPLES' 'BUGS' 'REFERENCES' 'SEE ALSO '  >
  
