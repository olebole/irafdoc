text2mask — Convert text description to pixel mask
==================================================

**Package: proto**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>text2mask (Jun96)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>proto</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>text2mask (Jun96)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>text2mask</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  text2mask -- convert text description to pixel mask
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage_">USAGE	</A></H2>
  <! BeginSection: 'USAGE	'>
  <UL>
  <PRE>
  text2mask text mask ncols nlines
  </PRE>
  </UL>
  <! EndSection:   'USAGE	'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_text">text</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='text' Line='text'>
  <DD>Text file of pixel regions.  The format of this file consists of lines of
  individual pixels (whitespace separated column and line) or rectangular
  regions (whitespace separated starting and ending columns and starting and
  ending lines).
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_mask">mask</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='mask' Line='mask'>
  <DD>Pixel mask name to be created.  A pixel list image, .pl extension,
  is created so no extension is necessary.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_ncols">ncols, nlines</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ncols' Line='ncols, nlines'>
  <DD>Dimensions for pixel mask image.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_linterp">linterp = 1</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='linterp' Line='linterp = 1'>
  <DD>Mask code for rectangular regions which are narrower in the line direction
  than the column direction.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_cinterp">cinterp = 2</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='cinterp' Line='cinterp = 2'>
  <DD>Mask code for rectangular regions which are narrower in the column direction
  than the line direction.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_square">square = 3</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='square' Line='square = 3'>
  <DD>Mask code for square regions which are larger than a single pixel.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_pixel">pixel = 4</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='pixel' Line='pixel = 4'>
  <DD>Mask code for single pixels.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  A text file describing individual pixels or rectangular regions is
  converted to a pixel mask image in pixel list format.  The name of
  the text file, the name of the pixel mask to be created, and the
  dimensions of the pixel mask image are specified.
  <P>
  The text file consists of lines of two or four numbers.  If two numbers
  are given, separated by whitespace, they define a single pixel and
  the values are the column and line pixel coordinates.  If four numbers
  are given, separated by whitespace, they define a rectangular region.
  The four numbers are the pixel coordinates for the starting column,
  the ending column, the starting line, and the ending line.  This format
  is the same as the old (pre-V2.11) "<TT>fixpix</TT>" format.  This task may
  be used to convert these old "<TT>fixpix</TT>" data files to pixel masks (as used
  by the new <B>fixpix</B> task) or to create pixel masks.
  <P>
  The different region shapes may be coded by the mask values.  This is
  useful with the <B>fixpix</B> task which can select different replacement
  methods based on the mask codes.  In particular, one may want to interpolate
  along the narrower dimension of a rectangular region.  The region
  shapes that may be coded are individual pixels, square regions, and
  rectangular regions with narrow dimension along lines or columns.
  <P>
  In addition to this task,
  pixel mask images may be made in a variety of ways.  Any task which produces
  and modifies image values may be used.  Some useful tasks are
  <B>imexpr, imreplace, imcopy,</B> and <B>mkpattern</B>.  If a new image
  is specified with the explicit "<TT>.pl</TT>" extension then the pixel mask
  format is produced.  Another way to make masks are with the
  task <B>ccdmask</B>.  The task <B>ccdmask</B> is specialized to make a mask
  of bad pixels from flat fields or, even better, from the ratio of
  two flat fields of different exposure levels.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1.  Convert a text region description into a mask and then use it to
  replace pixels by interpolation along the narrower dimension.
  <P>
  <PRE>
      cl&gt; list2mask fp.dat mask
      cl&gt; fixpix pix mask linterp=1,3,4 cinterp=2
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_revisions">REVISIONS</A></H2>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_TEXT2MASK">TEXT2MASK V2.11</A></B></DT>
  <! Sec='REVISIONS' Level=0 Label='TEXT2MASK' Line='TEXT2MASK V2.11'>
  <DD>This task is new and appears in conjunction with a new pixel mask
  based version of <B>fixpix</B>.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'REVISIONS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  imreplace, imexpr, imcopy, imedit, fixpix
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE	' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'REVISIONS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>