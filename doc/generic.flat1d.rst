.. _flat1d:

flat1d — Make flat field by fitting a 1D func. to the lines or columns
======================================================================

**Package: generic**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  flat1d -- Make flat fields by fitting a 1D function to the image
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage	</H3>
  <! BeginSection: 'USAGE	'>
  <UL>
  flat1d input output
  </UL>
  <! EndSection:   'USAGE	'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>Calibration images to be used to make the flat fields.  The images may
  contain image sections.  Only the region covered by the section will be
  modified in the output image.
  </DD>
  </DL>
  <DL>
  <DT><B>output</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>Flat field images to be created or modified.  The number of output images
  must match the number of input images.  If an output image does not exist
  it is first created and initialized to unit response.
  </DD>
  </DL>
  <DL>
  <DT><B>axis = 1</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='axis' Line='axis = 1'>
  <DD>Axis along which the one dimensional fitting is done.  Axis 1 corresponds
  to fitting the image lines and axis 2 corresponds to fitting the columns.
  </DD>
  </DL>
  <DL>
  <DT><B>interactive = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='interactive' Line='interactive = yes'>
  <DD>Set the fitting parameters interactively?
  </DD>
  </DL>
  <DL>
  <DT><B>sample = "<TT>*</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='sample' Line='sample = "*"'>
  <DD>Lines or columns to be used in the fits.
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
  <DT><B>function = spline3</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='function' Line='function = spline3'>
  <DD>Function to be fit to the image lines or columns.  The functions are
  "<TT>legendre</TT>" (legendre polynomial), "<TT>chebyshev</TT>" (chebyshev polynomial),
  "<TT>spline1</TT>" (linear spline), and "<TT>spline3</TT>" (cubic spline).  The functions
  may be abbreviated.
  </DD>
  </DL>
  <DL>
  <DT><B>order = 1</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='order' Line='order = 1'>
  <DD>The order of the polynomials or the number of spline pieces.
  </DD>
  </DL>
  <DL>
  <DT><B>low_reject = 2.5, high_reject = 2.5</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='low_reject' Line='low_reject = 2.5, high_reject = 2.5'>
  <DD>Low and high rejection limits in units of the residual sigma.
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
  <DL>
  <DT><B>minflat = 0.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='minflat' Line='minflat = 0.'>
  <DD>When the fitted value is less than the value of this parameter the flat
  field value is set to unity.
  </DD>
  </DL>
  <DL>
  <DT><B>graphics = "<TT>stdgraph</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='graphics' Line='graphics = "stdgraph"'>
  <DD>Graphics device for interactive graphics output.
  </DD>
  </DL>
  <DL>
  <DT><B>cursor = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='cursor' Line='cursor = ""'>
  <DD>Graphics cursor input
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Flat fields are created containing only the small scale variations in the
  calibration images.  The large scale variations in the images are modeled
  by fitting a function to each image line or column with deviant pixel rejection.
  The flat field values are obtained by taking the ratio of the image values
  to the function fit.  However, if the fitted value is less than the
  parameter <I>minflat</I> the flat field value is set to unity.
  <P>
  The function fitting parameters may be set interactively when the interactive
  flag is set using the interactive curve fitting package <B>icfit</B>.
  The cursor mode commands for this package are described in a separate
  help entry under "<TT>icfit</TT>".  For two dimensional images the user is
  prompted for the sample line or column or a blank-separated range to be
  averaged and graphed.
  Note that the lines or columns are relative the input image section; for
  example line 1 is the first line of the image section and not the first
  line of the image.  Any number of lines or columns may be examined.
  When satisfied with the fit parameters the user
  responds with a carriage return to the line or column prompt.
  The function is then fit to all the lines or columns and the flat field
  ratios are determined.
  <P>
  If the output image does not exist initially it is created with the same
  size as the input image <I>without</I> an image section and initialized
  to unit response.  Subsequently the flat field data modifies the pixel
  values in the output image.  Input image sections may be used to restrict
  the region in which the flat field response is determined leaving the
  rest of the output image unmodified.  This ability is particularly useful
  when dealing with multi-aperture data.
  <P>
  This task is very similar to <B>fit1d</B> with the addition of the
  parameter <I>minflat</I> and the deletion of the parameter <I>type</I>
  which is always "<TT>ratio</TT>".
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1.  Create a flat field from the calibration image "<TT>quartz</TT>" with the
  spectrum running along the lines.  Exclude the first and last columns,
  use a spline fit of 25 pieces (a width of 32 pixels over 800 columns),
  and set grow to 4 pixels.
  <P>
  <PRE>
  	cl&gt; flat1d quartz flat order=25 sample="2:799" grow=4 \<BR>
  	&gt;&gt;&gt; interactive=no
  <P>
  			or
  <P>
  	cl&gt; flat1d quartz[2:799,*] flat order=25 grow=4 inter-
  </PRE>
  <P>
  The fitting parameters may be set interactively in which case the fitting
  parameters need not be specified.  The command would be
  <P>
  <PRE>
  	cl&gt; flat1d quartz flat
  	quartz: Fit column = 1 10
  	quartz: Fit column =
  </PRE>
  <P>
  The user selects sample columns to be fit interactively with the interactive
  curve fitting package.  When satisfied with the fit parameters
  respond with a carriage return to the prompt.  The function is then fit to
  all the columns and the flat field ratios are determined.
  <P>
  2.  As an example for multi-slit spectra the locations of the slits are
  determined and a file containing the image sections is created.
  Since there must be the same number of output images another file
  containing the output images is also created.  For
  example the files might contain
  <P>
  <PRE>
  	  File quartzs			File flats
  	_______________			__________
  	quartz[23:40,*]			   flat
  	quartz[55:61,*]			   flat
  	quartz[73:84,*]			   flat
  </PRE>
  <P>
  A flat field for the slits is then obtained with the command
  <P>
  	cl&gt; flat1d @quartzs flats axis=2
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Revisions</H3>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B>FLAT1D V2.10.3</B></DT>
  <! Sec='REVISIONS' Level=0 Label='FLAT1D' Line='FLAT1D V2.10.3'>
  <DD>The image header keyword "<TT>CCDMEAN = 1.</TT>" is now added or updated.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'REVISIONS'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  The creation of multi-slit files and the need for an equal number of
  repeated output files is annoying.  It will be worked on in the future.
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  fit1d, icfit
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE	' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'REVISIONS' 'BUGS' 'SEE ALSO'  >
  
