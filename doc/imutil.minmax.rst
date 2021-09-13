minmax — Compute the minimum and maximum pixel values in an image
=================================================================

**Package: imutil**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>minmax (May91)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>images.imutil</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>minmax (May91)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>minmax</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  minmax -- compute the minimum and maximum pixel values of an image
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  minmax images
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_images">images</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='images' Line='images'>
  <DD>Image template specifying the images to be examined.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_force">force = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='force' Line='force = no'>
  <DD>Force recomputation of the minimum and maximum pixel and pixel values even if
  they are noted as up to date in the image header.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_update">update = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='update' Line='update = yes'>
  <DD>Update the image header with the new values (requires write permission).
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_verbose">verbose = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes'>
  <DD>Print the image name, minimum value, and maximum value of each image
  processed.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_minval">minval = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='minval' Line='minval = INDEF'>
  <DD>Set to the minimum pixel value of the last image processed.
  If the pixel type of the last input image was complex, this is the real
  part of the minimum value.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_maxval">maxval = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='maxval' Line='maxval = INDEF'>
  <DD>Set to the maximum pixel value of the last image processed.
  If the pixel type of the last input image was complex, this is the real
  part of the maximum value.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_iminval">iminval = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='iminval' Line='iminval = INDEF'>
  <DD>Set to the minimum imaginary part of the pixel value of the last image
  processed. Only used if the pixel type of the last input image was complex.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_imaxval">imaxval = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='imaxval' Line='imaxval = INDEF'>
  <DD>Set to the maximum imaginary part of the pixel value of the last image
  processed. Only used if the pixel type of the last input image was complex.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_minpix">minpix = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='minpix' Line='minpix = ""'>
  <DD>Set to the minimum pixel specification of the last image processed.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_maxpix">maxpix = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='maxpix' Line='maxpix = ""'>
  <DD>Set to the maximum pixel specification of the last image processed.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
      The <I>minmax</I> task computes the minimum and maximum pixel and pixel
  values of
  each of the images or image sections listed in the image template <I>images</I>.
  If the <I>force</I> option is set the extreme values will be recomputed by
  physical examination of the data, otherwise the image is examined only if the
  extreme values stored in the image header are flagged as invalid.
  The minimum and maximum pixel will be printed only if the force option
  is enabled or if the image minimum and maximum is out of date. 
  If the <I>update</I> option is set the image header will be updated with the
  newly computed values.  Updating is not allowed when a section is used to
  compute the new values.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Compute and print the minimum and maximum values of the images <I>image1</I>
  and <I>image2</I>, updating the image header with the new values when done.
  <P>
  <PRE>
  	cl&gt; minmax image1,image2
  </PRE>
  <P>
  2. Force update the minimum and maximum values in the image headers of all
  images matching the template in the background, without printing the computed
  values on the terminal.
  <P>
  	cl&gt; minmax nite1.* force+ verbose- &amp;
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  The minimum and maximum pixel values are stored in the image header as values
  of type real, hence some precision may be lost for images of type long integer
  or double precision floating.
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  imheader, hedit
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>