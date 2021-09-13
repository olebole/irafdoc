tupar — Edit table header keywords.
===================================

**Package: nttools**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>tupar (Jun97)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>tables</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>tupar (Jun97)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>tupar</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  tupar -- Edit table header parameters.
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  tupar table
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  This task is an interactive editor that allows the user to modify table
  header parameters.
  Prompts are written to STDERR rather than
  STDOUT so that STDOUT can be redirected to a file.
  If STDERR is redirected, no prompts will appear.
  Prompting is also turned off if the input is redirected from a file.
  <P>
  The table to be edited is copied to a temporary table
  in the same directory as the original table
  (or in tmp$ if the first copy attempt fails),
  and the changes are made to that copy.
  When you exit 'tupar',
  the copy is renamed back to the name of the original table.
  If you quit rather than exit,
  then the copy is deleted, so the original table will remain unchanged.
  <P>
  The prompt "<TT>:</TT>" is used by the task when it is waiting for user input.
  At this prompt the user can enter any editor command.
  The "<TT>e</TT>" command (or end of file, e.g. Control-Z) will exit the editor.
  The following commands are available:  e, q, g, p, d, r, k, t, l.
  These commands are interpreted as exit, quit (without saving changes),
  get, put, delete, replace, change keyword name, type, and list respectively.
  Each of these commands is described in detail below:
  <P>
  The exit command, specified by "<TT>e</TT>" or end of file,
  will close the file--saving all changes,
  and open the next file if more than one file was specified
  for the 'table' input parameter.
  <P>
  The quit command is similar to exit except that changes that were made
  to the header parameters will not take effect,
  unless 'inplace = yes'.
  If changes were made to the table header
  you will be prompted for confirmation
  unless the command was given followed by "<TT>!</TT>";
  for example, "<TT>q!</TT>" or "<TT>quit!</TT>".
  <P>
  The type command, specified by "<TT>t</TT>", and the list command,
  specified by "<TT>l</TT>",
  both display header parameters---one header per line of output.
  The difference between the two commands is that list will show the parameter
  number and type will not.
  Entering the command "<TT>t</TT>" or "<TT>l</TT>" will produce
  a listing of all header parameters.
  Optionally, an integer may follow
  the command indicating that only a particular parameter is to be displayed.
  Two integers following the command indicate a range of parameters.
  If a number is specified that is beyond the range of valid headers,
  an error message will be displayed.
  The output consists of the name of the header parameter,
  its data type (indicated by a single letter,
  "<TT>r</TT>" for real, "<TT>b</TT>" for boolean, "<TT>i</TT>" for integer, or "<TT>d</TT>" for double),
  and its current value.
  If the keyword has an associated comment,
  the comment will be displayed following the value.
  The following are examples of valid syntax for listing header parameters:
  <PRE>
  t
  l
  t 3
  l 300 310
  </PRE>
  <P>
  The get command, indicated by "<TT>g</TT>", will look for a specific keyword and
  display its current value.
  Optionally, the data type can be specified
  using the letter "<TT>r</TT>" for real, "<TT>i</TT>" for integer, "<TT>d</TT>" for double, or
  "<TT>b</TT>" for boolean.
  If no data type is specified, then the type is assumed to be text.
  If the data type is specified,
  the type immediately follows the "<TT>g</TT>" command;
  for example, typing the command "<TT>gd X</TT>" will get the value 
  contained in the header keyword "<TT>X</TT>" and display it as a double-precision
  real value.
  If "<TT>X</TT>" does not exist, no output will be produced.
  If the keyword has an associated comment,
  the get command displays the comment following the value;
  a text string value will be enclosed in quotes
  to distinguish the value from the comment.
  Examples of valid syntax follow:
  <PRE>
  g history
  gd coeff0
  gi numpts
  </PRE>
  <P>
  The put command, specified by "<TT>p</TT>", will either replace the value of an
  existing parameter,
  or it will create a new parameter if the specified parameter is not found.
  The "<TT>p</TT>" command is followed on the command line by a keyword
  name and the parameter value.
  A comment may optionally follow the value.
  The "<TT>p</TT>" command itself should
  be followed by a single letter type specifier, "<TT>i</TT>" for integer,
  "<TT>r</TT>" for real, "<TT>d</TT>" for double, or "<TT>b</TT>" for boolean.
  If no type is specified, then the data type is assumed to be text.
  In order to specify a comment with a parameter of type text,
  the parameter value must be enclosed in quotes
  in order to distinguish it from the comment.  (Keyword names
  HISTORY and COMMENT are already comments,
  and further comments cannot be added to them.)
  Examples of valid put command syntax follow:
  <PRE>
  p comment Created for testing.
  gd coeff0
  pd coeff0 3.141592653589793
  pi ncoeff 7 number of coefficients
  pt fittype chebychev
  pt fittype "chebychev" type of fit that these coefficients represent
  </PRE>
  <P>
  The replace command, specified by "<TT>r</TT>", works much like the put command
  described above; however, it will prompt the user for confirmation before
  actually changing any values in the table.
  A parameter can be specified by name or by number.
  The "<TT>r</TT>" command will not change a keyword name or a data type,
  whereas the "<TT>p</TT>" command can.
  After the command is entered,
  the current value of the keyword is displayed and
  the editor waits for a new value to be entered by the user.
  Pressing the return key indicates that no change is to be made.
  Pressing the space bar will blank the current value.
  You will then be prompted for
  confirmation unless the command was issued as "<TT>r!</TT>" or the input was
  redirected from a file.
  The default action is given by the 'delete_default' parameter.
  <P>
  A range of contiguous parameters can be replaced at one time by giving
  the names or numbers of the first and last parameters to be replaced.
  This can involve a lot of prompting for confirmation,
  especially if several tables are being edited with 'same=yes'.
  In this context, "<TT>contiguous</TT>" means adjacent in the table header.
  Thus, when replacing a range by name,
  it is not the parameters that fall alphabetically within the limits
  that will be replaced
  but rather the parameters that are numerically within the limits.
  When editing a list of tables with 'same=yes',
  the same replacement string is used for each table.
  Thus it is essential that there be the same number of parameters in
  the range in all tables being edited.
  When no replacement value is given (i.e., just hit the return key),
  then the current keyword value is not changed,
  either in the first table or in subsequent tables.
  <P>
  Sample replace commands follow:
  <PRE>
  r coeff0
  r 17
  r! 17
  r junk dummy
  r junk 12
  r 5 12
  </PRE>
  <P>
  The delete command, specified by "<TT>d</TT>", will delete a header parameter by
  either name or number.
  The editor prompts for confirmation of delete,
  unless input is redirected from a file.
  The default action is given by the 'delete_default' parameter.
  If you do not want to be prompted for confirmation, enter the command as "<TT>d!</TT>".
  If you want to delete a history or comment record other than the first,
  you can identify the parameter by number rather than name.
  <P>
  A range of contiguous parameters can be deleted at one time by giving
  the names or numbers of the first and last parameters to be deleted.
  As with replacing a range of parameters,
  a contiguous block of parameters will be deleted.
  <P>
  Examples of valid delete commands follow:
  <PRE>
  d testflag
  d 17
  d! 17
  d junk dummy
  d junk 12
  d 5 12
  </PRE>
  <P>
  The "<TT>k</TT>" command changes the name of a keyword
  without changing the data type, value, or comment.
  Give the current and new keyword names following the "<TT>k</TT>".
  Note that keywords are limited to eight characters.
  If the name of a COMMENT or HISTORY keyword is changed,
  only the first occurrence of that keyword will be changed.
  <P>
  Examples of valid change keyword commands follow:
  <PRE>
  k history comment
  k dummy test
  </PRE>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_table">table [file name template]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='table' Line='table [file name template]'>
  <DD>A table name or list of table names whose header parameters are to be edited.
  Unless 'inplace = yes',
  each table will be copied (one at a time) to a temporary table,
  and changes are made to the copy until you exit.
  This can cause problems if there is not enough disk space for the copy;
  however, the 'inplace' parameter can
  be set to "<TT>yes</TT>" so that the tables are opened in-place.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(same = no) [boolean]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(same = no) [boolean]'>
  <DD>Apply the same set of instructions to all tables?  
  <P>
  This is only relevant when more than one table is being edited.
  If 'same = no', instructions are processed separately for each table,
  with the "<TT>e</TT>" command used to end processing of a table and open
  the next table.
  <P>
  If 'same = yes', the same instruction set is applied to all tables.
  These instructions will be read from STDIN (which may be redirected)
  and saved in a local buffer while the first table in the list is open.
  For each subsequent table the instructions will be read from the local buffer.
  Caution is advised when deleting or replacing parameters, especially by
  number; remember that prompting for confirmation is turned off if the
  input is redirected or if the instruction is given as "<TT>d!</TT>" or "<TT>r!</TT>".
  <P>
  If 'same = yes' and you quit (rather than exit) from editing the first table,
  the behavior of the task depends on whether changes were made before quitting.
  If changes were made then the task aborts immediately
  without opening the other tables in the input list.
  If no change was made then the other tables are processed.
  The idea is to allow "<TT>g</TT>", "<TT>t</TT>", and "<TT>l</TT>" commands
  and still be able to quit rather than exit,
  since nothing was modified.
  If changes were made but you quit,
  that's interpreted as trying to recover from an error,
  so we don't change the first table and we don't continue.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(verbose = yes) [boolean]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(verbose = yes) [boolean]'>
  <DD>Display the name of each table when it is opened?  
  <P>
  If STDOUT is redirected
  then these file names will be written to STDERR as well as to STDOUT.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(readonly = no) [boolean]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(readonly = no) [boolean]'>
  <DD>Prevent changes from being made to the file?  
  <P>
  If 'readonly = yes', then the
  table is opened with read only access.  This is useful for viewing the
  contents of the table while at the same time preventing changes from
  being made to it.  (Only the "<TT>g</TT>", "<TT>t</TT>", and "<TT>l</TT>" commands are useful in
  read only mode).
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(inplace = no) [boolean]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(inplace = no) [boolean]'>
  <DD>Edit the original table in-place?
  <P>
  By default a copy of the original table is made,
  either in the same directory or in tmp$.
  This makes it possible to quit without saving changes.
  If the table is large, however,
  it may be undesirable to make a copy,
  so the 'inplace' parameter gives you the option
  of editing the original table.
  In this case, however, it will not be possible to quit without saving changes.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(quit_default = no) [boolean]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(quit_default = no) [boolean]'>
  <DD>The value of this parameter is the default response to the prompt
  for confirmation if you give the quit command.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(delete_default = yes) [boolean]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(delete_default = yes) [boolean]'>
  <DD>The value of this parameter is the default response to the prompt
  for confirmation for the delete and replace commands.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_go_ahead">go_ahead [boolean]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='go_ahead' Line='go_ahead [boolean]'>
  <DD>The user does not set this explicitly.
  It is the parameter which is actually gotten in response to a prompt.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. This example reads all history records from all tables in the default
  directory and writes them to 'history.lis'.
  <PRE>
  <P>
  tt&gt; tupar *.tab same=yes verbose=no readonly=yes &gt;history.lis
          (The task writes a ":" prompt and waits for input.)
  :g history
  :q
  tt&gt;
  </PRE>
  <P>
  2. This example illustrates the use of each of the commands when editing
  parameters in one table.  This kind of interactive use of the task
  would not be appropriate when operating on a list of tables unless
  the 'same' parameter is set to "<TT>no</TT>".
  <PRE>
  <P>
  tt&gt; tupar junk
          (The task writes the table name and a ":" prompt and waits for input.)
  junk.lis
  :g garvage
          (The keyword was not found, so nothing was displayed.)
  :g garbage
  GARBAGE = 3.1416926535
  :pd garbage 3.1415926535
  :p comment yet another comment
  :t
  GARBAGE  d 3.1415926535
  COMMENT  t This is the first comment.
  PI       t 3.1415926535  not an accurate value
  COMMENT  t yet another comment
  :l 3 999
   3 PI       t '3.1415926535'  not an accurate value
   4 COMMENT  t yet another comment
  :g pi
  PI = '3.1415926535'  not an accurate value
  :gd pi
  PI = 3.1415926535  not an accurate value
  :pd pi 3.14159265358979323846 a more accurate value
  :l
   1 GARBAGE  d 3.1415926535
   2 COMMENT  t This is the first comment.
   3 PI       d 3.141592653589793  a more accurate value
   4 COMMENT  t yet another comment
  :d garbage
  The following parameter is to be deleted:
  GARBAGE  d 3.1415926535
     ...   OK to delete ? (yes):			(user hits return)
  :d comment
  The following parameter is to be deleted:
  COMMENT  t This is the first comment.
     ...   OK to delete ? (yes): n		(user types n)
  :l 4
  parameter out of range; max is 3
  :d 3
  The following parameter is to be deleted:
  COMMENT  t yet another comment
     ...   OK to delete ? (yes):			(user hits return)
  :t
  COMMENT  t This is the first comment.
  PI       d 3.141592653589793  a more accurate value
  :r 1
  keyword COMMENT, type t; give replacement value:
  This is the first comment.			(TUPAR writes this &amp; waits)
  this is a comment				(this line entered by user)
  Current parameter and its replacement are:
  COMMENT  t This is the first comment.
  COMMENT  t this is a comment
     ...   OK to replace ? (yes): n		(user types n)
  no action taken
  :q
  tt&gt;
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_references">REFERENCES</A></H2>
  <! BeginSection: 'REFERENCES'>
  <UL>
  This task was written by Phil Hodge.
  </UL>
  <! EndSection:   'REFERENCES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  tprint, tdump, tedit
  <P>
  Type "<TT>help tables opt=sys</TT>" for a higher-level description of the 'tables' 
  package.
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'PARAMETERS' 'EXAMPLES' 'BUGS' 'REFERENCES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>