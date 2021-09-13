.. _crtpict:

crtpict — Generate greyscale plots of IRAF images
=================================================

**Package: plot**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  crtpict -- make a hardcopy of an IRAF image
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  crtpict input 
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>Input images to be processed.
  </DD>
  </DL>
  <DL>
  <DT><B>device = "<TT>dicomed</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='device' Line='device = "dicomed"'>
  <DD>The output device.
  </DD>
  </DL>
  <DL>
  <DT><B>auto_fill = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='auto_fill' Line='auto_fill = yes'>
  <DD>If set to yes, the image will be scaled to fit the device viewport.
  The aspect ratio is always preserved when <I>auto_fill</I> = yes.
  </DD>
  </DL>
  <DL>
  <DT><B>xmag = 1.0, ymag = 1.0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xmag' Line='xmag = 1.0, ymag = 1.0'>
  <DD>When <I>auto_fill</I> = no, the x and y magnification ratios are specified
  by these parameters.
  </DD>
  </DL>
  <DL>
  <DT><B>replicate = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='replicate' Line='replicate = yes'>
  <DD>The image pixels are block replicated to fit the device viewport when
  <I>replicate</I> = yes.  Otherwise, the pixels are linearly interpolated
  to match the device pixels.
  </DD>
  </DL>
  <DL>
  <DT><B>x_block_avg = 1, y_block_avg = 1</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='x_block_avg' Line='x_block_avg = 1, y_block_avg = 1'>
  <DD>These parameters are used when <I>replicate</I> = no to decrease the
  effective output device resolution, and speed up the interpolation.  The
  pixels are interpolated to the block averaged output device, then
  block replicated to fill the device viewport.
  </DD>
  </DL>
  <DL>
  <DT><B>ztrans = "<TT>auto</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ztrans' Line='ztrans = "auto"'>
  <DD>This parameter specifies how the image intensities are mapped into the 
  greyscale values of the output device.  Intensity z1 maps to black, z2 to white.
  The 4 choices for <I>ztrans</I> are:
  <PRE>
  <P>
  	"auto"		- z1 and z2 centered on median of image
  	"min_max"	- set z1 and z2 to specified intensities
  	"none" 		- truncate intensities to fit output range
  	"user"		- user supplies look up table of values
  </PRE>
  </DD>
  </DL>
  <DL>
  <DT><B>lutfile = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lutfile' Line='lutfile = ""'>
  <DD>Name of text file containing the look up table when <I>ztrans</I> = user. 
  The table should contain two columns per line; column 1 contains the 
  intensity, column 2 the desired greyscale output.  
  </DD>
  </DL>
  <DL>
  <DT><B>contrast = 0.25</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='contrast' Line='contrast = 0.25'>
  <DD>Used when automatically determining z1 and z2.  The slope of the transfer
  function is divided by <I>contrast</I>, so negative values of <I>contrast</I>
  result in a negative transfer function.
  </DD>
  </DL>
  <DL>
  <DT><B>nsample_lines = 25</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nsample_lines' Line='nsample_lines = 25'>
  <DD>Used when automatically determining z1 and z2, this parameter sets the number 
  of image lines to be sampled when determining the median.
  </DD>
  </DL>
  <DL>
  <DT><B>z1 = 0.0, z2 = 0.0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='z1' Line='z1 = 0.0, z2 = 0.0'>
  <DD>These parameters are used when <I>ztrans</I> = "<TT>min_max</TT>", to specify which
  pixel values map to black and white.  
  </DD>
  </DL>
  <DL>
  <DT><B>perimeter = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='perimeter' Line='perimeter = yes'>
  <DD>Draw annotated axes around the plot perimeter?
  </DD>
  </DL>
  <DL>
  <DT><B>image_fraction = 0.70</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='image_fraction' Line='image_fraction = 0.70'>
  <DD>The fraction of the vertical device viewport reserved for the image.
  </DD>
  </DL>
  <DL>
  <DT><B>graphics_fraction = 0.20</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='graphics_fraction' Line='graphics_fraction = 0.20'>
  <DD>The fraction of the vertical device viewport reserved for histogram
  plots and id information. 
  </DD>
  </DL>
  <DL>
  <DT><B>greyscale_fraction = 0.05</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='greyscale_fraction' Line='greyscale_fraction = 0.05'>
  <DD>The fraction of the vertical device viewport reserved for the greyscale
  step wedge.  
  </DD>
  </DL>
  <DL>
  <DT><B>output = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output = ""'>
  <DD>Output metacode is appended to this file.
  By naming an output file, the metacode can be "<TT>trapped</TT>", and the normal
  spooling process intercepted.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Procedure <B>crtpict</B> makes a photographic hardcopy plot of IRAF images.
  <P>
  The image can be automatically scaled to fill the output plotting window, with 
  the aspect ratio preserved, by setting <B>auto_fill</B> = yes.  When 
  <B>auto_fill</B> = no, magnification factors for the axes are entered as 
  <B>xmag</B> and <B>ymag</B>, where negative values (as well as fractional 
  values &lt; 1.0), indicate that the image is to be reduced.  By default, the
  imaged is enlarged by block replication.  By setting <B>replicate</B> = no,
  the image will be linearly interpolated to fit the device area.  (In this
  case, to speed things up, the <B>block_avg</B> parameters can be set to
  reduce the effective output resolution.)  In either case, if an image needs
  to be reduced in size, it will be decimated.   
  <P>
  Four methods of determining the greyscale transformation are available.
  When <I>ztrans</I> = "<TT>none</TT>", no transformation between intensity and 
  greyscale level occurs, the intensities are simply copied, which will most
  likely result in truncation.  With this method, the lowest bits of each pixel, 
  the lowest level variations, are always shown, regardless of the dynamic 
  range of the image.
  <P>
  When <I>ztrans</I> = "<TT>auto</TT>",
  the greyscale levels are automatically centered on the median of the image 
  pixels.  The window of intensities spanned by the greyscale is controlled 
  by parameter <I>contrast</I>, which is divided into the calculated slope of 
  the transfer function. The larger the absolute value of <I>contrast</I>, the 
  higher the contrast in the output image.  A subset of the image pixels are 
  used to determine the median; the number of lines sampled is 
  <I>nsample_lines</I>.
  <P>
  When <B>ztrans</B> = "<TT>min_max</TT>", intensity <B>z1</B> maps to the minimum
  greyscale level (black), <B>z2</B> maps to the maximum greyscale level
  (white) and the transfer function is linear in between these two endpoints.
  If <I>z1</I> = <I>z2</I>, the image min and max map to black and white, modified
  by <B>contrast</B>.  (NOTE:  When running <I>crtpict</I> on an image created with 
  <I>snap</I>, <B>ztrans</B> should be set to "<TT>min_max</TT>", with <B>z1</B> = 0 and
  <B>z2</B> = 1023, the maximum output value possible from the IIS.)
  <P>
  When <B>ztrans</B> = "<TT>user</TT>", a look up table of intensity values and their
  corresponding greyscale levels is read from the file specified by the
  <B>lutfile</B> parameter.  From this information, 
  <I>crtpict</I> constructs a piecewise linear look up table containing
  4096 discrete values.  
  The text format table contains two columns per line; 
  column 1 contains the intensity, column 2 the desired greyscale output.  
  The greyscale values specified by the user must match those available on
  the output device.  Task <B>showcap</B> can be used to determine the range
  of acceptable greyscale levels.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1.  To subsample every 4th pixel of a large image, fill the output area and use
  previously determined values of z1 and z2 for the greyscale transformation
  the command would be:
  <P>
      cl&gt; crtpict sunpic[*:4,*:4] ztrans=min z1=0 z2=800
  <P>
  2.  To process every image with the root name ccdpic, using default values of
  all parameters, the command would be:
  <P>
      cl&gt; crtpict ccdpic*
  <P>
  3.  To process images created with <B>snap</B>, ztrans and z2 must be changed
  from their default values:
  <P>
      cl&gt; crtpict iis.snap ztrans=min z2=1023
  <P>
  4.  Image `mypic' is processed using the look up table in file `mylut',
  <P>
      cl&gt; crtpict mypic ztrans=user lutfile=mylut
  <P>
  Where file `mylut' contains this information:
  <PRE>
  		10	40
  		1500	100
  		2500	100
  		3500	200
  		7500	255
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Timing</H3>
  <! BeginSection: 'TIMING'>
  <UL>
  For a 512 x 512 real image, <B>crtpict</B> takes about 40 cpu seconds with
  <B>auto_fill</B> and <B>replicate</B> = yes.  When <B>auto_fill</B> = yes
  but <B>replicate</B> = no, <B>crtpict</B> requires almost 400 cpu seconds.
  </UL>
  <! EndSection:   'TIMING'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  display, showcap
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIMING' 'SEE ALSO'  >
  
