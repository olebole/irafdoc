.. _average:

average: Compute the mean and standard deviation of a list
==========================================================

**Package: lists**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  average -- compute the average and standard deviation
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  average option
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>option</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='option' Line='option' -->
  <dd>Chosen from <tt>"add"</tt>, <tt>"subtract"</tt> or <tt>"new_sample"</tt>, 
  in which case the numbers averaged are those in STDIN.
  If no argument is given on the command line, <tt>"new_sample"</tt> is assumed.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  Task <i>average</i> computes the average and standard deviation of a list
  of numbers.  Numeric input is read from STDIN with one number per line.
  The mean, sigma and number of samples are written to the standard
  output.
  </p>
  <p>
  By default, the sample is taken to be
  the set of numbers in the standard input when <i>average</i> is run. 
  Additional points can be added to or deleted from the sample by rerunning
  <i>average</i> with <b>option</b> equal to one of the following:
  </p>
  <pre>
  
  	add -- add points to the sample, recalculate mean and sigma
  	sub -- subtract points from the sample
  </pre>
  <p>
  The sample is reinitialized by setting <b>option</b> = <tt>"new_sample"</tt>.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  Run <i>average</i> on the list of numbers in file <tt>"numbers"</tt>.
  </p>
  <pre>
  	
  	cl&gt; type numbers | average
  </pre>
  <p>
  Add in to the sample the list of numbers in file <tt>"numbers.2"</tt>.
  </p>
  <pre>
  
  	cl&gt; average add &lt; numbers.2
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  lintran
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  -->
  
