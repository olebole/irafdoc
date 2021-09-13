hdfit — Fit a curve to density, log exposure values
===================================================

**Package: dtoi**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>hdfit (Mar88)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>imred.dtoi</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>hdfit (Mar88)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>hdfit</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  hdfit -- fit characteristic curve to density, exposure data
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  hdfit database 
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_database">database</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='database' Line='database'>
  <DD>Database[s] containing the density, log exposure information.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_function">function = "<TT>power</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='function' Line='function = "power"'>
  <DD>Type of curve to fit; chosen from "<TT>power</TT>", "<TT>legendre</TT>", "<TT>chebyshev</TT>", 
  "<TT>spline1</TT>" or "<TT>spline3</TT>".  Abbreviations are permitted.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_transform">transform = "<TT>logopacitance</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='transform' Line='transform = "logopacitance"'>
  <DD>Transformation performed on the density prior to fitting.  Chosen from
  "<TT>none</TT>", "<TT>logopacitance</TT>", "<TT>k50</TT>" or "<TT>k75</TT>". 
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_weighting">weighting = "<TT>none</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='weighting' Line='weighting = "none"'>
  <DD>Weights can be assigned to the independent variable for fitting a curve.
  Choices are "<TT>none</TT>", "<TT>user</TT>" and "<TT>calculated</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_order">order = 4</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='order' Line='order = 4'>
  <DD>Order of the fit.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_interactive">interactive = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='interactive' Line='interactive = yes'>
  <DD>Fit the data interactively?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_device">device = "<TT>stdgraph</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='device' Line='device = "stdgraph"'>
  <DD>Interactive graphics device.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_cursor">cursor = "<TT>stdgcur</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='cursor' Line='cursor = "stdgcur"'>
  <DD>Source of cursor input.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
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
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
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
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  spotlist, dematch, hdtoi
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>