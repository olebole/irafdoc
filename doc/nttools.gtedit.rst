.. _gtedit:

gtedit — Graphically edit a table.
==================================

**Package: nttools**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  gtedit -- Graphically edit an STSDAS table.
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  gtedit input xcolumn ycolumn
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The 'gtedit' task lets you graphically edit 
  an STSDAS table.
  You can use the editor to delete rows. You can
  also choose whether to overwrite the existing
  file (by setting 'inplace=yes') or you
  can create a new output table. You can also
  save deleted points in a separate file by
  setting the 'reject' parameter to an output
  file name.
  <P>
  The rows that are plotted can be selected using the :x and :y
  commands to specify columns for the X and Y axes. Points that
  are to be deleted will be marked with an "<TT>x</TT>" (this information
  is retained if columns change).
  <P>
  To mark a point for deletion you can:
  <PRE>
  1) Specify the points individually
  2) Define a box in which all points will be deleted
  3) Delete all points on one side of the cursor or line segment
  </PRE>
  <P>
  You can also toggle between "<TT>delete mode</TT>" and "<TT>undelete mode</TT>". When
  you are in undelete mode, any previously-deleted points that you
  selected will be unmarked.
  <P>
  If you don't like using 'gtedit', you can switch to the 'tedit'
  task and edit the table in the usual manner.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Cursor commands</H3>
  <! BeginSection: 'CURSOR COMMANDS'>
  <UL>
  <P>
  <PRE>
  	GTEDIT Interactive Cursor Commands
  <P>
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
  q	quit and do not save changes made since the last <TT>'f'</TT>
  r	delete all points with X values greater than the cursor X position
  s	mark one end of a line segment
  t	delete all points with Y values greater than the cursor Y position
  u	toggle between delete and undelete mode
  v	change from gtedit to tedit mode
  z	display current status (delete or undelete)
  <P>
  :x(-) xcolumn	set the table column for the X axis and possibly replot
  :y(-) ycolumn	set the table column for the Y axis and possibly replot
  - do not automatically replot after reading in new column
  <P>
  </PRE>
  </UL>
  <! EndSection:   'CURSOR COMMANDS'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input [file name]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input [file name]'>
  <DD>The input table to be edited.
  </DD>
  </DL>
  <DL>
  <DT><B>xcolumn</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xcolumn' Line='xcolumn'>
  <DD>The name of the column in the input table to use for the X-axis of the plot.
  </DD>
  </DL>
  <DL>
  <DT><B>ycolumn</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ycolumn' Line='ycolumn'>
  <DD>The name of the column in the input table to use for the Y-axis of the plot.
  </DD>
  </DL>
  <DL>
  <DT><B>(device = "<TT>stdgraph</TT>")</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(device = "stdgraph")'>
  <DD>The standard graphics device.
  </DD>
  </DL>
  <DL>
  <DT><B>(commands = "<TT></TT>")</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(commands = "")'>
  <DD>The graphics cursor.
  </DD>
  </DL>
  <DL>
  <DT><B>(inplace = no)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(inplace = no)'>
  <DD>Edit the table inplace. No new output table is created and the original
  table is overwritten.
  </DD>
  </DL>
  <DL>
  <DT><B>(output = "<TT></TT>")</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(output = "")'>
  <DD>The name of the output table if the input table is not edited inplace. If
  inplace = no then output should be a valid filename.
  </DD>
  </DL>
  <DL>
  <DT><B>(reject = "<TT></TT>")</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(reject = "")'>
  <DD>If this parameter contains a valid filename then this table will contain
  the points which were deleted using this task.
  </DD>
  </DL>
  <DL>
  <DT><B>(gtpar = "<TT></TT>") [pset]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(gtpar = "") [pset]'>
  <DD>The name of the pset containing the parameters which describe the plot
  attributes.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Edit a table containing the output photometry from DAOPHOT. 
  Initially plot the magnitude (MAG) versus the error in the magnitude (MAGERR)
  to decide which points to delete.
  <P>
  <PRE>
       st&gt; gtedit m31.mag MAG MERR
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
  This task was written by Dennis Crabtree.
  </UL>
  <! EndSection:   'REFERENCES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'CURSOR COMMANDS' 'PARAMETERS' 'EXAMPLES' 'BUGS' 'REFERENCES' 'SEE ALSO'  >
  
