.. _bitcount:

bitcount — Accumulate the bit statistics for a list of images
=============================================================

**Package: obsutil**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  bitcount - accumulate the bit statistics for a list of images
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  bitcount images
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>images</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='images' Line='images'>
  <DD>A list of image names whose bit statistics will be counted.  The
  statistics can either be reported for each individual image (the
  default) or as a grand total over all the images.
  </DD>
  </DL>
  <DL>
  <DT><B>grandtotal = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='grandtotal' Line='grandtotal = no'>
  <DD>If <I>grandtotal</I> = yes, accumulate a grand total over all the
  images.  If <I>grandtotal</I> = no (the default), report the statistics
  individually for each image in turn.
  </DD>
  </DL>
  <DL>
  <DT><B>leftzeroes = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='leftzeroes' Line='leftzeroes = yes'>
  <DD>If <I>leftzeroes</I> = yes, leftmost zeroes are counted into the
  statistics (the default).  If <I>leftzeroes</I> = no, leftmost zeroes
  (those past the most significant digit for each individual pixel)
  are omitted from the statistics.
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes'>
  <DD>If <I>verbose</I> = no, only the raw bit counts will be reported.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <I>Bitcount</I> will report the absolute and relative proportions
  of zeroes and ones populating each bit plane of a list of images.
  This is useful for diagnosing problems with a CCD's A/D converter,
  especially when an input image is supplied that contains a linear
  ramp in exposure across the range of the A/D.
  <P>
  The statistics for the list of images can be accumulated either
  individually for each image, or as a grand total over all of the
  images depending on the value of the <I>grandtotal</I> parameter.
  A single linear exposure ramp can be mimiced by a grand total
  over a list of progressively more exposed images.  Care should
  be taken to arrange that the exposures sample all parts of the
  A/D's range.
  <P>
  The <I>leftzeroes</I> parameter is used to correct a problem seen
  with the ctio.bitstat task.  Bitstat under-reports zeroes for the
  more significant bits since only pixels with values greater than
  the bit being currently counted participate in that count.  The
  severity and precise nature of this problem depends on the exposure
  level of a particular test image.  <I>Leftzeroes</I> may be set to
  "<TT>no</TT>" if there is some reason to restore this behavior.
  <P>
  The <I>verbose</I> parameter may be set to "<TT>no</TT>" in order to pass
  the raw bit counts on to some other task.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  To report the bit statistics for a test exposure ramp:
  <P>
  <PRE>
      nl&gt; bitcount testramp
  </PRE>
  <P>
  To accumulate a grand total over a list of images:
  <P>
  <PRE>
      nl&gt; bitcount a001*.imh grandtotal+
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  A warning will be issued when accumulating a grand total over a list
  of images whose datatypes vary.  In this case, the totals for each bit
  will be correct - to the extent that some images may not populate some
  bits - but the datatype of the final image in the list will control the
  range of bitplanes included in the output report.  The interpretation
  of the most significant bit as a sign bit will also depend on the
  datatype of this final image.
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  imstatistics, ctio.bitstat
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
