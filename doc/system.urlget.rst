urlget — Get a (http) URL to a named file
=========================================

**Package: system**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>urlget (Sep2011)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>system</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>urlget (Sep2011)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>urlget</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  urlget -- Get a (http) URL to the named file
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  urlget url fname
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_url">url</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='url' Line='url'>
  <DD>The URL to download.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_fname">fname</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fname' Line='fname'>
  <DD>The name of the file to create containing the URL contents.  If not
  specified, the trailing part of the URL is used as the filename.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_use_cache">use_cache = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='use_cache' Line='use_cache = yes'>
  <DD>Use the system file cache?  If 'yes' and the file already exists in the
  cache, the cached file will be copied to the output filename.
  If 'no' then the URL will be downloaded again.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_extn">extn = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='extn' Line='extn = ""'>
  <DD>Optional filename extension to put on the cached filename.  This can be
  used to force files to be saved as a particular type in the cache.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_verbose">verbose = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = no'>
  <DD>Print verbose output?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_cache">cache = "<TT>cache$</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='cache' Line='cache = "cache$"'>
  <DD>Logical cache directory name.
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The <I>URLGET</I> task is used to download a URL (HTTP protocol only) to a 
  local file named by the <I>fname</I> parameter.  If no <I>fname</I> is given, 
  a filename is constructed from the last part of the URL (i.e.
  characters trailing any of the <TT>'?'</TT>, <TT>'/'</TT>, or <TT>'&'</TT> delimiters).  Because 
  the URL may not point to a static file, use of the <I>fname</I> parameter
  is recommended.
  <P>
  If the <I>use_cache</I> parameter is set, the URL will only be downloaded if
  it does not already exist in the file cache pointed to by the <I>cache</I>
  parameter, otherwise the cached file will be copied to the output filename.
  The <I>extn</I> parameter may be to used to force a specific file extension
  to be appended to the filename in the cache, this allows a URL to be passed
  to a task and treated as if it were a file of a specific type.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Download a FITS image from a URL (these are equivalent):
  <P>
  <PRE>
      cl&gt; urlget http://iraf.noao.edu/foo.fits 
      cl&gt; urlget http://iraf.noao.edu/foo.fits foo.fits
  </PRE>
  <P>
  2. Force a URL to be downloaded again:
  <PRE>
      cl&gt; urlget http://iraf.noao.edu/foo.fits use_cache=no
  </PRE>
  <P>
  3. Download a URL with special characters:
  <PRE>
      cl&gt; urlget http://iraf.noao.edu/scripts/tget?f=foo.fits
  or
      cl&gt; s1 = "http://iraf.noao.edu/scripts/tget?f=foo.fits"
      cl&gt; urlget(s1)
  or
      cl&gt; s1 = "http://iraf.noao.edu/scripts/tget?f=foo.fits&amp;d=/iraf/web"
      cl&gt; urlget(s1,"foo.fits",verbose+)
  </PRE>
  <P>
  Escaping special characters isn't required from the commandline since the
  URL is assumed to be whitespace or comma delimited.
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  <P>
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  <P>
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>