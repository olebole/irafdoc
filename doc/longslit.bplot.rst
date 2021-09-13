bplot — Batch plots of spectra
==============================

**Package: longslit**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>bplot (Mar92)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.onedspec</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>bplot (Mar92)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>bplot</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  bplot -- Plot spectra noninteractively using SPLOT
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  bplot images [records]
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_images">images</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='images' Line='images'>
  <DD>List of images to be plotted.  These may be one dimensional, multiaperture,
  long slit, or nonspectral images.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_records">records (imred.irs and imred.iids only)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='records' Line='records (imred.irs and imred.iids only)'>
  <DD>List of records to be appended to the input image root names when
  using record number extension format.  The syntax of this list is comma
  separated record numbers or ranges of record numbers.  A range consists of
  two numbers separated by a hyphen.  A null list may be used if no record
  number extensions are desired.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_apertures">apertures = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='apertures' Line='apertures = ""'>
  <DD>List of apertures/lines/columns to be plotted in each image.  If
  <I>apertures</I> is null all of the apertures/lines/columns will be plotted.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_band">band = 1</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='band' Line='band = 1'>
  <DD>The band or plane of a three dimensional image to be plotted in each image.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_graphics">graphics = "<TT>stdgraph</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='graphics' Line='graphics = "stdgraph"'>
  <DD>Output graphics device.  This may be one of "<TT>stdgraph</TT>", "<TT>stdplot</TT>",
  "<TT>stdvdm</TT>", or the actual device name.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_cursor">cursor = "<TT>onedspec$gcurval.dat</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='cursor' Line='cursor = "onedspec$gcurval.dat"'>
  <DD>File(s) containing cursor commands for the SPLOT task.
  The files will be cycled sequentially.  If there is more than one file
  usually the number of files will agree with the number of apertures
  for each image since otherwise different cursor/aperture pairings will
  occur.  The default is a file containing only the (q)uit command.
  </DD>
  </DL>
  <P>
  The following parameters are used in response to particular keystrokes.
  In <B>splot</B> they are query parameters but in <B>bplot</B> they are hidden
  parameters.
  <DL>
  <DT><B><A NAME="l_next_image">next_image = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='next_image' Line='next_image = ""'>
  <DD>In response to <TT>'g'</TT> (get next image) this parameter specifies the image.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_new_image">new_image = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='new_image' Line='new_image = ""'>
  <DD>In response to <TT>'i'</TT> (write current spectrum) this parameter specifies the
  name of a new image to create or existing image to overwrite.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_overwrite">overwrite = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='overwrite' Line='overwrite = yes'>
  <DD>Overwrite an existing output image?  If set to yes it is possible to write
  back into the input spectrum or to some other existing image.  Otherwise
  the user is queried again for a new image name.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_spec2">spec2 = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='spec2' Line='spec2 = ""'>
  <DD>When adding, subtracting, multiplying, or dividing by a second spectrum
  (<TT>'+'</TT>, <TT>'-'</TT>, <TT>'*'</TT>, <TT>'/'</TT> keys in the <TT>'f'</TT> mode) this parameter is used to get
  the name of the second spectrum.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_constant">constant = 0.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='constant' Line='constant = 0.'>
  <DD>When adding or multiplying by a constant (<TT>'p'</TT> or <TT>'m'</TT> keys in the <TT>'f'</TT> mode)
  the parameter is used to get the constant.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_wavelength">wavelength = 0.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='wavelength' Line='wavelength = 0.'>
  <DD>This parameter is used to get a dispersion coordinate value during deblending or
  when changing the dispersion coordinates with <TT>'u'</TT>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_linelist">linelist = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='linelist' Line='linelist = ""'>
  <DD>During deblending this parameter is used to get a list of line positions
  and widths.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_wstart">wstart = 0., wend = 0., dw = 0.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='wstart' Line='wstart = 0., wend = 0., dw = 0.'>
  <DD>In response to <TT>'p'</TT> (convert to a linear wavelength scale) these parameter
  specify the starting wavelength, ending wavelength, and wavelength per pixel.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_boxsize">boxsize = 2</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='boxsize' Line='boxsize = 2'>
  <DD>In response to <TT>'s'</TT> (smooth) this parameter specifies the box size in pixels
  to be used for the boxcar smooth
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The spectra in the input image list are successively processed by the task
  <B>splot</B> with input supplied by the cursor parameter and the output sent
  to the specified graphics device.  The range of apertures and bands
  specified by <I>apertures</I> and <I>bands</I> will be processed for each
  image.  In the <B>iids/irs</B> packages the record extension syntax is used
  with input root names and a record number list.  The hidden parameters from
  <B>splot</B> apply to this task.
  <P>
  The cursor file(s) consists of line(s) of the form:
  <P>
  	[x y 1] key [command]
  <P>
  where x and y are the position of the cursor (may be zero or absent if the
  cursor position is irrelevant) and key is one of the keystrokes understood
  by <B>splot</B>.  If the key is "<TT>:</TT>" then the <I>colon</I> command string follows.
  The default cursor file consists of the single line:
  <P>
  	0 0 1 q
  <P>
  If more than one cursor file is specified they are sequentially assigned to
  each aperture and the list is repeated as needed.  This allows the aperture
  to be manipulated in differing ways.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. To plot all of apertures of the multiaperture spectra indicated by the file
  "<TT>nite1.lst</TT>" on the default plotter and run in the background:
  <P>
  <PRE>
      cl&gt; bplot @nite1.lst graphics=stdplot &amp;
  </PRE>
  <P>
  2. To preview the plots:
  <P>
  <PRE>
      cl&gt; bplot @nite1.lst graphics=stdgraph
  </PRE>
  <P>
  3.  To produce a histogram type plot about Balmer alpha for aperture 5 of
  each spectrum with the IRAF banner suppressed:
  <P>
  <PRE>
      cl&gt; type curfile
      6555 0 1 a
      6570 0 1 a
      q
      cl&gt; splot.options="auto hist nosysid"
      cl&gt; splot.xmin=6555
      cl&gt; splot.xmax=6570
      cl&gt; bplot @nite1.lst apertures=5 cursor=curfile
  </PRE>
  <P>
  4. To produce plots with four spectra per page:
  <P>
  <PRE>
      cl&gt; bplot @nite1.lst ... &gt;G nite1.mc
      cl&gt; gkimosaic nite1.mc dev=stdplot
  </PRE>
  <P>
  The first command redirects the output of the graphics to the metacode
  file nite1.mc.  The task <B>gkimosaic</B> is used to make multiple plots
  per page.  Other tasks in the <B>plot</B> package may be used to
  manipulate and redisplay the contents of the metacode file.
  <P>
  5. To plot a list of apertures with a different cursor file for each aperture:
  <P>
  <PRE>
      cl&gt; bplot @nite1.lst apertures=3,9,14 cursor=@nite1.cur
  </PRE>
  <P>
  In this case the file "<TT>nite1.cur</TT>" is assumed to be a list of
  individual cursor file names, for instance:
  <P>
  <PRE>
  	cur.03
  	cur.09
  	cur.14
  </PRE>
  <P>
  that are in one to one correspondence with the range of apertures.
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_revisions">REVISIONS</A></H2>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_BPLOT">BPLOT V2.10.3</A></B></DT>
  <! Sec='REVISIONS' Level=0 Label='BPLOT' Line='BPLOT V2.10.3'>
  <DD>The query parameters from SPLOT were added as hidden parameters in BPLOT
  to allow use of those keys in a batch way.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_BPLOT">BPLOT V2.10</A></B></DT>
  <! Sec='REVISIONS' Level=0 Label='BPLOT' Line='BPLOT V2.10'>
  <DD>The <I>apertures</I> and <I>band</I> parameters been added to select
  apertures from multiple spectra and long slit images, and bands from 3D
  images.  Since the task is a script calling <B>splot</B>, the many revisions
  to that task also apply.  The version in the <B>irs/iids</B> packages
  selects spectra using the record number extension syntax.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'REVISIONS'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  The cursor file command keystrokes cannot include any of the cursor
  mode (CAPITALIZED) keys.  This results from the implementation of
  the cursor mode commands as external to both BPLOT and SPLOT.
  <P>
  When first entered, SPLOT will always display an initial plot.  BPLOT
  calls SPLOT once for each aperture in each image and thus produces
  N(apertures)*N(images) initial plots.  The plots are not optional because
  of the possible confusion a blank screen might cause an inexperienced
  user.  If the initial plots are unwanted they must be edited out of the
  graphics stream.  This can be done as follows, by directing the
  graphics output of BPLOT to a metacode file and then using GKIEXTRACT
  to remove only the desired plots from the metacode file:
  <P>
  <PRE>
      cl&gt; bplot @nite1.lst cursor=curfile &gt;G nite1.mc
      cl&gt; gkiextract nite1.mc 2x2 | gkimosaic dev=stdplot
  </PRE>
  <P>
  This assumes that curfile is designed to produce only one plot in
  addition to the non-optional initial plot.  In this case there will be
  two plots per aperture per image and we extract every other plot starting
  with the second (as encoded in the range string:  "<TT>2x2</TT>").
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  splot, specplot, slist, gkiextract, gkimosaic, implot, graph, ranges
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'REVISIONS' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>