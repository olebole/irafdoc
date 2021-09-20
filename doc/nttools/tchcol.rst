.. _tchcol:

tchcol: Change column name, print format, or units.
===================================================

**Package: nttools**

.. raw:: html

  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  tchcol table oldname newname newfmt newunits
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  This task may be used to change the name of a column, the display
  format, or the units.
  To change more than one column the task must be called more than once.
  Only those items (name, units, format) that are not null will be changed.
  The word <span style="font-family: monospace;">"default"</span> may be used to set 
  the print format or the units to their default values.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>table [file name template]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='table' Line='table [file name template]' -->
  <dd>Names of tables to be modified.
  The same change(s) will be made to all tables.
  Note that the tables are modified in-place.
  </dd>
  </dl>
  <dl>
  <dt><b>oldname = <span style="font-family: monospace;">""</span> [string]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='oldname' Line='oldname = "" [string]' -->
  <dd>Name of column to be changed.
  If the column is not found,
  a message will be printed,
  and the current table will not be changed.
  </dd>
  </dl>
  <dl>
  <dt><b>newname = <span style="font-family: monospace;">""</span> [string]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='newname' Line='newname = "" [string]' -->
  <dd>New column name or a null string (<span style="font-family: monospace;">""</span>).
  If this is null or blank, the column name will not be changed.
  </dd>
  </dl>
  <dl>
  <dt><b>newfmt = <span style="font-family: monospace;">""</span> [string]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='newfmt' Line='newfmt = "" [string]' -->
  <dd>New value for print format, or <span style="font-family: monospace;">"default"</span> or <span style="font-family: monospace;">""</span>.
  If this is null or blank, the display format will not be changed.
  If 'newfmt = <span style="font-family: monospace;">"default"</span>' the print format will be set to the default
  for the column data type.
  Type <span style="font-family: monospace;">"help ttools opt=sysdoc"</span> for more information about print formats.
  </dd>
  </dl>
  <dl>
  <dt><b>newunits = <span style="font-family: monospace;">""</span> [string]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='newunits' Line='newunits = "" [string]' -->
  <dd>New value for units, or <span style="font-family: monospace;">"default"</span> or <span style="font-family: monospace;">""</span>.
  If this is null or blank the units will not be changed.
  If newunits = <span style="font-family: monospace;">"default"</span> the units will be set to null.
  There is no way (with this task) to set the units to the value <span style="font-family: monospace;">"default"</span>!
  </dd>
  </dl>
  <dl>
  <dt><b>(verbose = yes) [boolean]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='' Line='(verbose = yes) [boolean]' -->
  <dd>Print the names of tables as the task progresses?
  If 'verbose=yes' then the table names are printed,
  and for each item that is changed, a message is printed
  giving the old and new values.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  In table 'm87pol.tab', change column name <span style="font-family: monospace;">"chi"</span> to <span style="font-family: monospace;">"CHI"</span> and set the units
  to degrees.  The display format is not changed.
  </p>
  <pre>
  tt&gt; tchcol m87pol chi CHI "" degrees
  </pre>
  <p>
  In the same table, set the units of column <span style="font-family: monospace;">"P"</span> to null.
  The name and format are not changed.
  </p>
  <pre>
  tt&gt; tchcol m87pol P "" "" default
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <!-- EndSection:   'BUGS' -->
  <h3>References</h3>
  <!-- BeginSection: 'REFERENCES' -->
  <p>
  This task was written by J.C. Hsu and was modified by Phil Hodge.
  </p>
  <!-- EndSection:   'REFERENCES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'PARAMETERS' 'EXAMPLES' 'BUGS' 'REFERENCES' 'SEE ALSO'  -->
  
