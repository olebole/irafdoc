.. _continpars:

continpars — Edit continuum subtraction parameters
==================================================

**Package: rv**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  continpars -- edit the continuum subtraction parameters
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  continpars
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>c_sample = "<TT>*</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='c_sample' Line='c_sample = "*"'>
  <DD>Lines or columns to be used in the fits.  The default value ("<TT>*</TT>") selects
  all pixels.  Type <I>help ranges</I> for a complete description of the
  syntax.
  </DD>
  </DL>
  <DL>
  <DT><B>c_function = "<TT>spline3</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='c_function' Line='c_function = "spline3"'>
  <DD>Continuum function to be fit to the image lines or columns.  The functions are
  "<TT>legendre</TT>" (Legendre polynomial), "<TT>chebyshev</TT>" (Chebyshev polynomial),
  "<TT>spline1</TT>" (linear spline), and "<TT>spline3</TT>" (cubic spline).  The functions
  may be abbreviated.
  </DD>
  </DL>
  <DL>
  <DT><B>c_interactive = "<TT>no</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='c_interactive' Line='c_interactive = "no"'>
  <DD>Interactively fit the continuum? If set to yes, each spectrum will be fit
  interactively as they are read into the task if the <I>fxcor.continuum</I>
  parameter requires it.  The <I>fxcor</I> keystroke commands <TT>'o'</TT> and <TT>'t'</TT> will
  automatically fit the continuum interactively.
  </DD>
  </DL>
  <DL>
  <DT><B>naverage = 1</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='naverage' Line='naverage = 1'>
  <DD>Number of sample points to combined to create a fitting point.
  A positive value specifies an average and a negative value specifies
  a median.
  </DD>
  </DL>
  <DL>
  <DT><B>order = 1</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='order' Line='order = 1'>
  <DD>The order of the polynomials or the number of spline pieces.
  </DD>
  </DL>
  <DL>
  <DT><B>replace = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='replace' Line='replace = no'>
  <DD>Replace rejected data points with continuum fit points prior to the
  subtraction?  If set to yes, points lying outside the <I>low_reject</I> or
  <I>high_reject</I> limits are replaced by the fit values prior to the 
  continuum subtraction.  This can be useful in removing emission features 
  or cosmic ray events, but great care must be taken in setting other parameters
  in order to get satisfactory results.  Adjusting the <I>grow</I> or 
  <I>average</I> parameters, and using a low order function usually provide
  a good result. 
  </DD>
  </DL>
  <DL>
  <DT><B>low_reject = 2.,  high_reject = 2.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='low_reject' Line='low_reject = 2.,  high_reject = 2.'>
  <DD>Rejection limits below and above the fit in units of the residual sigma.
  </DD>
  </DL>
  <DL>
  <DT><B>niterate = 1</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='niterate' Line='niterate = 1'>
  <DD>Number of rejection iterations.
  </DD>
  </DL>
  <DL>
  <DT><B>grow = 1.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='grow' Line='grow = 1.'>
  <DD>When a pixel is rejected, pixels within this distance of the rejected pixel
  are also rejected.
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The <I>continpars</I> pset is used to control the continuum subtraction from 
  the data.  When the <I>fxcor</I> task is run in a batch mode, 
  the parameters are used to
  automatically process the data without intervention from the user.  In an
  interactive session, the user may experiment with different parameter values by
  changing them with the allowed colon commands.
  <P>
  Continuum subtraction is done exactly as with the <I>onedspec.continuum</I>
  task.  (Details of the operation are described in the <I>continuum</I> 
  documentation.)  The fit to the spectra is subtracted from the data, thus 
  producing a continuum subtracted spectrum suitable for input to the correlation
  routines.  
  <P>
  Users who require the full ability of the <I>onedspec.continuum</I> task to
  supply another form of output spectrum, such as the ratio of the fit, or
  who wish to make use of the "<TT>clean</TT>" option, should use that task and disable
  continuum subtraction in the <I>rv</I> package tasks.  More functionality is
  planned for this pset in the future.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Task colon commands</H3>
  <! BeginSection: 'TASK COLON COMMANDS'>
  <UL>
  The values of the <I>continpars</I> pset may be changed, displayed, or updated
  from within tasks that use them by means of various colon commands.  Simply 
  typing the parameter name will have the default action of printing the current
  value of that parameter. 
  <DL>
  <DT><B>:unlearn	continpars</B></DT>
  <! Sec='TASK COLON COMMANDS' Level=0 Label='' Line=':unlearn	continpars'>
  <DD>Reset the continpars pset parameters with their default values.
  The argument "<TT>continpars</TT>" must be present or else the command will default
  to the <I>fxcor</I> task command.
  </DD>
  </DL>
  <DL>
  <DT><B>:update	continpars</B></DT>
  <! Sec='TASK COLON COMMANDS' Level=0 Label='' Line=':update	continpars'>
  <DD>Update the continpars pset parameters with the current values.
  The argument "<TT>continpars</TT>" must be present or else the command will default
  to the <I>fxcor</I> task command.
  </DD>
  </DL>
  <DL>
  <DT><B>:show	continpars</B></DT>
  <! Sec='TASK COLON COMMANDS' Level=0 Label='' Line=':show	continpars'>
  <DD>Show the current values of the continpars pset parameters.
  The argument "<TT>continpars</TT>" must be present or else the command will default
  to the <I>fxcor</I> task command.
  </DD>
  </DL>
  <P>
  The following parameters will be displayed if it's name it typed, and a new 
  value accepted if an argument is given.
  <P>
  <PRE>
  :c_sample	[range_string]
  :naverage	[int_value]
  :c_function	[spline3|legendre|chebyshev|spline1]
  :order		[int_value]
  :low_reject	[int_value]
  :high_reject	[int_value]
  :niterate	[int_value]
  :grow		[int_value]
  </PRE>
  <P>
  </UL>
  <! EndSection:   'TASK COLON COMMANDS'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. List the continuum parameters.
  <P>
  <PRE>
  	rv&gt; lpar continpars
  </PRE>
  <P>
  2. Edit the continuum parameters
  <P>
  <PRE>
  	rv&gt; continpars
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  fxcor, onedspec.continuum, icfit, sfit
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'TASK COLON COMMANDS' 'EXAMPLES' 'SEE ALSO'  >
  
