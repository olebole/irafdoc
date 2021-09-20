.. _velvect:

velvect: Plot representation of a velocity field
================================================

**Package: plot**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  velvect -- two dimensional velocity field plot
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  velvect uimage vimage
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>uimage</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='uimage' Line='uimage' -->
  <dd>Name of image containing u components of the velocity field.
  </dd>
  </dl>
  <dl>
  <dt><b>vimage </b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='vimage' Line='vimage ' -->
  <dd>Name of image containing v components of the velocity field.
  </dd>
  </dl>
  <dl>
  <dt><b>device = stdgraph</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='device' Line='device = stdgraph' -->
  <dd>Output device for plot.
  </dd>
  </dl>
  <dl>
  <dt><b>title = <span style="font-family: monospace;">"imtitle"</span></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='title' Line='title = "imtitle"' -->
  <dd>Title to be centered over the plot.  By default, it will be the title
  from the image header of the <b>uimage</b>.
  </dd>
  </dl>
  <dl>
  <dt><b>append = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='append' Line='append = no' -->
  <dd>Append to an old plot?
  </dd>
  </dl>
  <dl>
  <dt><b>verbose = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes' -->
  <dd>Print warning messages?
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  Task <i>velvect</i> draws a representation of a two-dimensional velocity
  field by drawing arrows from each data location.  The length of the arrow
  is proportional to the strength of the field at that location and the direction
  of the arrow indicates the direction of the flow at that location.  The
  two images <i>uimage</i> and <i>vimage</i> contain the velocity field to be
  plotted.  The vector at the point (i,j) has:
  </p>
  <pre>
      magnitude = sqrt (uimage(i,j)**2 + vimage(i,j)**2)
      direction = atan2 (vimage(i,j), uimage(i,j))
  </pre>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Make a vector plot from the two images <span style="font-family: monospace;">"crab.blue"</span> and <span style="font-family: monospace;">"crab.red"</span>.
  </p>
  <p>
      cl&gt; velvect crab.blue crab.red
  </p>
  
  <!-- EndSection:    'EXAMPLES' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES'  -->
  
