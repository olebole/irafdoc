.. _gtedit:

gtedit: Graphically edit a table.
=================================

**Package: nttools**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  gtedit -- Graphically edit an STSDAS table.
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  gtedit input xcolumn ycolumn
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  The 'gtedit' task lets you graphically edit 
  an STSDAS table.
  You can use the editor to delete rows. You can
  also choose whether to overwrite the existing
  file (by setting 'inplace=yes') or you
  can create a new output table. You can also
  save deleted points in a separate file by
  setting the 'reject' parameter to an output
  file name.
  </p>
  <p>
  The rows that are plotted can be selected using the :x and :y
  commands to specify columns for the X and Y axes. Points that
  are to be deleted will be marked with an <span style="font-family: monospace;">"x"</span> (this information
  is retained if columns change).
  </p>
  <p>
  To mark a point for deletion you can:
  </p>
  <pre>
  1) Specify the points individually
  2) Define a box in which all points will be deleted
  3) Delete all points on one side of the cursor or line segment
  </pre>
  <p>
  You can also toggle between <span style="font-family: monospace;">"delete mode"</span> and <span style="font-family: monospace;">"undelete mode"</span>. When
  you are in undelete mode, any previously-deleted points that you
  selected will be unmarked.
  </p>
  <p>
  If you don't like using 'gtedit', you can switch to the 'tedit'
  task and edit the table in the usual manner.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Cursor commands</h3>
  <!-- BeginSection: 'CURSOR COMMANDS' -->
  <pre>
  	GTEDIT Interactive Cursor Commands
  
  ?	Print options
  :	Colon commands
  a	print out the complete row for the data point nearest the cursor
  b	delete all points with Y values less than the cursor Y position
  c	mark the corner of a box
  d	delete the point nearest the cursor
  e	exit and save changes in the output table
  f	make all the marked deletions and replot remaining data
  h	print out the column names of the input table
  l	delete all points with X values less than the cursor X position
  p	replot the graph possibly using new data columns
  q	quit and do not save changes made since the last <span style="font-family: monospace;">'f'</span>
  r	delete all points with X values greater than the cursor X position
  s	mark one end of a line segment
  t	delete all points with Y values greater than the cursor Y position
  u	toggle between delete and undelete mode
  v	change from gtedit to tedit mode
  z	display current status (delete or undelete)
  
  :x(-) xcolumn	set the table column for the X axis and possibly replot
  :y(-) ycolumn	set the table column for the Y axis and possibly replot
  - do not automatically replot after reading in new column
  
  </pre>
  <!-- EndSection:   'CURSOR COMMANDS' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>input [file name]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='input' Line='input [file name]' -->
  <dd>The input table to be edited.
  </dd>
  </dl>
  <dl>
  <dt><b>xcolumn</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='xcolumn' Line='xcolumn' -->
  <dd>The name of the column in the input table to use for the X-axis of the plot.
  </dd>
  </dl>
  <dl>
  <dt><b>ycolumn</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='ycolumn' Line='ycolumn' -->
  <dd>The name of the column in the input table to use for the Y-axis of the plot.
  </dd>
  </dl>
  <dl>
  <dt><b>(device = <span style="font-family: monospace;">"stdgraph"</span>)</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='' Line='(device = "stdgraph")' -->
  <dd>The standard graphics device.
  </dd>
  </dl>
  <dl>
  <dt><b>(commands = <span style="font-family: monospace;">""</span>)</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='' Line='(commands = "")' -->
  <dd>The graphics cursor.
  </dd>
  </dl>
  <dl>
  <dt><b>(inplace = no)</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='' Line='(inplace = no)' -->
  <dd>Edit the table inplace. No new output table is created and the original
  table is overwritten.
  </dd>
  </dl>
  <dl>
  <dt><b>(output = <span style="font-family: monospace;">""</span>)</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='' Line='(output = "")' -->
  <dd>The name of the output table if the input table is not edited inplace. If
  inplace = no then output should be a valid filename.
  </dd>
  </dl>
  <dl>
  <dt><b>(reject = <span style="font-family: monospace;">""</span>)</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='' Line='(reject = "")' -->
  <dd>If this parameter contains a valid filename then this table will contain
  the points which were deleted using this task.
  </dd>
  </dl>
  <dl>
  <dt><b>(gtpar = <span style="font-family: monospace;">""</span>) [pset]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='' Line='(gtpar = "") [pset]' -->
  <dd>The name of the pset containing the parameters which describe the plot
  attributes.
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  1. Edit a table containing the output photometry from DAOPHOT. 
  Initially plot the magnitude (MAG) versus the error in the magnitude (MAGERR)
  to decide which points to delete.
  <pre>
       st&gt; gtedit m31.mag MAG MERR
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <!-- EndSection:   'BUGS' -->
  <h3>References</h3>
  <!-- BeginSection: 'REFERENCES' -->
  This task was written by Dennis Crabtree.
  <!-- EndSection:   'REFERENCES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'CURSOR COMMANDS' 'PARAMETERS' 'EXAMPLES' 'BUGS' 'REFERENCES' 'SEE ALSO'  -->
  
