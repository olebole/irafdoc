.. _average:

average: Compute the mean and standard deviation of a list
==========================================================

**Package: lists**

.. raw:: html

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
  <dd>Chosen from <span style="font-family: monospace;">"add"</span>, <span style="font-family: monospace;">"subtract"</span> or <span style="font-family: monospace;">"new_sample"</span>, 
  in which case the numbers averaged are those in STDIN.
  If no argument is given on the command line, <span style="font-family: monospace;">"new_sample"</span> is assumed.
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
  The sample is reinitialized by setting <b>option</b> = <span style="font-family: monospace;">"new_sample"</span>.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  Run <i>average</i> on the list of numbers in file <span style="font-family: monospace;">"numbers"</span>.
  </p>
  <pre>
  	
  	cl&gt; type numbers | average
  </pre>
  <p>
  Add in to the sample the list of numbers in file <span style="font-family: monospace;">"numbers.2"</span>.
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
  
