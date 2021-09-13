.. _irmosaic:

irmosaic — Mosaic an ordered list of images onto a grid
=======================================================

**Package: nproto**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  irmosaic -- mosaic a set of infrared ccd images
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  mosaic input output database nxsub nysub
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>The list of input images to be mosaiced. The images are
  assumed to be ordered either by row,
  column, or in a raster pattern. If the image list is not in
  order then the iraf files task plus the editor must be used
  to construct an image list.  The images in the input list 
  are assumed to all be the same size.
  </DD>
  </DL>
  <DL>
  <DT><B>output</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>The name of the output image.
  </DD>
  </DL>
  <DL>
  <DT><B>database</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='database' Line='database'>
  <DD>The name of the text file listing the operations performed by irmosaic.
  This list can be used as input for iralign.
  </DD>
  </DL>
  <DL>
  <DT><B>nxsub</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nxsub' Line='nxsub'>
  <DD>The number of subrasters along a row of the output image.
  </DD>
  </DL>
  <DL>
  <DT><B>nysub</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nysub' Line='nysub'>
  <DD>The number of subrasters along a column of the output image.
  </DD>
  </DL>
  <DL>
  <DT><B>trim_section = "<TT>[*,*]</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='trim_section' Line='trim_section = "[*,*]"'>
  <DD>The section of the input images to be mosaiced into the output image.
  Section can be used to flip and/or trim the individual subrasters before adding
  them to the mosaic. For example if we want to flip each subraster around the
  y axis before adding it to the mosaic, then <I>trim_section</I> = "<TT>[*,-*]</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>null_input = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='null_input' Line='null_input = ""'>
  <DD>The list of unobserved subrasters. For example if the subrasters 3 to 5 and
  10 of a sequence of observations were not observed then
  <I>null_input</I> = "<TT>3-5,10</TT>".
  This parameter follows the ranges notation convention. The number of unobserved
  subrasters plus the number of images must equal <I>nxsub</I> *
  <I>nysub</I>.
  </DD>
  </DL>
  <DL>
  <DT><B>corner = "<TT>ll</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='corner' Line='corner = "ll"'>
  <DD>The starting position in the output image.
  The four options are "<TT>ll</TT>" for lower left corner, "<TT>lr</TT>" for lower right corner,
  "<TT>ul</TT>" for upper left corner and "<TT>ur</TT>" for upper right corner.
  </DD>
  </DL>
  <DL>
  <DT><B>direction = "<TT>row</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='direction' Line='direction = "row"'>
  <DD>Add subrasters to the output image in row or column order. The options are
  "<TT>row</TT>" for row order and "<TT>column</TT>" for column order.
  </DD>
  </DL>
  <DL>
  <DT><B>raster = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='raster' Line='raster = no'>
  <DD>Add subrasters to the output image in a raster pattern or return to the start
  of a column or a row?
  </DD>
  </DL>
  <DL>
  <DT><B>median_section = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='median_section' Line='median_section = ""'>
  <DD>The section of each input subraster for which the median is computed. If
  <I>median_section</I> is the null string then the medians are not computed.
  If <I>median_section</I> is "<TT>[*,*]</TT>" the whole input subraster is used to
  compute the median.
  </DD>
  </DL>
  <DL>
  <DT><B>subtract = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='subtract' Line='subtract = no'>
  <DD>Subtract the median value from each input subraster before placing the
  subraster in the output image.
  </DD>
  </DL>
  <DL>
  <DT><B>nimcols = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nimcols' Line='nimcols = INDEF'>
  <DD>The number of columns in the output image. If <I>nimcols</I> is INDEF then
  the program will compute the number of columns using the size of the input
  subrasters, <I>nxsub</I> and <I>nxoverlap</I>.
  </DD>
  </DL>
  <DL>
  <DT><B>nimrows = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nimrows' Line='nimrows = INDEF'>
  <DD>The number of rows in the output image. If <I>nimrows</I> is INDEF then
  the program will compute the number of rows using the size of the input
  subrasters, <I>nysub</I> and <I>nyoverlap</I>.
  </DD>
  </DL>
  <DL>
  <DT><B>nxoverlap = -1</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nxoverlap' Line='nxoverlap = -1'>
  <DD>The number of columns between adjacent frames. A negative value specifies 
  the amount of column space between adjacent subrasters.
  A positive value specifies the amount of column overlap on adjacent
  subrasters.
  </DD>
  </DL>
  <DL>
  <DT><B>nyoverlap = -1</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nyoverlap' Line='nyoverlap = -1'>
  <DD>The number of rows between adjacent frames. A negative value specifies
  the amount of row space between adjacent subrasters.
  A positive value specifies the amount of row overlap on adjacent subrasters.
  </DD>
  </DL>
  <DL>
  <DT><B>oval = 0.0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='oval' Line='oval = 0.0'>
  <DD>The output image pixel value in regions undefined by the by the list of input
  images.
  </DD>
  </DL>
  <DL>
  <DT><B>opixtype = "<TT>r</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='opixtype' Line='opixtype = "r"'>
  <DD>The pixel type of the output image. The options are "<TT>s</TT>" (short integer),
  "<TT>i</TT>" (integer), "<TT>l</TT>" (long integer), "<TT>r</TT>" (real) and "<TT>d</TT>" for double
  precision.
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes'>
  <DD>Print messages about task progress and actions taken.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  IRMOSAIC takes a the list of subrasters of identical dimensions specified
  by <I>input</I> and combines them into a single
  output image <I>output</I>. The order in which the subrasters are placed
  in the output image is determined by the parameters <I>corner</I>,
  <I>direction</I> and <I>raster</I>. The orientation of each individual
  subraster in the output image may be altered by setting the <I>trim_section</I>
  parameter.
  <P>
  IRMOSAIC uses the subraster size, the number of subrasters, the <I>nxoverlap</I>
  and nyoverlap<I> parameters and the fInxsub</I> and <I>nysub</I> partmeters
  to compute the size of the output image. An image of size larger than the
  minimum required can be specified by setting <I>nimcols</I> and <I>nimrows</I>. 
  The pixel type of the output image is specified by <I>opixtype</I> and undefined
  regions of the output image are given the value <I>oval</I>.
  <P>
  The median of a section each subraster may be optionally computed
  and placed in the database file by setting <I>median_section</I>.
  The computed median will be subtracted from the input subrasters if
  <I>subtract</I> is set to yes.
  Task action messages will be printed on the standard output
  if <I>verbose</I> is set to yes.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Mosaic a list of 64 infrared images onto an 8 by 8 grid in column order
  starting in the upper right hand corner. Allow one blank column and row
  between each subraster.
  <P>
  <PRE>
      pr&gt; irmosaic @imlist mosaic mosaic.dat nxsub=8 nysub=8 \<BR>
  	nxoverlap=-1 nyoverlap=-1 corner="ur" direct="column"
  </PRE>
  <P>
  2. Mosaic a list of 62 infrared images onto an 8 by 8 grid in column order
  starting in the upper right hand corner. Allow one blank column and row
  between each subraster. Subrasters 3 and 9 in the sequence do not exist
  and are to be replaced in the output image with an unknown value of -1.0.
  <P>
  <PRE>
      pr&gt; irmosaic @imlist mosaic mosaic.dat nxsub=8 nysub=8 \<BR>
  	nxoverlap=-1 nyoverlap=-1 corner="ur" direct="column"\<BR>
  	null_input="3,9", oval=-1.0
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Time requirements</H3>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  </UL>
  <! EndSection:   'TIME REQUIREMENTS'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  At present only integral pixel overlaps are allowed in this routine.
  Fine tuning of the alignments can be done with iralign.
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  iralign, irmatch1d, irmatch2d
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
