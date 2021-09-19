.. _qstatistics:

qstatistics: Calculate image statistics for multi-amplifier CCD images
======================================================================

**Package: quadred**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  qstatistics -- Compute and print statistics for multi-amp data
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  qstatistics images
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>images</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='images' Line='images' -->
  <dd>List of image names in <b>quadformat</b>.
  </dd>
  </dl>
  <dl>
  <dt><b>window = <tt>"datasec"</tt> (datasec|trimsec|biassec)</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='window' Line='window = "datasec" (datasec|trimsec|biassec)' -->
  <dd>Type of section to output.  The choices are <tt>"datasec"</tt> for the amplifier
  section which includes the bias if any is present, <tt>"trimsec"</tt> for the trim
  section, and <tt>"biassec"</tt> for the bias section.
  </dd>
  </dl>
  <p>
  The remaining parameters come from the <b>imstatistics</b> task.
  </p>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  This script tasks uses the <b>quadsections</b> task to break the
  <b>quadformat</b> data into separate sections and runs the <b>imstatistics</b>
  task on the sections.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. To compute the mean and stddev of the data section.
  </p>
  <pre>
      qu&gt; qstat quad0072 fields=image,mean,stddev
      #               IMAGE      MEAN    STDDEV
       quad0072[1:1034,1:1024]     5537.     2647.
       quad0072[1163:2196,1:1024]     6210.     5439.
       quad0072[1:1034,1025:2048]     5364.     2535.
       quad0072[1163:2196,1025:2048]     5862.     1327.
  </pre>
  <p>
  2. To compute the mean and stdev of the bias section.
  </p>
  <pre>
      qu&gt; qstat quad0072 fields=image,mean,stddev window=biassec
      #               IMAGE      MEAN    STDDEV
       quad0072[1045:1098,1:1024]      713.     1.272
       quad0072[1099:1152,1:1024]     516.2     1.425
       quad0072[1045:1098,1025:2048]     554.3     1.347
       quad0072[1099:1152,1025:2048]     530.3     1.377
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  quadformat, quadsections, imstatistics
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  -->
  
