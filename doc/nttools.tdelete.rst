tdelete — Delete tables.
========================

**Package: nttools**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>tdelete (Aug93)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>tables</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>tdelete (Aug93)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>tdelete</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  tdelete -- Delete a table.
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  tdelete table
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  This task deletes tables.
  The input may be a general filename template,
  including wildcard characters, or the name of a list file
  (preceded by the "<TT>@</TT>" character) containing table names.
  <P>
  The task checks that the file to be deleted really is a table
  before deleting it.
  In order to protect against accidental deletion of files other than tables,
  text tables may be deleted using 'tdelete' only if 'verify = yes'.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_table">table [file name template]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='table' Line='table [file name template]'>
  <DD>A list of one or more tables to be deleted.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(verify = no) [boolean]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(verify = no) [boolean]'>
  <DD>Prompt for confirmation before deleting?  It is possible to delete
  text tables using 'tdelete' if 'verify' is set to "<TT>yes</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(default_action = yes) [boolean]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(default_action = yes) [boolean]'>
  <DD>Default action for the verify query.  If 'default_action = yes', then the
  prompt will come back with "<TT>yes?</TT>" and striking return will proceed with
  the delete.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_go_ahead">go_ahead = yes [boolean]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='go_ahead' Line='go_ahead = yes [boolean]'>
  <DD>This is a copy of 'default_action' used for prompting if 'verify = yes'.
  This parameter is set by the task, it copies the value of 'default_action',
  but cannot be directly set by the user.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Delete a single table.
  <P>
  <PRE>
  	cl&gt; tdelete table
  </PRE>
  <P>
  2. Delete several tables.
  <P>
  <PRE>
  	cl&gt; tdelete table1,table2,tab67
  	cl&gt; tdelete *.tab,a,b,c
  <P>
  </PRE>
  In the latter case, the extension is given explicitly because there may be
  other files beginning with "<TT>tab</TT>" that are not tables.
  <P>
  3. Delete a list of tables using verify.
  <P>
  <PRE>
  	cl&gt; tdelete fits*.tab ver+
  	cl&gt; delete table `fits1.tab' ? (yes): yes
  	cl&gt; delete table `fits2.tab' ? (yes): yes
  	cl&gt; delete table `fits3.tab' ? (yes): yes
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  Text tables cannot be deleted by 'tdelete' unless 'verify' is set to yes.
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
  delete, tcopy, trename
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'PARAMETERS' 'EXAMPLES' 'BUGS' 'REFERENCES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>