photpars — Edit the aperture photometry parameters
==================================================

**Package: daophot**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>photpars (May00)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.digiphot.daophot</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>photpars (May00)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>photpars</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  photpars -- edit the photometry parameters
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  photpars
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_weighting">weighting = "<TT>constant</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='weighting' Line='weighting = "constant"'>
  <DD>The type of weighting. The weighting is ignored by the PHOT task. The options
  are:
  <DL>
  <DT><B><A NAME="l_constant">constant</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='constant' Line='constant'>
  <DD>Uniform weights of 1 for each pixel are used.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_cone">cone</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='cone' Line='cone'>
  <DD>A conical weighting function of full width half maximum <I>fwhmpsf</I> as
  defined in the DATAPARS parameter set is used.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_gauss">gauss</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='gauss' Line='gauss'>
  <DD>A Gaussian weighting function of full width half maximum <I>fwhmpsf</I> as
  defined in the DATAPARS parameter set is used.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_apertures">apertures = "<TT>3</TT>" (scale units)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='apertures' Line='apertures = "3" (scale units)'>
  <DD>A list of aperture radii in units of the  scale parameter or the name of the
  file containing the list of apertures. List elements may be separated by
  whitespace or commas. A ranges syntax of the form ap1:apN:apstep is also
  supported. 
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_zmag">zmag = 25.00</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='zmag' Line='zmag = 25.00'>
  <DD>The zero point offset for the magnitude scale. 
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_mkapert">mkapert = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='mkapert' Line='mkapert = no'>
  <DD>Mark the photometry apertures on the displayed image?
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  The integral of the flux within the circular apertures specified by
  <I>apertures</I> is computed by summing pixels in the aperture with
  the specified weighting function <I>weighting</I>. The fraction of each pixel
  lying within the aperture is computed by an approximation and all the
  approximations are summed.  The zero point of the magnitude
  scale is determined by <I>zmag</I>.
  <P>
  Apertures is specified in units of the image scale. If <I>scale</I>
  is specified in units of the half-width at half-maximum of the point
  spread function the aperture per pixel  a single value of apertures
  will work well on images with differing psfs.
  <P>
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. List the PHOTPARS parameters.
  <P>
  <PRE>
      da&gt; lpar photpars
  </PRE>
  <P>
  2. Edit the PHOTPARS parameters.
  <P>
  <PRE>
      da&gt; photpars
  </PRE>
  <P>
  3. Edit the PHOTPARS parameters from with the PHOT task.
  <P>
  <PRE>
      da&gt; epar phot
  <P>
  	... edit a few phot parameters
  <P>
  	... move to the photpars parameter and type :e
  <P>
  	... edit the photpars parameters and type :wq
  <P>
  	... finish editing the phot parameters and type :wq
  </PRE>
  <P>
  4. Save the current PHOTPARS parameter set in a text file photnite1.par.
     This can also be done from inside a higher level task as in the above
     example.
  <P>
  <PRE>
      da&gt; photpars
  <P>
  	... type ":w photnite1.par"  from within epar
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
  epar,datapars,centerpars,fitskypars,phot
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>