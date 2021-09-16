.. _darksub:

darksub — Scale and subtract a dark count image
===============================================

**Package: generic**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  darksub -- Scale and subtract a dark count image
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage	</H3>
  <! BeginSection: 'USAGE	'>
  <UL>
  darksub input output darkimage
  </UL>
  <! EndSection:   'USAGE	'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>List of input images from which to subtract the dark count image.
  </DD>
  </DL>
  <DL>
  <DT><B>output</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>List of output dark count subtracted images.  The output images may
  be the same as the input images.  The input and output image lists should
  contain the same number of images.
  </DD>
  </DL>
  <DL>
  <DT><B>darkimage</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='darkimage' Line='darkimage'>
  <DD>Dark count image to be scaled and subtracted from the input images.
  </DD>
  </DL>
  <DL>
  <DT><B>exposure = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='exposure' Line='exposure = ""'>
  <DD>Header parameter name from which to obtain the exposure times.
  </DD>
  </DL>
  <DL>
  <DT><B>pixtype = "<TT>1</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='pixtype' Line='pixtype = "1"'>
  <DD>The pixel datatype of the dark subtracted images.  The default ("<TT>1</TT>")
  is the pixel datatype of the original image.  The other choices are
  "<TT>short</TT>", "<TT>integer</TT>", "<TT>long</TT>", "<TT>real</TT>", and "<TT>double</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes'>
  <DD>Print log of operations performed.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The dark count image is scaled by the ratio of the input image exposure to the
  dark count image exposure and subtracted from each of the input images.
  The exposures are obtained from the image headers under the specified
  name.  The output images may have the same names as the input images.
  A temporary image is used for the scaled dark count image and the original
  image is not modified.  The pixel datatype of the output images is
  specified by the parameter <I>pixtype</I>.  The default ("<TT>1</TT>") uses the
  datatype of the input image.  A log of the operations performed may be
  printed on the standard output when the verbose options is specified.
  <P>
  Note that this task can be used to subtract any type of image from a set
  of images in which the subtracted image must be scaled to a given exposure.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  To subtract the dark count image 'dark' from obs1, obs2, and obs3:
  <P>
  <PRE>
  	cl&gt; darksub obs1,obs2 obs1,obs2 dark exp="exposure"
  	Tue 18:50:56 08-Apr-86
  	  obs1 = obs1 - 5.0049997336067 * dark
  	Tue 18:51:05 08-Apr-86
  	  obs2 = obs2 - 5.009999733075 * dark
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  imarith
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE	' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
