.. _filtpars:

filtpars — Edit the filter function parameters
==============================================

**Package: rv**

.. raw:: html

  <H3>Name </H3>
  <! BeginSection: 'NAME '>
  <UL>
  filtpars -- edit the filter function parameters
  </UL>
  <! EndSection:   'NAME '>
  <H3>Usage </H3>
  <! BeginSection: 'USAGE '>
  <UL>
  filtpars
  </UL>
  <! EndSection:   'USAGE '>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>f_type = "<TT>ramp</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='f_type' Line='f_type = "ramp"'>
  <DD>Type of filter to be used.  Possible choices are
  <DL>
  <DT><B>ramp</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='ramp' Line='ramp'>
  <DD>A ramp function which begins to rise at the <I>cuton</I> wavenumber and
  reaches full value (i.e. passes the full value of the component) at the
  <I>fullon</I> wavenumber.  It begin to decline at the <I>cutoff</I> wavenumber
  and returns to zero at the <I>fulloff</I> wavenumber.
  </DD>
  </DL>
  <DL>
  <DT><B>Hanning</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='Hanning' Line='Hanning'>
  <DD>A Hanning function is used to attenuate the fourier components over the
  range specified by the <I>cuton</I> and <I>cutoff</I> parameters.
  </DD>
  </DL>
  <DL>
  <DT><B>Welch</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='Welch' Line='Welch'>
  <DD>A Welch function is used to attenuate the fourier components over the range
  specified by the <I>cuton</I> and <I>cutoff</I> parameters.
  </DD>
  </DL>
  <DL>
  <DT><B>Square</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='Square' Line='Square'>
  <DD>A standard step function which is zero outside the <I>cuton</I> and
  <I>cutoff</I> component numbers and one within those numbers.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B>cuton = 0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='cuton' Line='cuton = 0'>
  <DD>The fourier wavenumber at which the filter begins to pass the filtered fft
  component.
  </DD>
  </DL>
  <DL>
  <DT><B>cutoff = 0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='cutoff' Line='cutoff = 0'>
  <DD>The fourier wavenumber at which the filter ceases to pass fft components.
  </DD>
  </DL>
  <DL>
  <DT><B>fullon = 0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fullon' Line='fullon = 0'>
  <DD>Used only for a 'ramp' filter.  The fourier wavenumber at which the filter
  reaches full value and passes all of the data.
  </DD>
  </DL>
  <DL>
  <DT><B>fulloff = 0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fulloff' Line='fulloff = 0'>
  <DD>Used only for a 'ramp' filter.  The fourier wavenumber at which the filter
  reaches zero value and passes none of the data.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description </H3>
  <! BeginSection: 'DESCRIPTION '>
  <UL>
  The filtering parameters control the type of filter to be used
  on the Fourier transformed data as well as the range in wavenumbers over
  which it will operate.  Filtering of the data may be necessary to remove
  high frequency noise or low-frequency tends not removed by continuum
  subtraction.  If the filtering is enabled, then once the data have been 
  transformed, a bandpass filter of the type chosen by the
  <I>f_type</I> parameter is applied to the Fourier components of the
  spectra.  Wavenumbers lower than that specified by the <I>cuton</I> parameter
  are set to zero and wavenumbers up to that specified by the <I>cutoff</I>
  parameter (or the <I>fulloff</I> parameter in the case of a 'ramp' filter)
  are attenuated or passed in full according to the filter chosen.   
  Since the data are assumed to be linearized in log-wavelength space, applying 
  a filter to the data in Fourier space introduces no phase shift and has 
  the same effect as smoothing the data in real space.  The data are centered 
  and zero padded in an array of length 2**N such that the number of elements 
  is greater than or equal to the number of actual data points.  This array in
  then Fourier transformed, and the resulting fft is then filtered prior
  to correlation.
  <P>
  Filtering is enabled by turning on the <I>fxcor.filter</I> parameter and setting
  it to something other than "<TT>none</TT>".  Filtering may be done on only one of the
  two spectra or both prior to correlation.
  <P>
  The filter choices behave as follows:
  <DL>
  <DT><B>Square Filter</B></DT>
  <! Sec='DESCRIPTION ' Level=0 Label='Square' Line='Square Filter'>
  <DD>The fourier components at wavenumbers between the <I>cuton</I> and <I>cutoff</I>
  wavenumbers are passed without change.  Those wavenumbers outside this region
  are set to zero.
  </DD>
  </DL>
  <DL>
  <DT><B>Ramp Filter</B></DT>
  <! Sec='DESCRIPTION ' Level=0 Label='Ramp' Line='Ramp Filter'>
  <DD>Fourier components below the <I>cuton</I> and above the <I>fulloff</I> 
  wavenumbers are set to zero. 
  At the <I>cuton</I> wavenumber the filter function
  begins to rise until the <I>fullon</I> wavenumber is reached.  Data in this 
  region is weighted by the slope of the filter until at the <I>fullon</I>
  wavenumber data are passed through without change.  Similarly, the filter
  begins to fall at the <I>cutoff</I> wavenumber until it completely blocks
  (i.e. zeros) the fourier components at the <I>fulloff</I> wavenumber.
  </DD>
  </DL>
  <DL>
  <DT><B>Welch Filter</B></DT>
  <! Sec='DESCRIPTION ' Level=0 Label='Welch' Line='Welch Filter'>
  <DD>Fourier components below the <I>cuton</I> and above the <I>cutoff</I> 
  wavenumbers are set to zero.  Components between these regions are weighted
  according to the equation for a Welch window.  Namely,
  <PRE>
  <P>
  						     2      
  	w(j)  = 1. - [ (j - 1/2(N-1)) / (1/2(N+1)) ] 
  		        
  		where j =  (wavenumber - cuton_wavenumber) 
  	      	      N =  (cutoff - cuton) + 1
  </PRE>
  </DD>
  </DL>
  <DL>
  <DT><B>Hanning Filter</B></DT>
  <! Sec='DESCRIPTION ' Level=0 Label='Hanning' Line='Hanning Filter'>
  <DD>Fourier components below the <I>cuton</I> and above the <I>cutoff</I> 
  wavenumbers are set to zero. Components between these regions are weighted
  according to the equation for a Hanning window.  Namely,
  <PRE>
  <P>
  	w(j)  =  1/2 [ 1. - cos( (TWOPI*j) / (N-1) ) ]
  <P>
  		where j =  (wavenumber - cuton_wavenumber) 
  	              N =  (cutoff - cuton) + 1
  </PRE>
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION '>
  <H3>Task colon commands</H3>
  <! BeginSection: 'TASK COLON COMMANDS'>
  <UL>
  The values of the <I>filtpars</I> pset may be changed, displayed, or updated
  from within the Fourier mode of the <I>fxcor</I> task.  Simply 
  typing the parameter name will have the default action of printing the current
  value of that parameter. An optional value may be added to change the named
  parameter.
  <DL>
  <DT><B>:update  filtpars</B></DT>
  <! Sec='TASK COLON COMMANDS' Level=0 Label='' Line=':update  filtpars'>
  <DD>Update the pset with the current values of the filter parameters.
  The argument "<TT>filtpars</TT>" must be present or else the command will default
  to the task parameters.
  </DD>
  </DL>
  <DL>
  <DT><B>:unlearn  filtpars</B></DT>
  <! Sec='TASK COLON COMMANDS' Level=0 Label='' Line=':unlearn  filtpars'>
  <DD>Reset the parameter values to their defaults.
  The argument "<TT>filtpars</TT>" must be present or else the command will default
  to the task parameters.
  </DD>
  </DL>
  <DL>
  <DT><B>:show  filtpars</B></DT>
  <! Sec='TASK COLON COMMANDS' Level=0 Label='' Line=':show  filtpars'>
  <DD>Clear the screen and display all values in the filtpars pset.
  The argument "<TT>filtpars</TT>" must be present or else the command will default
  to the task default.
  </DD>
  </DL>
  <DL>
  <DT><B>:filttype	[ramp|welch|hanning|square|none]</B></DT>
  <! Sec='TASK COLON COMMANDS' Level=0 Label='' Line=':filttype	[ramp|welch|hanning|square|none]'>
  <DD>Set or show the current value of the filter type to use
  </DD>
  </DL>
  <DL>
  <DT><B>:cuton	[int_value]</B></DT>
  <! Sec='TASK COLON COMMANDS' Level=0 Label='' Line=':cuton	[int_value]'>
  <DD>Set or show the current value of the cuton fourier component
  </DD>
  </DL>
  <DL>
  <DT><B>:cutoff	[int_value]</B></DT>
  <! Sec='TASK COLON COMMANDS' Level=0 Label='' Line=':cutoff	[int_value]'>
  <DD>Set or show the current value of the cutoff fourier component
  </DD>
  </DL>
  <DL>
  <DT><B>:fullon	[int_value]</B></DT>
  <! Sec='TASK COLON COMMANDS' Level=0 Label='' Line=':fullon	[int_value]'>
  <DD>Set or show the current value of the fullon fourier component
  </DD>
  </DL>
  <DL>
  <DT><B>:fulloff	[int_value]</B></DT>
  <! Sec='TASK COLON COMMANDS' Level=0 Label='' Line=':fulloff	[int_value]'>
  <DD>Set or show the current value of the fulloff fourier component
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'TASK COLON COMMANDS'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. List the filtering parameters.
  <P>
  <PRE>
  	rv&gt; lpar filtpars
  </PRE>
  <P>
  2. Edit the filtering parameters
  <P>
  <PRE>
  	rv&gt; filtpars
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  fxcor
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME ' 'USAGE ' 'PARAMETERS' 'DESCRIPTION ' 'TASK COLON COMMANDS' 'EXAMPLES' 'SEE ALSO'  >
  
