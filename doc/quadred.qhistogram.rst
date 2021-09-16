.. _qhistogram:

qhistogram — Make histogram of multi-amplifier CCD image
========================================================

**Package: quadred**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  qhistogram -- Compute and print histogram for multi-amp data
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  qhistogram images
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>images</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='images' Line='images'>
  <DD>List of image names in <B>quadformat</B>.
  </DD>
  </DL>
  <DL>
  <DT><B>window = "<TT>datasec</TT>" (datasec|trimsec|biassec)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='window' Line='window = "datasec" (datasec|trimsec|biassec)'>
  <DD>Type of section to use for histogram.  The choices are "<TT>datasec</TT>" for the
  amplifier section which includes the bias if any is present, "<TT>trimsec</TT>" for
  the trim section, and "<TT>biassec</TT>" for the bias section.
  </DD>
  </DL>
  <P>
  The remaining parameters come from the <B>imhistogram</B> task.
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  This script tasks uses the <B>quadsections</B> task to break the
  <B>quadformat</B> data into separate sections and runs the <B>imhistogram</B>
  task on the sections.  The graphics is collected onto a single page.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. To graph the histograms (default behavior).
  <P>
  <PRE>
      qu&gt; qhist quad0072
      [graph appears]
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  quadformat, quadsections, imhistogram
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
