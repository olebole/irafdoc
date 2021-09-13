.. _oimstatistics:

oimstatistics — IMSTATISTICS from V2.11.3
=========================================

**Package: obsolete**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  oimstatistics -- compute and print image pixel statistics
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage	</H3>
  <! BeginSection: 'USAGE	'>
  <UL>
  oimstatistics images
  </UL>
  <! EndSection:   'USAGE	'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>images</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='images' Line='images'>
  <DD>Images for which pixel statistics are to be computed.
  </DD>
  </DL>
  <DL>
  <DT><B>fields = "<TT>image,npix,mean,stddev,min,max</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fields' Line='fields = "image,npix,mean,stddev,min,max"'>
  <DD>The statistical quantities to be computed and printed.
  </DD>
  </DL>
  <DL>
  <DT><B>lower = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lower' Line='lower = INDEF'>
  <DD>Use only pixels with values greater than or equal to this limit.
  All pixels are above the default value of INDEF.
  </DD>
  </DL>
  <DL>
  <DT><B>upper = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='upper' Line='upper = INDEF'>
  <DD>Use only pixels with values less than or equal to this limit.
  All pixels are below the default value of INDEF.
  </DD>
  </DL>
  <DL>
  <DT><B>binwidth = 0.1</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='binwidth' Line='binwidth = 0.1'>
  <DD>The width of the histogram bins used for computing the midpoint (estimate
  of the median) and the mode.
  The units are in sigma.
  </DD>
  </DL>
  <DL>
  <DT><B>format = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='format' Line='format = yes'>
  <DD>Label the output columns and print the result in fixed format. If format
  is "<TT>no</TT>" no column labels are printed and the output is in free format.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The statistical quantities specified by the parameter <I>fields</I> are
  computed and printed for each image in the list specified by <I>images</I>.
  The results are printed in tabular form with the fields listed in the order
  they are specified in the fields parameter. The available fields are the
  following.
  <P>
  <PRE>
  	 image - the image name
  	  npix - the number of pixels used to do the statistics
  	  mean - the mean of the pixel distribution
  	 midpt - estimate of the median of the pixel distribution
  	  mode - the mode of the pixel distribution
  	stddev - the standard deviation of the pixel distribution
  	  skew - the skew of the pixel distribution
        kurtosis - the kurtosis of the pixel distribution
  	   min - the minimum pixel value
  	   max - the maximum pixel value
  </PRE>
  <P>
  The mean, standard deviation, skew, kurtosis, min and max are computed in a
  single pass through the image using the expressions listed below.
  Only the quantities selected by the fields parameter are actually computed.
  <P>
  <PRE>
            mean = sum (x1,...,xN) / N
  	     y = x - mean
        variance = sum (y1 ** 2,...,yN ** 2) / (N-1)
          stddev = sqrt (variance)
            skew = sum ((y1 / stddev) ** 3,...,(yN / stddev) ** 3) / (N-1)
        kurtosis = sum ((y1 / stddev) ** 4,...,(yN / stddev) ** 4) / (N-1) - 3
  </PRE>
  <P>
  The midpoint and mode are computed in two passes through the image. In the
  first pass the standard deviation of the pixels is calculated and used
  with the <I>binwidth</I> parameter to compute the resolution of the data
  histogram. The midpoint is estimated by integrating the histogram and
  computing by interpolation the data value at which exactly half the
  pixels are below that data value and half are above it. The mode is
  computed by locating the maximum of the data histogram and fitting the
  peak by parabolic interpolation.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. To find the number of pixels, mean, standard deviation and the minimum
  and maximum pixel value of a bias region in an image.
  <P>
  <PRE>
      cl&gt; oimstat flat*[*,1]
      #      IMAGE      NPIX      MEAN    STDDEV       MIN       MAX
        flat1[*,1]       800     999.5     14.09      941.     1062.
        flat2[*,1]       800     999.4     28.87      918.     1413.
  </PRE>
  <P>
  The string "<TT>flat*</TT>" uses a wildcard to select all images beginning with the
  word flat.  The string "<TT>[*,1]</TT>" is an image section selecting row 1.
  <P>
  2. Compute the mean, midpoint, mode and standard deviation of a pixel
  distribution.
  <P>
  <PRE>
      cl&gt; oimstat m51 fields="image,mean,midpt,mode,stddev"
      #      IMAGE    PIXELS      MEAN     MIDPT     MODE     STDDEV
  	     M51    262144     108.3     88.75    49.4       131.3
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  When using a very large number of pixels the accumulation of the sums
  of the pixel values to the various powers may
  encounter roundoff error.  This is significant when the true standard
  deviation is small compared to the mean.
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE	' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
