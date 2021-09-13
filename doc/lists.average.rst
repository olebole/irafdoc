.. _average:

average — Compute the mean and standard deviation of a list
===========================================================

**Package: lists**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  average -- compute the average and standard deviation
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  average option
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>option</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='option' Line='option'>
  <DD>Chosen from "<TT>add</TT>", "<TT>subtract</TT>" or "<TT>new_sample</TT>", 
  in which case the numbers averaged are those in STDIN.
  If no argument is given on the command line, "<TT>new_sample</TT>" is assumed.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Task <I>average</I> computes the average and standard deviation of a list
  of numbers.  Numeric input is read from STDIN with one number per line.
  The mean, sigma and number of samples are written to the standard
  output.
  <P>
  By default, the sample is taken to be
  the set of numbers in the standard input when <I>average</I> is run. 
  Additional points can be added to or deleted from the sample by rerunning
  <I>average</I> with <B>option</B> equal to one of the following:
  <PRE>
  <P>
  	add -- add points to the sample, recalculate mean and sigma
  	sub -- subtract points from the sample
  </PRE>
  <P>
  The sample is reinitialized by setting <B>option</B> = "<TT>new_sample</TT>".
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  Run <I>average</I> on the list of numbers in file "<TT>numbers</TT>".
  <PRE>
  	
  	cl&gt; type numbers | average
  </PRE>
  <P>
  Add in to the sample the list of numbers in file "<TT>numbers.2</TT>".
  <PRE>
  <P>
  	cl&gt; average add &lt; numbers.2
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  lintran
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
