.. _epix:

epix — Edit pixels in an image
==============================

**Package: proto**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  epix -- edit pixels in an image
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  epix image_name x y new_value
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>image_name</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='image_name' Line='image_name'>
  <DD>Name of image or image section to be edited.
  </DD>
  </DL>
  <DL>
  <DT><B>xcoord, ycoord</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xcoord' Line='xcoord, ycoord'>
  <DD>The coordinates of the pixel to be edited.
  </DD>
  </DL>
  <DL>
  <DT><B>new_value</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='new_value' Line='new_value'>
  <DD>The new value of the pixel.
  </DD>
  </DL>
  <DL>
  <DT><B>boxsize = 3</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='boxsize' Line='boxsize = 3'>
  <DD>The width of a square subraster surrounding the pixel to be edited over which
  the rejection mean and the median will be computed.
  </DD>
  </DL>
  <DL>
  <DT><B>ksigma = 0.0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ksigma' Line='ksigma = 0.0'>
  <DD>The pixel rejection threshold for the iterative rejection algorithm used
  to compute the mean.  If zero, a rejection threshold will be computed based
  on the size of the sample using Chauvenet's relation.
  </DD>
  </DL>
  <DL>
  <DT><B>edit_image = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='edit_image' Line='edit_image = yes'>
  <DD>Set the pixel value to <I>new_value</I>?  If editing is disabled the mean
  and median may still be computed, and the subraster may still be printed.
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes'>
  <DD>Print the values of the pixels in the subraster surrounding the image,
  and compute the rejection mean and the median.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  A subraster <I>boxsize</I> pixels square is extracted centered on the pixel
  (xcoord,ycoord).  If the <I>verbose</I> flag is enabled the values
  of the pixels in the subraster are printed on the standard output along with
  the rejection mean and median of the subraster.  If <I>edit_image</I> is yes
  the program will ask for the <I>new_value</I> and edit the image.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Replace the specified pixels with a value of zero.
  <P>
  <PRE>
      cl&gt; epix M92 400 87 0.0
      cl&gt; epix M92 45 300 0.0
      cl&gt; epix M92 207 300 0.0
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  imedit
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
