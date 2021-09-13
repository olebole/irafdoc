.. _rskysub:

rskysub — Sky subtract images using running mean or median
==========================================================

**Package: proto**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  rskysub -- sky subtract images using running mean or median
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  rskysub input output
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>The list of input images to be sky subtracted in time of observation order.
  </DD>
  </DL>
  <DL>
  <DT><B>output</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>The list of output sky subtracted images. The number of output images must
  equal the number of input images.  If output is "<TT>default</TT>", "<TT>dir$default</TT>", or
  "<TT>dir$</TT>" then for every input image an output image called "<TT>dir$image.sub.?</TT>"
  is created, where "<TT>dir$</TT>" is the optional directory specification, "<TT>image</TT>" is
  the root input image name, and "<TT>?</TT>" is the next available version number.
  </DD>
  </DL>
  <DL>
  <DT><B>imasks = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='imasks' Line='imasks = ""'>
  <DD>The optional list of input image masks. The input image masks are assumed to
  consist of 0's in good pixel regions and &gt; 0 integer values elsewhere. The
  number of input images masks must be 0, 1, or equal to the number of input
  images. If imasks is "<TT>default</TT>", "<TT>dir$default</TT>", or "<TT>dir$</TT>" then for every input
  image a default input image mask called "<TT>dir$image.obm.?</TT>" is searched for,
  where "<TT>dir$</TT>" is the optional directory specification, "<TT>image</TT>" is the root
  input image name, and "<TT>?</TT>" is the highest available version number.
  </DD>
  </DL>
  <DL>
  <DT><B>omasks = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='omasks' Line='omasks = ""'>
  <DD>The optional list of output masks. If output masks are defined they are
  used to created the sky image in place of the input masks. The output masks
  are a combination of the original input mask and pixels masked during the
  input image scale factor computation and consist of 0's in good data regions
  and 1's elsewhere. Output masks are only computed if <I>scale</I> = "<TT>median</TT>".
  The number of output masks must be 0 or equal to the number of input images.
  If imasks is "<TT>default</TT>", "<TT>dir$default</TT>", or "<TT>dir$</TT>" then for every input image
  an output mask image called "<TT>dir$image.skm.?</TT>" is created, where "<TT>dir$</TT>" is
  the optional directory specification, "<TT>image</TT>" is the root input image name,
  and "<TT>?</TT>" is the next available version number.
  </DD>
  </DL>
  <DL>
  <DT><B>hmasks = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='hmasks' Line='hmasks = ""'>
  <DD>The list of output holes masks.  The holes masks defined bad pixels in the
  output images, i.e. those for which the underlying sky image was undefined.
  Holes masks are created only if <I>hmasks</I> is defined and there is at least
  1 undefined sky image pixel in the output image.  Holes masks contain 0's in
  undefined sky regions and 1's elsewhere.  If hmasks is "<TT>default</TT>", "<TT>dir$default</TT>",
  or "<TT>dir$</TT>" then for every input image an output mask image called
  "<TT>dir$image.hom.?</TT>" is created, where "<TT>dir$</TT>" is the optional directory
  specification, "<TT>image</TT>" is the root input image name, and "<TT>?</TT>" is the next
  available version number.
  </DD>
  </DL>
  <P>
  <DL>
  <DT><B>rescale = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='rescale' Line='rescale = yes'>
  <DD>Force recomputation of the individual input image scale factors  even though
  they have been previously computed and stored in the keyword <I>skyscale</I>?
  </DD>
  </DL>
  <DL>
  <DT><B>scale = "<TT>median</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='scale' Line='scale = "median"'>
  <DD>The method used to compute the individual image scale factors. The options
  are:
  <DL>
  <DT><B>none</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='none' Line='none'>
  <DD>The individual scale factors are all set to 1.0.
  </DD>
  </DL>
  <DL>
  <DT><B>!&lt;keyword&gt;</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='' Line='!&lt;keyword&gt;'>
  <DD>The individual scale factors are all set to the value of the input image header
  keyword <I>keyword</I>.
  </DD>
  </DL>
  <DL>
  <DT><B>median</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='median' Line='median'>
  <DD>The individual scale factors are set to 1 / median. The medians are estimated
  using the input masks <I>imasks</I>, input image section <I>statsec</I>,
  the minimum and maximum good data values <I>lower</I> and <I>upper\R, the
  clipping factors fImaxiter</I>, <I>lnsigrej</I>, and <I>unsigrej</I> and the
  histogram binning parameter <I>binwidth</I>.
  </DD>
  </DL>
  <DL>
  <DT><B>@&lt;file&gt;</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='' Line='@&lt;file&gt;'>
  <DD>The individual image scale factors are read from the file <I>file</I>. 
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B>skyscale = "<TT>SKYSCALE</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='skyscale' Line='skyscale = "SKYSCALE"'>
  <DD>The image header keyword containing the computed scaling factor.
  <I>Skyscale</I> is written to both the input and output images.
  </DD>
  </DL>
  <P>
  <DL>
  <DT><B>statsec = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='statsec' Line='statsec = ""'>
  <DD>The input image section used to compute the individual image scaling factors.
  Statsec is independent of the input image section if any.
  </DD>
  </DL>
  <DL>
  <DT><B>lower = INDEF, upper = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lower' Line='lower = INDEF, upper = INDEF'>
  <DD>The minimum and maximum input image good data values.
  </DD>
  </DL>
  <DL>
  <DT><B>maxiter = 20</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='maxiter' Line='maxiter = 20'>
  <DD>The maximum number of clipping iterations.
  </DD>
  </DL>
  <DL>
  <DT><B>lnsigrej = 3.0, unsigrej = 3.0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lnsigrej' Line='lnsigrej = 3.0, unsigrej = 3.0'>
  <DD>The lower and upper side sigma clipping factors.
  </DD>
  </DL>
  <DL>
  <DT><B>binwidth = 0.1</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='binwidth' Line='binwidth = 0.1'>
  <DD>The histogram bin width in sigma used in estimating the median value.
  </DD>
  </DL>
  <P>
  <DL>
  <DT><B>resubtract = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='resubtract' Line='resubtract = yes'>
  <DD>Force recomputation and subtraction of the sky image even though it exists
  already ?
  </DD>
  </DL>
  <DL>
  <DT><B>combine = "<TT>average</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='combine' Line='combine = "average"'>
  <DD>The method used to create the sky images. The options are "<TT>average</TT>" and
  "<TT>median</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>ncombine = 6</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ncombine' Line='ncombine = 6'>
  <DD>The default number of images used to create the sky images.
  </DD>
  </DL>
  <DL>
  <DT><B>nmin = 3</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nmin' Line='nmin = 3'>
  <DD>The minimum number of images used to create the sky images.
  </DD>
  </DL>
  <DL>
  <DT><B>nlorej = 0, nhirej = 0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nlorej' Line='nlorej = 0, nhirej = 0'>
  <DD>The number of high and low side pixels to reject if <I>combine</I> is "<TT>average</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>blank = 0.0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='blank' Line='blank = 0.0'>
  <DD>The value assigned to undefined output image pixels, i.e. those for
  which the corresponding sky image pixel is undefined.
  </DD>
  </DL>
  <DL>
  <DT><B>skysub = "<TT>SKYSUB</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='skysub' Line='skysub = "SKYSUB"'>
  <DD>The sky subtraction processing keyword which is written to the output
  image when processing is complete.
  </DD>
  </DL>
  <DL>
  <DT><B>holes = "<TT>HOLES</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='holes' Line='holes = "HOLES"'>
  <DD>The homes mask name keyword which is written to the output image if an output
  holes mask is created.
  </DD>
  </DL>
  <P>
  <DL>
  <DT><B>cache = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='cache' Line='cache = yes'>
  <DD>Cache the input images in memory if possible ?
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes'>
  <DD>Print messages about the progress of the task ?
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  RSKYSUB computes the average sky image for each image in the input image
  list <I>inlist</I> using a running mean or median technique and subtracts
  it from the input image to create the output sky subtracted images
  <I>outlist</I>. The input image list is assumed to be ordered by time of
  observation. If the input image masks list <I>imasks</I> is defined then the
  input image pixels in the bad pixel regions are removed from the sky statistics
  and sky image computation. RSKYSUB optionally creates a list of output pixel
  masks <I>omasks</I> and a list of holes masks <I>hmasks</I>.
  <P>
  The input masks <I>imasks</I> can be specified in a variety of ways as
  shown below.
  <P>
  <PRE>
                 "" - empty mask, use all the pixels
              EMPTY - empty mask, use all the pixels
           !KEYWORD - use mask specified by  header keyword KEYWORD
          !^KEYWORD - use inverse of mask specified by  header keyword KEYWORD
               mask - use specified mask
              ^mask - use inverse of specified mask
  </PRE>
  <P>
  In all cases the mask values are assumed to be 0 in good data regions and
  non-zero in rejected data regions. The input masks may in pixel list, e.g.
  "<TT>.pl</TT>" format, or any supported integer image format, e.g. "<TT>.imh</TT>", "<TT>.fits</TT>", etc.
  <P>
  The optional output pixel masks <I>omasks</I> are a combination of the
  input image masks and the scaling factor computation masks. They consist
  entirely of 0's and 1's with 0's defining the good data regions.
  <P>
  The optional output holes masks <I>hmasks</I> which specify those pixels
  in the output images which are undefined consist entirely of 1's and 0's
  with 0's defining the holes.
  <P>
  Before beginning the sky subtraction step RSKYSUB computes a scaling factor for
  each individual input image in <I>inlist</I> and stores it in the input image
  header keyword <I>skyscale</I>. If <I>scale</I> is "<TT>median</TT>" then the median of
  the input image pixels is computed using the input image masks <I>imasks</I>,
  the good data limits <I>lower</I> and <I>upper</I>, the clipping factors
  <I>maxiter</I>, <I>lnsigrej</I>, and <I>unisgrej</I>, and the histogram
  resolution parameter <I>binwidth</I>. The scaling factor is set to 1 / median.
  If <I>scale</I> is "<TT>none</TT>", "<TT>!&lt;keyword&gt;</TT>", or "<TT>@&lt;file&gt;</TT>" the individual
  scale factors are set to 1, read from the input image header keyword
  <I>&lt;keyword&gt;</I>, or from a file <I>@&lt;file&gt;</I> respectively. If <I>rescale</I> is
  yes and <I>scale</I> is "<TT>median</TT>" then the scaling computation is  redone
  regardless of whether or not the <I>skyscale</I> keyword is present in the
  input image header.
  <P>
  RSKYSUB computes the sky image for each input image by multiplying each
  input image by the value of its scaling factor  and then computing the
  combination of <I>ncombine</I> neighbor images using the algorithm
  specified by <I>combine</I>. If <I>combine</I> is average then the
  <I>nlorej</I> and <I>nhirej</I> lowest and highest pixels are rejected from
  the stack to be combined. For example if the number of input images is 25 and
  ncombine is 6 then images 2-4 are used to compute the sky image for image 1,
  images 10-12 and 14-16 are used to compute the sky for image 13, and images
  22-24 are used to compute the sky image for image 25. There must be a minimum
  of <I>nmin</I> neighbor images or the sky image will not be computed. If the
  input masks are defined then pixels in bad regions are also rejected
  from the final sky image computation. Undefined output image pixels,
  i.e. those for which the corresponding sky image pixel is undefined, are
  assigned the value <I>blank</I>. The sky subtraction processing keyword
  <I>skysub</I> is written to the output image when sky subtraction is complete.
  <P>
  If <I>cache</I> is "<TT>yes</TT>" then RSKYSUB will attempt to buffer the active images
  in memory and will run significantly faster. If <I>verbose</I> = yes then
  the task prints messages about its actions as it goes along.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Sky subtract a list of 25 images without masking.
  <P>
  <PRE>
  cl&gt; rskysub @inlist @outlist maxiter=10 lnsigrej=5.0 unsigrej=5.0
  </PRE>
  <P>
  <P>
  2. Sky subtract the same list of 25 images with masking where the masks
  are assumed to be stored in the BPM keyword.
  <P>
  <PRE>
  cl&gt; rskysub @inlist @outlist imasks="!BPM" maxiter=10 lnsigrej=5.0 \<BR>
  unsigrej=5.0
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Time requirements</H3>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  <P>
  </UL>
  <! EndSection:   'TIME REQUIREMENTS'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  <P>
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  imcombine, imexpr
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
