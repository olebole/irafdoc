psfmatch — Match the point-spread functions of 1-D or 2-D images
================================================================

**Package: immatch**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>psfmatch (Oct94)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>images.immatch</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>psfmatch (Oct94)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>psfmatch</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  psfmatch -- match the point spread functions of 1 and 2D images
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  psfmatch input reference psfdata kernel 
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>The list of input images to be matched.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_reference">reference</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='reference' Line='reference'>
  <DD>The list of reference images to which the input images are to be matched if
  <I>convolution</I> = "<TT>image</TT>", or the list of reference image psfs if 
  <I>convolution</I> = "<TT>psf</TT>". The reference image psf must be broader than the
  input image psf in at least one dimension.
  The number of reference images/psfs must be one or equal to the number of
  input images.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_psfdata">psfdata</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='psfdata' Line='psfdata'>
  <DD>The list of objects used to compute the psf matching function if
  <I>convolution</I> is "<TT>image</TT>", or the list of input image psfs if 
  <I>convolution</I> is "<TT>psf</TT>". In the former case <I>psfdata</I> may be:
  1) a string containing the x and y coordinates of a single object,
  e.g. "<TT>51.0 105.0</TT>" or 2) the name of a text file containing a list of
  objects, and the number of objects
  files must equal the number of reference images. In the latter case
  the number of input psf images must equal the number of input images.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_kernel">kernel</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='kernel' Line='kernel'>
  <DD>The list of input/output psf matching function images to be convolved with the
  input images to produce the output images. The number of kernel images
  must equal the number of input images.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_output">output = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output = ""'>
  <DD>The list of output matched images. If <I>output</I> is the NULL string
  then the psf matching function is computed for each input image and written to
  <I>kernel</I> but no output images are written. If <I>output</I> is not NULL
  then the number of output images must equal the number of input images.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_convolution">convolution = "<TT>image</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='convolution' Line='convolution = "image"'>
  <DD>The algorithm used to compute the psf matching function. The options are:
  <DL>
  <DT><B><A NAME="l_image">image</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='image' Line='image'>
  <DD>The psf matching function is computed directly from the reference and input
  image data using the objects specified in <I>psfdata</I>, the data
  regions specified by <I>dnx</I>, <I>dny</I>, <I>pnx</I>, and <I>pny</I>,
  and the convolution theorem.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_psf">psf   </A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='psf' Line='psf   '>
  <DD>The psf matching function is computed directly from pre-computed
  reference and input image psfs using the convolution theorem.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_kernel">kernel</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='kernel' Line='kernel'>
  <DD>No psf matching function is computed. Instead the psf matching function
  is  read from the input image <I>kernel</I>.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_dnx">dnx = 31, ls dny = 31</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='dnx' Line='dnx = 31, ls dny = 31'>
  <DD>The x and y width of the data region to be extracted around each object. The
  data region should be big enough to include both object and sky data.
  <I>Dnx</I> and <I>dny</I> are not used if <I>convolution</I> is "<TT>psf</TT>" or
  "<TT>kernel</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_pnx">pnx = 15, pny = 15</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='pnx' Line='pnx = 15, pny = 15'>
  <DD>The x and y width of the psf matching function to be computed which must be
  less than <I>dnx</I> and <I>dny</I> respectively. The psf
  matching function should be kept as small as possible to minimize
  the time required to compute the output image.
  <I>Pnx</I> and <I>Pny</I> are not used if <I>convolution</I> is "<TT>psf</TT>" or
  "<TT>kernel</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_center">center = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='center' Line='center = yes'>
  <DD>Center the objects in <I>psfdata</I> before extracting the data from the
  input and reference images. Centering should be turned off if the objects
  are non-stellar and do not have well-defined centers.
  Centering is turned off if <I>convolution</I> is "<TT>psf</TT>" or
  "<TT>kernel</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_background">background = median</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='background' Line='background = median'>
  <DD>The default background function to be subtracted from the input
  and reference image data in each object region before the
  psf matching function is computed. The background is computed using
  data inside the data extraction region defined by <I>dnx</I> and <I>dny</I>
  but outside the kernel region defined by <I>pnx</I> and <I>pny</I>.
  Background fitting is turned off if <I>convolution</I> is "<TT>psf</TT>" or
  "<TT>kernel</TT>".
  The options are:
  <DL>
  <DT><B><A NAME="l_none">none</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='none' Line='none'>
  <DD>no background subtraction is done.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">"<TT>insky refsky</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='' Line='"insky refsky"'>
  <DD>the numerical values of insky and refsky are subtracted from the
  input and reference image respectively.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_mean">mean</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='mean' Line='mean'>
  <DD>the mean of the input and reference image region is computed and subtracted
  from the image data.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_median">median</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='median' Line='median'>
  <DD>the median of the input and reference image region is computed and subtracted
  from the data.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_plane">plane</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='plane' Line='plane'>
  <DD>a plane is fit to the input and reference image region and subtracted
  from the data.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_loreject">loreject = INDEF, ls hireject = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='loreject' Line='loreject = INDEF, ls hireject = INDEF'>
  <DD>The k-sigma rejection limits for removing the effects of bad data from the
  background fit.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_apodize">apodize = 0.0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='apodize' Line='apodize = 0.0'>
  <DD>The fraction of the input and reference image data endpoints in x and y
  to apodize with a
  cosine bell function before the psf matching function is computed.
  Apodizing is turned off if <I>convolution</I> is "<TT>psf</TT>" or
  "<TT>kernel</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_fluxratio">fluxratio = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fluxratio' Line='fluxratio = INDEF'>
  <DD>The ratio of the integrated flux of the reference objects to the integrated
  flux of the input objects.
  By default <I>fluxratio</I> is computed directly from the input data.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_filter">filter = "<TT>replace</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='filter' Line='filter = "replace"'>
  <DD>The filter used to remove high frequency noise from the psf
  matching function. Filtering is not performed if <I>convolution</I>
  is "<TT>kernel</TT>". The options are:
  <DL>
  <DT><B><A NAME="l_cosbell">cosbell</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='cosbell' Line='cosbell'>
  <DD>apply a cosine bell taper to the psf matching function in frequency space. 
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_replace">replace</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='replace' Line='replace'>
  <DD>replace the high-frequency low signal-to-noise components of the psf matching
  function with a gaussian model computed from the low frequency
  high signal-to-noise components of the matching function.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_model">model</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='model' Line='model'>
  <DD>replace the entire psf matching function with a gaussian model fit to the
  low frequency high signal-to-noise components of the matching function.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_sx1">sx1 = INDEF, sx2 = INDEF, sy1 = INDEF, sy2 = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='sx1' Line='sx1 = INDEF, sx2 = INDEF, sy1 = INDEF, sy2 = INDEF'>
  <DD>The limits of the cosine bell taper in frequency space. Frequency components
  inside sx1 and sy1 are unaltered. Frequency components outside sx2 and sy2
  are set to 0.0. By default sx1 and sy1 are set to 0.0,
  and sx2 and sy2 are set to the largest frequency present in the data.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_radsym">radsym = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='radsym' Line='radsym = no'>
  <DD>Compute a radially symmetric cosine bell function ?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_threshold">threshold = 0.2</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='threshold' Line='threshold = 0.2'>
  <DD>The low frequency cutoff in fraction of the total input image spectrum
  power for the filtering options "<TT>replace</TT>" and "<TT>model</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_normfactor">normfactor = 1.0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='normfactor' Line='normfactor = 1.0'>
  <DD>The total power in the computed psf matching function <I>kernel</I>. By default
  the psf matching function is normalized.  If <I>normfactor</I>
  is set to INDEF, then the total power is set to <I>fluxratio</I>.
  <I>Normfactor</I> is not used if <I>convolution</I> is set "<TT>kernel</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_boundary_type">boundary_type = "<TT>nearest</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='boundary_type' Line='boundary_type = "nearest"'>
  <DD>The boundary extension algorithm used to compute the output matched
  image.  The options are:
  <DL>
  <DT><B><A NAME="l_nearest">nearest</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='nearest' Line='nearest'>
  <DD>use the value of the nearest boundary pixel.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_constant">constant</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='constant' Line='constant'>
  <DD>use a constant value.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_reflect">reflect</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='reflect' Line='reflect'>
  <DD>generate a value by reflecting about the boundary.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_wrap">wrap</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='wrap' Line='wrap'>
  <DD>generate a value by wrapping around to the opposite side of the image.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_constant">constant = 0.0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='constant' Line='constant = 0.0'>
  <DD>The default constant for constant boundary extension.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_interactive">interactive = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='interactive' Line='interactive = no'>
  <DD>Compute the psf matching function for each image
  interactively using graphics cursor and, optionally, image cursor input.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_verbose">verbose</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose'>
  <DD>Print messages about the progress of the task in non-interactive mode.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_graphics">graphics = "<TT>stdgraph</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='graphics' Line='graphics = "stdgraph"'>
  <DD>The default graphics device.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_display">display = "<TT>stdimage</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='display' Line='display = "stdimage"'>
  <DD>The default image display device.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_gcommands">gcommands = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='gcommands' Line='gcommands = ""'>
  <DD>The default graphics cursor.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_icommands">icommands = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='icommands' Line='icommands = ""'>
  <DD>The default image display cursor.
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  PSFMATCH computes the convolution kernel required to match the
  point-spread functions
  of the input images <I>input</I> to the point-spread functions of
  the reference images <I>reference</I> using either the image data 
  or pre-computed psfs and the convolution theorem.
  The computed psf matching functions are stored in the <I>kernel</I> images.
  If a non-NULL list of output images <I>output</I> is
  specified the input images are
  convolved with the kernel images to produce a list of psf matched output
  images. PSFMATCH requires
  that the input and reference images be spatially registered
  and that the reference images have poorer resolution (broader PSF)
  than the input images in at least one dimension.
  <P>
  If <I>convolution</I> = "<TT>image</TT>", the matching function is computed directly
  from the input and reference image data using the objects listed in
  <I>psfdata</I> and the convolution theorem as described in the ALGORITHMS
  section. <I>psfdata</I> is interpreted as either: 1) a
  string defining the coordinates of a single object e.g. "<TT>103.3 189.2</TT>" or 2)
  the name of a text file containing the coordinates of one or 
  more objects, one object per line, with the x and y coordinates
  in columns 1 and 2 respectively.  The object coordinates, the
  size of the data region to be extracted <I>dnx</I>
  by <I>dny</I>, and the size of the kernel to be computed <I>pnx</I> and
  <I>pny</I>, determine 
  the input and reference image regions used to compute the psf matching
  function.
  These image regions should be selected with care. Ideal regions 
  contain a single high signal-to-noise unsaturated star which has no close
  neighbors and is well centered on a pixel.
  <P>
  If <I>center</I> is "<TT>yes</TT>" and <I>convolution</I> is "<TT>image</TT>", the objects
  in <I>psfdata</I> are centered before
  the data region is extracted.  Centering should be on if the objects
  are stellar, particularly if their coordinates were read from the image
  display cursor. Centering should be off if the objects are non-stellar and
  do not have well-defined centers.
  <P>
  If the <I>background</I> fitting algorithm is other than "<TT>none</TT>" and
  <I>convolution</I> is "<TT>image</TT>", the background for each object is fit using 
  data inside the region defined by
  <I>dnx</I> and <I>dny</I> but outside the region defined by
  <I>pnx</I> by <I>pny</I>. Bad data can be removed from the
  background fit by setting the parameters <I>loreject</I> and <I>hireject</I>.
  A cosine bell function is applied to the edges of the data region
  after background fitting but before computing the psf matching function
  if the <I>apodize</I> parameter is &gt; 0.0.
  <P>
  If <I>psfdata</I> contains more than one object, the extracted image data
  is weighted by the total intensity in the extracted region after
  background subtraction, and averaged to produce a single smoothed
  data region for each reference and input image.
  <P>
  If <I>convolution</I> = "<TT>psf</TT>",
  the psf matching function is computed directly from the input image
  and reference
  image point-spread functions
  using the convolution theorem as described in the ALGORITHMS section.
  In this case  <I>psfdata</I> is the list of input image psfs  and
  <I>reference</I> are the corresponding reference image psfs written by
  by some external psf modeling task. 
  If <I>convolution</I> is "<TT>psf</TT>",
  centering and background fitting
  are assumed to have been performed by the psf modeling task and are not
  performed by PSFMATCH.
  <P>
  PSFMATCH requires that the total power in the psf matching function
  before normalization be the ratio
  of the integrated flux of the reference image/psf over the integrated
  flux of the input image/psf. If <I>fluxratio</I> is INDEF, PSFMATCH
  estimates this number internally as described in the ALGORITHMS section,
  otherwise the <I>fluxratio</I> is set to the value supplied by the user.
  <P>
  If <I>convolution</I> is "<TT>kernel</TT>", PSFMATCH reads the psf matching function
  from the images in <I>kernel</I>  which were either
  created during a previous run of PSFMATCH or by a separate task.
  <P>
  PSFMATCH provides several options for filtering out the ill-behaved
  noise-dominated high frequency components of the psf matching function
  that are produced when the ratio of reference / input image of psf
  fourier transforms is taken.
  <P>
  If <I>filter</I> is set to "<TT>cosbell</TT>", a cosine bell function
  with a taper defined by <I>sx1</I>, <I>sx2</I>, <I>sy1</I>, and <I>sy2</I> and
  symmetry defined by radsym is applied to
  the psf matching function in frequency space. This filter
  sets all the frequency components greater than <I>sx2</I> and <I>sy2</I>
  to 0.0 and leaves all frequency components inside <I>sx1</I> and <I>sy1</I>
  unaltered. Users should exercise this option with caution as the effect
  of the filtering process can be to significantly
  broaden the computed psf matching function as described in the ALGORITHMS
  section.
  <P>
  An alternative approach to dealing with the noisy
  high frequency components of the psf
  matching function it is to replace them with a reasonable guess. If the
  matching function is approximately gaussian then its fourier transform is also
  approximately gaussian and the low frequency components can be modeled
  reliably with an elliptical gaussian function. The model derived from the low
  frequency components of the matching can then be used to replace the high
  frequency components.
  If <I>filter</I> is set to "<TT>replace</TT>", those high frequency components
  of the matching function  which have less than a fraction
  <I>threshold</I> of their total power in the equivalent high frequency
  components of the divisor or input image transform,
  are replaced by a model computed by fitting a gaussian to the low frequency
  components of the matching function, as described in the ALGORITHMS section.
  If <I>filter</I> = "<TT>model</TT>" then the entire psf matching function
  is replaced with the best fitting gaussian model.
  <P>
  Another problem can arise during the computation of the psf matching
  function . Occasionally it is not possible by means of a single execution
  of PSFMATCH to match the reference and input image psfs. An example
  of this situation
  is the case where the seeing of the reference and input images
  was comparable but the declination guiding error in the reference
  image was larger than the error in the input image.
  In this case input image  needs to be convolved to the resolution of 
  the reference image. However it is also the case
  that the guiding error in ra in the input image is greater than the guiding
  error  in ra in the reference image. In this case the reference image needs
  to be convolved to the resolution of the input image along the other axis.
  If no corrective action is taken by the task, the 
  first time PSFMATCH is run the values of the psf matching function along
  the ra axis will be greater than the computed fluxratio, resulting in
  unrealistic action
  along this axis. PSFMATCH avoids this situation by internally limiting
  the psf matching function to a maximum value of fluxratio computed as described
  above. 
  <P>
  By default the psf matching function is normalized to unit power before 
  output. This may not be what is desired since if carefully computed the
  internally computed quantity a contains information about differences
  in exposure time, transparency, etc. If <I>normfactor</I> is set to
  a number of INDEF, the total power of the psf matching function will be
  set to that value of <I>fluxratio</I> respectively.
  <P>
  If a list of output images names has been supplied then the computed
  psf matching function is applied to the input images to produce
  the output images using the boundary extension algorithm
  defined by <I>boundary</I> and <I>constant</I>.
  <P>
  In non-interactive mode the parameters are set at task startup time and
  the input images are processed sequentially. If the <I>verbose</I> flag
  is set messages about the progress of the task are printed on he 
  screen as the task is running.
  <P>
  In interactive mode the user can mark the regions to be used to compute
  the psf matching function on the image display, show/set the data
  and algorithm parameters, compute, recompute, and plot the psf matching
  function and its accompanying fourier spectrum, and experiment with the
  various filtering and modeling options.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_cursor_commands">CURSOR COMMANDS</A></H2>
  <! BeginSection: 'CURSOR COMMANDS'>
  <UL>
  <P>
  The following graphics cursor commands are currently available in
  PSFMATCH.
  <P>
  <PRE>
  	Interactive Keystroke Commands
  <P>
  <P>
  ?	Print help 
  :	Colon commands
  k	Draw a contour plot of the psf matching kernel
  p	Draw a contour plot of the psf matching kernel fourier spectrum
  x	Draw a column plot of the psf matching kernel / fourier spectrum
  y	Draw a line plot of the psf matching kernel / fourier spectrum
  r	Redraw the current plot
  f	Recompute the psf matching kernel
  w	Update the task parameters
  q	Exit
  <P>
  <P>
  	Colon Commands
  <P>
  <P>
  :mark	[file]		Mark objects on the display
  :show			Show current values of the parameters
  <P>
  <P>
  	Show/Set Parameters
  <P>
  <P>
  :input	    [string]	    Show/set the current input image name
  :reference  [string]	    Show/set the current reference image/psf name
  :psf	    [file/string]   Show/set the objects/input psf list
  :psfimage   [string]	    Show/set the current input psf name
  :kernel	    [string]	    Show/set the current psf matching kernel name
  :output     [string]	    Show/set the current output image name
  <P>
  :dnx	    [value]	    Show/set x width of data region(s) to extract
  :dny	    [value]	    Show/set y width of data region(s) to extract
  :pnx	    [value]	    Show/set x width of psf matching kernel
  :pny	    [value]	    Show/set y width of psf matching kernel
  :center	    [yes/no]	    Show/set the centering switch
  :background [string]        Show/set the background fitting function
  :loreject   [value]	    Show/set low side k-sigma rejection parameter
  :hireject   [value]	    Show/set high side k-sigma rejection parameter
  :apodize    [value]	    Show/set percent of endpoints to apodize
  <P>
  :filter	    [string]	    Show/set the filtering algorithm
  :fluxratio  [value]	    Show/set the reference/input psf flux ratio
  :sx1	    [value]	    Show/set inner x frequency for cosbell filter
  :sx2	    [value]	    Show/set outer x frequency for cosbell filter
  :sy1	    [value]	    Show/set inner y frequency for cosbell filter
  :sy2	    [value]	    Show/set outer y frequency for cosbell filter
  :radsym	    [yes/no]        Show/set radial symmetry for cosbell filter
  :threshold  [value]	    Show/set %threshold for replace/modeling filter
  :normfactor [value]	    Show/set the kernel normalization factor
  </PRE>
  <P>
  </UL>
  <! EndSection:   'CURSOR COMMANDS'>
  <H2><A NAME="s_algorithms">ALGORITHMS</A></H2>
  <! BeginSection: 'ALGORITHMS'>
  <UL>
  <P>
  The problem of computing the psf matching function can expressed
  via the convolution theorem as shown below.
  In the following expressions r is the reference
  image data or reference image psf, i is the input image data or input image
  psf, k is the unit power psf matching
  function,
  a is a scale factor specifying the ratio of the total
  power in the reference data or psf to the total power in the input data or
  psf, * is the convolution operator, and FT is the fourier transform operator.
  <P>
  <PRE>
  	r = ak * d
  	R = FT (r)
  	I = FT (i)
  	aK = R / I
  	ak = FT (aK)
  </PRE>
  <P>
  The quantity ak is the desired psf matching function and aK is its fourier
  transform.
  <P>
  If the background was accurately removed from the image or psf data before the
  psf matching function was computed, the quantity a is simply the central
  frequency component of the computed psf matching function aK as shown below.
  <P>
  <PRE>
  	aK[0,0] = a = sum(r) / sum(i)
  </PRE>
  <P>
  If the background was not removed from the image or psf data before the
  psf matching function was computed the previous expression is not valid.
  The computed aK[0,0] will include an offset and a must be estimated
  in some other manner. The approach taken by PSFMATCH in this circumstance
  is to fit a gaussian model to the absolute value of 1st and 2nd frequencies
  of R and I along the x and y axes independently, average the fitted x and y
  amplitudes, and set aK[0,0] to the ratio of the resulting fitted amplitudes
  as shown below.
  <P>
  <PRE>
  	      a = amplitude (R) / amplitude (I)
  	        = (sum(r) - sum(skyr)) / (sum(i) - sum(skyi))  
  	      aK[0,0] = a
  </PRE>
  <P>
  This approach will work well as long as the image data or psf is reasonably
  gaussian but may not work well in arbitrary image regions. If the user is
  dissatisfied with either of the techniques described above they can
  set aK[0,0] to a pre-determined value of their own.
  <P>
  If a filter is applied to the computed psf matching function in frequency
  space then instead of computing
  <P>
  <PRE>
  	       ak = FT (aK)
  </PRE>
  <P>
  PSFMATCH actually computes
  <P>
  <PRE>
  	       ak' = FT (aKF) = ak * f
  </PRE>
  <P>
  where F is the applied filter in frequency space and f is its
  fourier transform. Care should be taken in applying any filter.
  For example if F is the step function, then ak' will be the desired kernel
  ak convolved with f, a sinc function of frequency 2 * PI / hwidth where
  hwidth is the half-width of the step function, and the resulting k'
  will be too broad.
  <P>
  If the user chooses to replace the high frequency components of the psf
  matching function with a best guess, PSFMATCH performs the following
  steps:
  <P>
  <PRE>
  1) fits an elliptical gaussian to those frequency components of the fourier
  spectrum of aK for which for which the amplitude of I is greater
  than threshold * I[0,0] to determine the geometry of the ellipse
  <P>
  2) uses the fourier shift theorem to preserve the phase information in the
  model and solve for any x and y shifts
  <P>
  3) replace those frequency components of aK for which the fourier spectrum
  of I is less than threshold * I[0,0] with the model values
  <P>
  		or alternatively
  <P>
  replace all of aK with the model values
  </PRE>
  <P>
  </UL>
  <! EndSection:   'ALGORITHMS'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Psf match a list of input images taken at different epochs with variable
  seeing conditions to a reference image with the poorest seeing by marking
  several high signal-to-noise isolated stars on the displayed reference image
  and computing the psf matching function directly from the input and reference
  image data. User makes two runs with psfmatch one to compute and check the
  kernel images and one to match the images.
  <P>
  <PRE>
  	cl&gt; display refimage 1 fi+
  <P>
  	cl&gt; rimcursor &gt; objects
  <P>
  	cl&gt; psfmatch @inimlist refimage objects @kernels dnx=31 \<BR>
  	    dny=31 pnx=15 pny=15
  <P>
  	cl&gt; imstat @kernels
  <P>
  	cl&gt; psfmatch @inlist refimage objects @kernels          \<BR>
  	    output=@outlist convolution="kernel"
  </PRE>
  <P>
  2. Psf match two spectra using a high signal-to-noise portion of the
  data in the middle of the spectrum. Since the spectra are registered
  spatially and there is little data available for background fitting the
  user chooses to turn centering off and set the backgrounds manually.
  <P>
  <PRE>
  	cl&gt; psfmatch inspec refspec "303.0 1.0" kernel         \<BR>
  	    output=outspec dnx=31 dny=31 pnx=15 pny=15 center- \<BR>
  	    back="403.6 452.0"
  </PRE>
  <P>
  3. Psf match two images using psf functions inpsf and refpsf computed with
  the daophot package phot/psf/seepsf tasks. Since the kernel is fairly
  large use the stsdas fourier package task fconvolve to do the actual
  convolution. The boundary extension algorithm in fconvolve is equivalent
  to setting the psfmatch boundary extension parameters boundary and
  constant to "<TT>constant</TT>" and "<TT>0.0</TT>" respectively.
  <P>
  <PRE>
  	cl&gt; psfmatch inimage refpsf inpsf kernel convolution=psf
  <P>
  	cl&gt; fconvolve inimage kernel outimage
  </PRE>
  <P>
  4. Psf match two images interactively using the image data itself to
  compute the psf matching function.
  <P>
  <PRE>
  	cl&gt; psfmatch inimage refimage objects kernel interactive+
  <P>
  	    ... a contour plot of the psf matching function appears
  		with the graphics cursor ready to accept commands
  <P>
              ... type x and y to get line and column plots of the psf
                  matching function at various points and k to return
                  to the default contour plot
  <P>
  	    ... type ? to get a list of the available commands
  <P>
  	    ... type :mark to define a new set of objects
  <P>
  	    ... type f to recompute the psf matching function using
                  the new objects
  <P>
   	    ... increase the data window to 63 pixels in x and y
                  with the :dnx 63 and :dny 63 commands, at the
                  same time increase the psf function size to 31 with
  		the colon commands :pnx 31 and :pny 31
  <P>
  	    ... type f to recompute the psf matching function using
                  the new data and kernel windows
  <P>
  	    ... type q to quit the task, and q again to verify the previous
                  q command
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_time_requirements">TIME REQUIREMENTS</A></H2>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  </UL>
  <! EndSection:   'TIME REQUIREMENTS'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  convolve, gauss, stsdas.fconvolve, digiphot.daophot.psf
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'CURSOR COMMANDS' 'ALGORITHMS' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>