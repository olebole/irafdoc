tchcol — Change column name, print format, or units.
====================================================

**Package: nttools**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>tchcol (Jan92)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>tables</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>tchcol (Jan92)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>tchcol</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  tchcol -- Change column description.
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  tchcol table oldname newname newfmt newunits
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  This task may be used to change the name of a column, the display
  format, or the units.
  To change more than one column the task must be called more than once.
  Only those items (name, units, format) that are not null will be changed.
  The word "<TT>default</TT>" may be used to set 
  the print format or the units to their default values.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_table">table [file name template]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='table' Line='table [file name template]'>
  <DD>Names of tables to be modified.
  The same change(s) will be made to all tables.
  <P>
  Note that the tables are modified in-place.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_oldname">oldname = "<TT></TT>" [string]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='oldname' Line='oldname = "" [string]'>
  <DD>Name of column to be changed.
  If the column is not found,
  a message will be printed,
  and the current table will not be changed.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_newname">newname = "<TT></TT>" [string]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='newname' Line='newname = "" [string]'>
  <DD>New column name or a null string ("<TT></TT>").
  <P>
  If this is null or blank, the column name will not be changed.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_newfmt">newfmt = "<TT></TT>" [string]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='newfmt' Line='newfmt = "" [string]'>
  <DD>New value for print format, or "<TT>default</TT>" or "<TT></TT>".
  <P>
  If this is null or blank, the display format will not be changed.
  If 'newfmt = "<TT>default</TT>"' the print format will be set to the default
  for the column data type.
  Type "<TT>help ttools opt=sysdoc</TT>" for more information about print formats.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_newunits">newunits = "<TT></TT>" [string]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='newunits' Line='newunits = "" [string]'>
  <DD>New value for units, or "<TT>default</TT>" or "<TT></TT>".
  <P>
  If this is null or blank the units will not be changed.
  If newunits = "<TT>default</TT>" the units will be set to null.
  There is no way (with this task) to set the units to the value "<TT>default</TT>"!
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(verbose = yes) [boolean]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(verbose = yes) [boolean]'>
  <DD>Print the names of tables as the task progresses?
  <P>
  If 'verbose=yes' then the table names are printed,
  and for each item that is changed, a message is printed
  giving the old and new values.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  In table 'm87pol.tab', change column name "<TT>chi</TT>" to "<TT>CHI</TT>" and set the units
  to degrees.  The display format is not changed.
  <P>
  <PRE>
  tt&gt; tchcol m87pol chi CHI "" degrees
  </PRE>
  <P>
  In the same table, set the units of column "<TT>P</TT>" to null.
  The name and format are not changed.
  <P>
  <PRE>
  tt&gt; tchcol m87pol P "" "" default
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
  This task was written by J.C. Hsu and was modified by Phil Hodge.
  </UL>
  <! EndSection:   'REFERENCES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'PARAMETERS' 'EXAMPLES' 'BUGS' 'REFERENCES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>