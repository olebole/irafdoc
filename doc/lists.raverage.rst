.. _raverage:

raverage — Running average, standard deviation, and envelope
============================================================

**Package: lists**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  raverage -- running average, standard deviation, and envelope
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  raverage input nwin
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>Input one or two column list of numbers.  Any line that can't be read
  as one or two numbers is ignored which means comments are allowed.  The
  special name "<TT>STDIN</TT>" may be used to read the numbers from the standard
  input pipe or redirection.
  </DD>
  </DL>
  <DL>
  <DT><B>nwin</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nwin' Line='nwin'>
  <DD>The number of values in the running average window.
  </DD>
  </DL>
  <DL>
  <DT><B>sort = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='sort' Line='sort = no'>
  <DD>Numerically sort the first column of the input list by increasing value?
  This is done in an temporary file and the
  actual input file is not modified.
  </DD>
  </DL>
  <DL>
  <DT><B>nsig = 0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nsig' Line='nsig = 0'>
  <DD>The number of standard deviations below and above the average for the
  envelope columns.  If the value is greater than zero two extra columns
  are output formed by subtracting and adding this number of standard
  deviations to the average value.  If the value is zero then the
  columns not be written.
  </DD>
  </DL>
  <DL>
  <DT><B>fd1, fd2</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fd1' Line='fd1, fd2'>
  <DD>Internal parameters.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  This task computes the running average and standard deviation of a
  one or two column list.  For a one column list the ordinal value is
  added.  Note that the ordinal is only for the lines that are successfully
  read so any comments are not counted.  So the internal list is always
  two columns.
  <P>
  The input may be a physical file or the standard input.  The standard
  input is specified by the special name "<TT>STDIN</TT>".  All the input values
  are read and stored in a temporary file prior to computing the output.
  A temporary file is also used if the input is to be numerically sorted
  by increasing value of the first column.  Note that the sorting is done
  before adding the implied ordinal for one column lists.
  <P>
  The output has four or six columns depending on whether <I>nsig</I> is
  zero or greater than zero.
  <P>
  <PRE>
      average1 average1 stddev number [lower upper]
  <P>
      average1 - the running average of the first column
      average2 - the running average of the second column
        stddev - standard deviation of the second column
        number - number of values in the statistic
         lower - optional lower envelope value
         upper - optional upper envelope value
  </PRE>
  <P>
  The "<TT>number</TT>" of values may be less than the window if the window size is
  larger than the list.
  <P>
  The number of lines will generally be less than the input because there is
  no boundary extension.  In other words the first output value is computed
  after the first <I>nwin</I> values have been read and the last output value
  is computed when the end of the list is reached.
  <P>
  The envelope columns are computed when <I>nsig</I> is greater than zero.
  The values are
  <P>
  <PRE>
      lower = average2 - nsig * stddev
      upper = average2 + nsig * stddev
  </PRE>
  <P>
  In many cases the data is intended to represent a scatter plot and one
  wants to show the trend and envelope as a function of the first column.
  This is where the sorting and envelope options are useful.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1.  Compute the running average with a window of 100 values on the list of
  numbers in file "<TT>numbers</TT>".
  <PRE>
  	
  	cl&gt; raverage numbers 100
  </PRE>
  <P>
  2.  Do this using the standard input.  In this example use random numbers.
  <P>
  <PRE>
      cl&gt; urand 100 1 | raverage STDIN 90
  </PRE>
  <P>
  3.  Make a scatter plot of a two column list with the trend and envelope
  overplotted.
  <P>
  <PRE>
  	cl&gt; fields numbers 1,3 | graph point+
  	cl&gt; fields numbers 1,3 | raverage STDIN 100 sort+ nsig=3 &gt; tmp
  	cl&gt; fields tmp 1,2 | graph append+
  	cl&gt; fields tmp 1,5 | graph append+
  	cl&gt; fields tmp 1,6 | graph append+
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  average, boxcar
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
