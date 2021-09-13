.. _hdfit:

hdfit — Fit a curve to density, log exposure values
===================================================

**Package: dtoi**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  hdfit -- fit characteristic curve to density, exposure data
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  hdfit database 
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>database</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='database' Line='database'>
  <DD>Database[s] containing the density, log exposure information.
  </DD>
  </DL>
  <DL>
  <DT><B>function = "<TT>power</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='function' Line='function = "power"'>
  <DD>Type of curve to fit; chosen from "<TT>power</TT>", "<TT>legendre</TT>", "<TT>chebyshev</TT>", 
  "<TT>spline1</TT>" or "<TT>spline3</TT>".  Abbreviations are permitted.
  </DD>
  </DL>
  <DL>
  <DT><B>transform = "<TT>logopacitance</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='transform' Line='transform = "logopacitance"'>
  <DD>Transformation performed on the density prior to fitting.  Chosen from
  "<TT>none</TT>", "<TT>logopacitance</TT>", "<TT>k50</TT>" or "<TT>k75</TT>". 
  </DD>
  </DL>
  <DL>
  <DT><B>weighting = "<TT>none</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='weighting' Line='weighting = "none"'>
  <DD>Weights can be assigned to the independent variable for fitting a curve.
  Choices are "<TT>none</TT>", "<TT>user</TT>" and "<TT>calculated</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>order = 4</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='order' Line='order = 4'>
  <DD>Order of the fit.
  </DD>
  </DL>
  <DL>
  <DT><B>interactive = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='interactive' Line='interactive = yes'>
  <DD>Fit the data interactively?
  </DD>
  </DL>
  <DL>
  <DT><B>device = "<TT>stdgraph</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='device' Line='device = "stdgraph"'>
  <DD>Interactive graphics device.
  </DD>
  </DL>
  <DL>
  <DT><B>cursor = "<TT>stdgcur</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='cursor' Line='cursor = "stdgcur"'>
  <DD>Source of cursor input.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Task <I>hdfit</I> is used to fit a curve to density and log exposure
  values in preparation for transforming an image from density to intensity.
  The log exposure and density are read from <B>database</B>.
  More than one database can be input,
  in which case one curve is fit to the combined data and the results
  written to each database in the list.
  <P>
  Weights can be applied to the independent variable of the fit.
  Weights can be changed interactively, and are originally chosen from
  "<TT>none</TT>", "<TT>user</TT>" and "<TT>calculated</TT>".  A weights value can
  be calculated from the standard deviations, read from <B>database</B>,
  as weight = (normalized density) / sdev.  If user weights are to be
  used, they are read from <B>database</B> record "<TT>weights</TT>" as "<TT>wts_vals</TT>"
  entries.  
  <P>
  When <B>interactive</B> = yes, the HD curve is plotted and the cursor
  made available for interactively examining and altering the fit.
  The fitting function, transformation and order can be modified; data
  points can be added, deleted or edited.  Four choices of independent
  variable are available in <B>hdfit</B> by means of the parameter 
  <B>transform</B>.  No transformation can take place, in which case
  the independent variable is the density.  Other choices are the log
  opacitance or a Kaiser transform with alpha = 0.50 or 0.75.  The
  default choice is to fit log exposure as a function of the log opacitance; 
  this is traditionally known as the Baker-Seidel function.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <PRE>
  Using the defaults as starting parameters, interactively fit a curve to
  the data points in db1.
  <P>
  	cl&gt; hdfit db1 
  <P>
  A sixth order power series function is fit in batch mode to the db1 data.
  <P>
  	cl&gt; hdfit db1 order=6 interactive-
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  spotlist, dematch, hdtoi
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
