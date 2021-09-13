.. _tdelete:

tdelete — Delete tables.
========================

**Package: nttools**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  tdelete -- Delete a table.
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  tdelete table
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Description</H3>
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
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>table [file name template]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='table' Line='table [file name template]'>
  <DD>A list of one or more tables to be deleted.
  </DD>
  </DL>
  <DL>
  <DT><B>(verify = no) [boolean]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(verify = no) [boolean]'>
  <DD>Prompt for confirmation before deleting?  It is possible to delete
  text tables using 'tdelete' if 'verify' is set to "<TT>yes</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>(default_action = yes) [boolean]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(default_action = yes) [boolean]'>
  <DD>Default action for the verify query.  If 'default_action = yes', then the
  prompt will come back with "<TT>yes?</TT>" and striking return will proceed with
  the delete.
  </DD>
  </DL>
  <DL>
  <DT><B>go_ahead = yes [boolean]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='go_ahead' Line='go_ahead = yes [boolean]'>
  <DD>This is a copy of 'default_action' used for prompting if 'verify = yes'.
  This parameter is set by the task, it copies the value of 'default_action',
  but cannot be directly set by the user.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Examples</H3>
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
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  Text tables cannot be deleted by 'tdelete' unless 'verify' is set to yes.
  </UL>
  <! EndSection:   'BUGS'>
  <H3>References</H3>
  <! BeginSection: 'REFERENCES'>
  <UL>
  This task was written by Phil Hodge.
  </UL>
  <! EndSection:   'REFERENCES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  delete, tcopy, trename
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'PARAMETERS' 'EXAMPLES' 'BUGS' 'REFERENCES' 'SEE ALSO'  >
  
