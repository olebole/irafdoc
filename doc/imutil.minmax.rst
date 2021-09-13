.. _minmax:

minmax — Compute the minimum and maximum pixel values in an image
=================================================================

**Package: imutil**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  minmax -- compute the minimum and maximum pixel values of an image
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  minmax images
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>images</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='images' Line='images'>
  <DD>Image template specifying the images to be examined.
  </DD>
  </DL>
  <DL>
  <DT><B>force = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='force' Line='force = no'>
  <DD>Force recomputation of the minimum and maximum pixel and pixel values even if
  they are noted as up to date in the image header.
  </DD>
  </DL>
  <DL>
  <DT><B>update = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='update' Line='update = yes'>
  <DD>Update the image header with the new values (requires write permission).
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes'>
  <DD>Print the image name, minimum value, and maximum value of each image
  processed.
  </DD>
  </DL>
  <DL>
  <DT><B>minval = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='minval' Line='minval = INDEF'>
  <DD>Set to the minimum pixel value of the last image processed.
  If the pixel type of the last input image was complex, this is the real
  part of the minimum value.
  </DD>
  </DL>
  <DL>
  <DT><B>maxval = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='maxval' Line='maxval = INDEF'>
  <DD>Set to the maximum pixel value of the last image processed.
  If the pixel type of the last input image was complex, this is the real
  part of the maximum value.
  </DD>
  </DL>
  <DL>
  <DT><B>iminval = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='iminval' Line='iminval = INDEF'>
  <DD>Set to the minimum imaginary part of the pixel value of the last image
  processed. Only used if the pixel type of the last input image was complex.
  </DD>
  </DL>
  <DL>
  <DT><B>imaxval = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='imaxval' Line='imaxval = INDEF'>
  <DD>Set to the maximum imaginary part of the pixel value of the last image
  processed. Only used if the pixel type of the last input image was complex.
  </DD>
  </DL>
  <DL>
  <DT><B>minpix = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='minpix' Line='minpix = ""'>
  <DD>Set to the minimum pixel specification of the last image processed.
  </DD>
  </DL>
  <DL>
  <DT><B>maxpix = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='maxpix' Line='maxpix = ""'>
  <DD>Set to the maximum pixel specification of the last image processed.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
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
  <H3>Examples</H3>
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
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  The minimum and maximum pixel values are stored in the image header as values
  of type real, hence some precision may be lost for images of type long integer
  or double precision floating.
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  imheader, hedit
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
