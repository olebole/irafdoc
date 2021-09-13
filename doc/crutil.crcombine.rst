.. _crcombine:

crcombine — Combine multiple exposures to eliminate cosmic rays
===============================================================

**Package: crutil**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  crcombine -- combine multiple exposures to eliminate cosmic rays
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage	</H3>
  <! BeginSection: 'USAGE	'>
  <UL>
  <PRE>
  crcombine input output
  </PRE>
  </UL>
  <! EndSection:   'USAGE	'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  See parameters for <B>imcombine</B>.
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  This task is a version of <B>imcombine</B>.  See the help for that task
  for a description of the parameters and algorithms.
  <P>
  For the purpose of removing cosmic rays the most useful options
  are the "<TT>crreject</TT>" algorithm and/or combining with a median.  Many other
  options may work as well.  The best use of this task depends on the
  number of images available.  If there are more than a few images the
  images should be combined with an "<TT>average</TT>" and using a rejection
  algorithm.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1.  To combine two images using the gain and read noise parameters in
  the image header:
  <P>
  <PRE>
      cl&gt; crcombine obj012,obj013 abc gain=gain rdnoise=rdnoise 
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  imcombine
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE	' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
