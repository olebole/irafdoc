.. _crfix:

crfix — Fix cosmic rays in images using cosmic ray masks
========================================================

**Package: crutil**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  crfix -- fix cosmic rays in images using cosmic ray masks
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage	</H3>
  <! BeginSection: 'USAGE	'>
  <UL>
  <PRE>
  crfix input output masks
  </PRE>
  </UL>
  <! EndSection:   'USAGE	'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>Input two dimensional image to be "<TT>fixed</TT>" (modified) by linear interpolation.
  </DD>
  </DL>
  <DL>
  <DT><B>output</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>Output image.  If the output image name exactly matches the input
  image name (including extensions) then the image will be modified in place.
  </DD>
  </DL>
  <DL>
  <DT><B>crmask</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='crmask' Line='crmask'>
  <DD>Cosmic ray mask identifying the cosmic rays to be fixed.  The mask
  values are zero for good data and non-zero for cosmic rays.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The input and output images are specified by the <I>input</I> and
  <I>output</I> parameters.  If the input and output image names are
  identifical (including extensions) then image is modified in place.  Cosmic
  rays, identified in a cosmic ray mask specified by the <I>crmask</I>
  parameter, are replaced in the output image by linear interpolation along
  lines or columns using the nearest good pixels.  The special mask name
  "<TT>BPM</TT>" may be used to select a mask name given in the input image header
  under the keyword "<TT>BPM</TT>".
  <P>
  Cosmic ray pixels are "<TT>fixed</TT>" by replacing them with values
  by linear interpolation to the nearest pixels not identified as bad.
  The interpolation direction is the shortest length between good pixels
  along columns or lines.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1.  To replace cosmic rays in an image:
  <P>
  <PRE>
      cl&gt; crfix obj012 crobj012 crmask012
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  fixpix, crmedian, crnebula, cosmicrays, credit, epix
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE	' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
