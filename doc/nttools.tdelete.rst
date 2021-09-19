.. _tdelete:

tdelete: Delete tables.
=======================

**Package: nttools**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  tdelete -- Delete a table.
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  tdelete table
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  This task deletes tables.
  The input may be a general filename template,
  including wildcard characters, or the name of a list file
  (preceded by the <tt>"@"</tt> character) containing table names.
  </p>
  <p>
  The task checks that the file to be deleted really is a table
  before deleting it.
  In order to protect against accidental deletion of files other than tables,
  text tables may be deleted using 'tdelete' only if 'verify = yes'.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>table [file name template]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='table' Line='table [file name template]' -->
  <dd>A list of one or more tables to be deleted.
  </dd>
  </dl>
  <dl>
  <dt><b>(verify = no) [boolean]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='' Line='(verify = no) [boolean]' -->
  <dd>Prompt for confirmation before deleting?  It is possible to delete
  text tables using 'tdelete' if 'verify' is set to <tt>"yes"</tt>.
  </dd>
  </dl>
  <dl>
  <dt><b>(default_action = yes) [boolean]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='' Line='(default_action = yes) [boolean]' -->
  <dd>Default action for the verify query.  If 'default_action = yes', then the
  prompt will come back with <tt>"yes?"</tt> and striking return will proceed with
  the delete.
  </dd>
  </dl>
  <dl>
  <dt><b>go_ahead = yes [boolean]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='go_ahead' Line='go_ahead = yes [boolean]' -->
  <dd>This is a copy of 'default_action' used for prompting if 'verify = yes'.
  This parameter is set by the task, it copies the value of 'default_action',
  but cannot be directly set by the user.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Delete a single table.
  </p>
  <pre>
  	cl&gt; tdelete table
  </pre>
  <p>
  2. Delete several tables.
  </p>
  <pre>
  	cl&gt; tdelete table1,table2,tab67
  	cl&gt; tdelete *.tab,a,b,c
  
  </pre>
  <p>
  In the latter case, the extension is given explicitly because there may be
  other files beginning with <tt>"tab"</tt> that are not tables.
  </p>
  <p>
  3. Delete a list of tables using verify.
  </p>
  <pre>
  	cl&gt; tdelete fits*.tab ver+
  	cl&gt; delete table `fits1.tab' ? (yes): yes
  	cl&gt; delete table `fits2.tab' ? (yes): yes
  	cl&gt; delete table `fits3.tab' ? (yes): yes
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <p>
  Text tables cannot be deleted by 'tdelete' unless 'verify' is set to yes.
  </p>
  <!-- EndSection:   'BUGS' -->
  <h3>References</h3>
  <!-- BeginSection: 'REFERENCES' -->
  <p>
  This task was written by Phil Hodge.
  </p>
  <!-- EndSection:   'REFERENCES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  delete, tcopy, trename
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'PARAMETERS' 'EXAMPLES' 'BUGS' 'REFERENCES' 'SEE ALSO'  -->
  
