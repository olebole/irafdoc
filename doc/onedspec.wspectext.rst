wspectext — Convert 1D image spectra to ascii text spectra
==========================================================

**Package: onedspec**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>wspectext (Oct93)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>onedspec</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>wspectext (Oct93)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>wspectext</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  wspectext -- convert 1D image spectra to an ascii text spectra
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  wspectext input output
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>Input list of 1D image spectra to be converted.  If the image is
  not one dimensional an warning will be given and the image will be skipped.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_output">output</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>Output list of ascii text spectra filenames.  The list must match the
  input list.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_header">header = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='header' Line='header = yes'>
  <DD>This parameter determines whether or not a descriptive header precedes the
  wavelength and flux values written to the text file.  When <I>header =
  no</I>, only a two column list of wavelengths and fluxes is output.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_wformat">wformat = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='wformat' Line='wformat = ""'>
  <DD>The wavelength coordinate output format.  If it is undefined the formatting
  option stored with the WCS in the image header is used.  If the WCS
  formatting option is not defined then a free format is used.  See
  <B>listpixels</B> for a description of the format syntax.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  IRAF one dimensional spectra are converted to ascii text files.  The
  text files consist of an optional FITS type header followed by a two
  column list of wavelengths and flux values.  The format of the wavelengths
  can be set but the flux values are given in free format.  This task
  is a combination of <B>wtextimage</B> and <B>listpixels</B>.  The output
  of this task may be converted back to an image spectrum with the
  task <B>rspectext</B>.
  <P>
  Spectra which are not in 1D images such as multispec format or long slit
  may first be converted to 1D images using <B>scopy</B> with format="<TT>onedspec</TT>".
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1.  Write a text file with a header.
  <P>
  <PRE>
      cl&gt; wspectext spec001 text001 header+ wformat="%0.2f"
      cl&gt; type text001
      BITPIX  =                    8  /  8-bit ASCII characters
      NAXIS   =                    1  /  Number of Image Dimensions
      NAXIS1  =                  100  /  Length of axis
      ORIGIN  = 'NOAO-IRAF: WTEXTIMAGE'  /
      IRAF-MAX=                   0.  /  Max image pixel (out of date)
      IRAF-MIN=                   0.  /  Min image pixel (out of date)
      IRAF-B/P=                   32  /  Image bits per pixel
      IRAFTYPE= 'REAL FLOATING     '  /  Image datatype
      OBJECT  = 'TITLE             '  /
      FILENAME= 'TEST              '  /  IRAF filename
      FORMAT  = '5G14.7            '  /  Text line format
      APNUM1  = '1 1     '
      DC-FLAG =                    0
      WCSDIM  =                    1
      CTYPE1  = 'LINEAR  '
      CRVAL1  =                4000.
      CRPIX1  =                   1.
      CDELT1  =     10.1010101010101
      CD1_1   =     10.1010101010101
      LTM1_1  =                   1.
      WAT0_001= 'system=equispec                                 '
      WAT1_001= 'wtype=linear label=Wavelength units=Angstroms   '
      END
  										    
      4000.00  1000.
      4010.10  1005.54
      4020.20  1011.05
      ...
  </PRE>
  <P>
  2.  Write a simple text file with two columns of wavelength and flux.
  <P>
  <PRE>
      cl&gt; wspectext spec001 text002 header- wformat="%0.2f"
      cl&gt; type text002
      4000.00  1000.
      4010.10  1005.54
      4020.20  1011.05
      ...
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_revisions">REVISIONS</A></H2>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_WSPECTEXT">WSPECTEXT V2.10.3</A></B></DT>
  <! Sec='REVISIONS' Level=0 Label='WSPECTEXT' Line='WSPECTEXT V2.10.3'>
  <DD>This is a new task with this version.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'REVISIONS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  rspectext, wtextimage, listpixels, scopy, imspec
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'REVISIONS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>