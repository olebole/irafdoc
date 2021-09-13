.. _imtile:

imtile — Tile same sized 2D images into a 2D mosaic
===================================================

**Package: imutil**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  imtile -- mosaic a list of same size images into a tile pattern
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  imtile input output nctile nltile
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>The list of input image tiles to be mosaiced. The image tile list is assumed
  to be ordered by row, column, or in a raster pattern. If the image tile list
  is not in order then the files or sections tasks plus the editor must be used
  to construct an ordered image tile list. The images in the input list must
  all be the same size.
  </DD>
  </DL>
  <DL>
  <DT><B>output</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>The name of the output image.
  </DD>
  </DL>
  <DL>
  <DT><B>nctile</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nctile' Line='nctile'>
  <DD>The number of image tiles to be placed along a row of the output image.
  </DD>
  </DL>
  <DL>
  <DT><B>nltile</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nltile' Line='nltile'>
  <DD>The number of image tiles to be placed along a column of the output image.
  </DD>
  </DL>
  <DL>
  <DT><B>trim_section = "<TT>[*,*]</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='trim_section' Line='trim_section = "[*,*]"'>
  <DD>The section of the input image tiles to be inserted into the output image.
  Trim_section can be used to flip and / or trim the individual image tiles
  before adding them to the mosaic. For example if we want to flip each
  image tile around the y axis before adding it to the mosaic, then
  <I>trim_section</I> should be set to "<TT>[*,-*]</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>missing_input = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='missing_input' Line='missing_input = ""'>
  <DD>The list of missing image tiles. For example if image tiles 3 to 5 and
  10 from a sequence of image tiles are missing then <I>missing_input</I> =
  "<TT>3-5,10</TT>". This parameter uses the IRAF ranges syntax. The number of missing
  image tiles plus the number of input image tiles must equal <I>nctile</I> *
  <I>nltile</I>.
  </DD>
  </DL>
  <DL>
  <DT><B>start_tile = "<TT>ll</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='start_tile' Line='start_tile = "ll"'>
  <DD>The position of the first input image tile placed in the output image mosaic.
  The four options are "<TT>ll</TT>" for lower left corner, "<TT>lr</TT>" for lower right corner,
  "<TT>ul</TT>" for upper left corner and "<TT>ur</TT>" for upper right corner.
  </DD>
  </DL>
  <DL>
  <DT><B>row_order = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='row_order' Line='row_order = yes'>
  <DD>Add the input image tiles to the output image in row order. If row_order is
  "<TT>no</TT>" then column order is used instead.
  </DD>
  </DL>
  <DL>
  <DT><B>raster_order = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='raster_order' Line='raster_order = no'>
  <DD>Add the input image tiles to the output image in a raster pattern or return
  to the start of a column or a row before adding a new image tile ?
  </DD>
  </DL>
  <DL>
  <DT><B>median_section = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='median_section' Line='median_section = ""'>
  <DD>The section of each input image tile used to compute the median value. If
  <I>median_section</I> is the null string then the medians are not computed.
  If <I>median_section</I> is "<TT>[*,*]</TT>" the entire input image tile is used to
  compute the median.
  </DD>
  </DL>
  <DL>
  <DT><B>subtract = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='subtract' Line='subtract = no'>
  <DD>Subtract the median value from each input image tile before placing the
  tile in the output image?
  </DD>
  </DL>
  <DL>
  <DT><B>ncols = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ncols' Line='ncols = INDEF'>
  <DD>The number of columns in the output image. If <I>ncols</I> is INDEF then
  the program will compute the number of columns using the size of the input
  image tiles, <I>nctile</I>, and <I>ncoverlap</I>.
  </DD>
  </DL>
  <DL>
  <DT><B>nlines = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nlines' Line='nlines = INDEF'>
  <DD>The number of lines in the output image. If <I>nlines</I> is INDEF then
  the program will compute the number of lines using the size of the input
  image tiles, <I>nltile</I> and <I>nloverlap</I>.
  </DD>
  </DL>
  <DL>
  <DT><B>ncoverlap = -1</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ncoverlap' Line='ncoverlap = -1'>
  <DD>The number of columns between adjacent tiles in the output image. A negative
  value specifies the amount of column space between adjacent tiles. A positive
  value specifies the amount of column overlap on adjacent tiles.
  </DD>
  </DL>
  <DL>
  <DT><B>nloverlap = -1</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nloverlap' Line='nloverlap = -1'>
  <DD>The number of lines between adjacent tiles in the output image. A negative
  value specifies the amount of lines space between adjacent tiles. A positive
  value specifies the amount of line overlap on adjacent tiles.
  </DD>
  </DL>
  <DL>
  <DT><B>ovalue = 0.0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ovalue' Line='ovalue = 0.0'>
  <DD>The output image pixel value in regions undefined by the list of input
  image tiles.
  </DD>
  </DL>
  <DL>
  <DT><B>opixtype = "<TT>r</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='opixtype' Line='opixtype = "r"'>
  <DD>The pixel type of the output image. The options are "<TT>s</TT>" (short integer),
  "<TT>i</TT>" (integer), "<TT>u</TT>" (ushort), "<TT>l</TT>" (long integer), "<TT>r</TT>" (real) and
  "<TT>d</TT>" for double precision.
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes'>
  <DD>Print messages about the progress of the task?
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  IMTILE takes the list of same size input images (image tiles) specified by
  <I>input</I> and combines them into a tiled output image mosaic <I>output</I>.
  The order in which the input image tiles are placed in the output image is
  determined by the parameters <I>start_tile</I>, <I>row_order</I> and
  <I>raster_order</I>. The orientation of each individual image tile in the
  output image is set by the <I>trim_section</I> parameter.
  <P>
  IMTILE uses the input image tile size, the number of image tiles, the
  <I>ncoverlap</I> and nloverlap<I> parameters, and the fInctile</I> and
  <I>nltile</I> parameters to compute the size of the output image. An image
  of size larger than the minimum required can be specified by setting the
  <I>ncols</I> and <I>nlines</I> parameters. The pixel type of the output
  image is specified by the <I>opixtype</I> parameter and undefined
  regions of the output image are assigned the value <I>ovalue</I>.
  <P>
  The median of a section of each input image tile is computed by setting
  the <I>median_section</I> parameter,  and the computed median is subtracted
  from the input image tiles if the <I>subtract</I> parameter is set to "<TT>yes</TT>".
  Task action messages will be printed on the standard output
  if <I>verbose</I> is set to yes.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Mosaic a list of 64 images onto an 8 by 8 grid in column order
  starting in the upper right hand corner. Allow one blank column and row
  between each subraster.
  <P>
  <PRE>
      cl&gt; imtile @imlist mosaic 8 8 ncoverlap=-1 nloverlap=-1 \<BR>
          start_tile="ur" row-
  </PRE>
  <P>
  2. Mosaic a list of 62 images onto an 8 by 8 grid in column order
  starting in the upper right hand corner. Allow one blank column and row
  between each subraster. Subrasters 3 and 9 in the sequence do not exist
  and are to be replaced in the output image with an unknown value of -1.0.
  <P>
  <PRE>
      cl&gt; imtile @imlist mosaic 8 8 nxoverlap=-1 nyoverlap=-1  \<BR>
          start_corner="ur" row- missing_input="3,9", ovalue=-1.0
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Time requirements</H3>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  <P>
  </UL>
  <! EndSection:   'TIME REQUIREMENTS'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  <P>
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  imcombine
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
