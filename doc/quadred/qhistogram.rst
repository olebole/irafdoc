.. _qhistogram:

qhistogram: Make histogram of multi-amplifier CCD image
=======================================================

**Package: quadred**

.. raw:: html

  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  qhistogram images
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
  <dt><b>window = <span style="font-family: monospace;">"datasec"</span> (datasec|trimsec|biassec)</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='window' Line='window = "datasec" (datasec|trimsec|biassec)' -->
  <dd>Type of section to use for histogram.  The choices are <span style="font-family: monospace;">"datasec"</span> for the
  amplifier section which includes the bias if any is present, <span style="font-family: monospace;">"trimsec"</span> for
  the trim section, and <span style="font-family: monospace;">"biassec"</span> for the bias section.
  </dd>
  </dl>
  <p>
  The remaining parameters come from the <b>imhistogram</b> task.
  </p>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  This script tasks uses the <b>quadsections</b> task to break the
  <b>quadformat</b> data into separate sections and runs the <b>imhistogram</b>
  task on the sections.  The graphics is collected onto a single page.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. To graph the histograms (default behavior).
  </p>
  <pre>
      qu&gt; qhist quad0072
      [graph appears]
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  quadformat, quadsections, imhistogram
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  -->
  
