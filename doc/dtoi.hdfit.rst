.. _hdfit:

hdfit: Fit a curve to density, log exposure values
==================================================

**Package: dtoi**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  hdfit -- fit characteristic curve to density, exposure data
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  hdfit database 
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>database</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='database' Line='database' -->
  <dd>Database[s] containing the density, log exposure information.
  </dd>
  </dl>
  <dl>
  <dt><b>function = <tt>"power"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='function' Line='function = "power"' -->
  <dd>Type of curve to fit; chosen from <tt>"power"</tt>, <tt>"legendre"</tt>, <tt>"chebyshev"</tt>, 
  <tt>"spline1"</tt> or <tt>"spline3"</tt>.  Abbreviations are permitted.
  </dd>
  </dl>
  <dl>
  <dt><b>transform = <tt>"logopacitance"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='transform' Line='transform = "logopacitance"' -->
  <dd>Transformation performed on the density prior to fitting.  Chosen from
  <tt>"none"</tt>, <tt>"logopacitance"</tt>, <tt>"k50"</tt> or <tt>"k75"</tt>. 
  </dd>
  </dl>
  <dl>
  <dt><b>weighting = <tt>"none"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='weighting' Line='weighting = "none"' -->
  <dd>Weights can be assigned to the independent variable for fitting a curve.
  Choices are <tt>"none"</tt>, <tt>"user"</tt> and <tt>"calculated"</tt>.
  </dd>
  </dl>
  <dl>
  <dt><b>order = 4</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='order' Line='order = 4' -->
  <dd>Order of the fit.
  </dd>
  </dl>
  <dl>
  <dt><b>interactive = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='interactive' Line='interactive = yes' -->
  <dd>Fit the data interactively?
  </dd>
  </dl>
  <dl>
  <dt><b>device = <tt>"stdgraph"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='device' Line='device = "stdgraph"' -->
  <dd>Interactive graphics device.
  </dd>
  </dl>
  <dl>
  <dt><b>cursor = <tt>"stdgcur"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='cursor' Line='cursor = "stdgcur"' -->
  <dd>Source of cursor input.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  Task <i>hdfit</i> is used to fit a curve to density and log exposure
  values in preparation for transforming an image from density to intensity.
  The log exposure and density are read from <b>database</b>.
  More than one database can be input,
  in which case one curve is fit to the combined data and the results
  written to each database in the list.
  </p>
  <p>
  Weights can be applied to the independent variable of the fit.
  Weights can be changed interactively, and are originally chosen from
  <tt>"none"</tt>, <tt>"user"</tt> and <tt>"calculated"</tt>.  A weights value can
  be calculated from the standard deviations, read from <b>database</b>,
  as weight = (normalized density) / sdev.  If user weights are to be
  used, they are read from <b>database</b> record <tt>"weights"</tt> as <tt>"wts_vals"</tt>
  entries.  
  </p>
  <p>
  When <b>interactive</b> = yes, the HD curve is plotted and the cursor
  made available for interactively examining and altering the fit.
  The fitting function, transformation and order can be modified; data
  points can be added, deleted or edited.  Four choices of independent
  variable are available in <b>hdfit</b> by means of the parameter 
  <b>transform</b>.  No transformation can take place, in which case
  the independent variable is the density.  Other choices are the log
  opacitance or a Kaiser transform with alpha = 0.50 or 0.75.  The
  default choice is to fit log exposure as a function of the log opacitance; 
  this is traditionally known as the Baker-Seidel function.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <pre>
  Using the defaults as starting parameters, interactively fit a curve to
  the data points in db1.
  
  	cl&gt; hdfit db1 
  
  A sixth order power series function is fit in batch mode to the db1 data.
  
  	cl&gt; hdfit db1 order=6 interactive-
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  spotlist, dematch, hdtoi
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  -->
  
