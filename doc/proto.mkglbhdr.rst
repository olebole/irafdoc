mkglbhdr — Make global header from keywords in images and reference
===================================================================

**Package: proto**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>mkglbhdr (Feb09)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>proto</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>mkglbhdr (Feb09)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>mkglbhdr</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  mkgblhdr -- make a global header
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  mkgblhdr input output
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>List of input images.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_output">output</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>Output global dataless image.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_reference">reference = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='reference' Line='reference = ""'>
  <DD>Optional reference image defining the allowed keywords, order, and
  blank cards.  If no reference image is specified the first image in
  the input list serves as the reference image.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_exclude">exclude = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='exclude' Line='exclude = ""'>
  <DD>List of keywords to be excluded from the global header even if present
  in the reference header and with common values in all the input images.
  The case of the keywords in the list is ignored and the are matched to
  the headers in uppercase.  Typically the list would be specified as an
  @file; i.e. the contents of a file with keywords on separate lines.
  Note that one may use the output of a header listing without editing
  since only the first eight characters of each line are used.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <B>Mkgblhdr</B> makes a global (dataless) header with keywords common to a
  set of <I>input</I> images.  Common means present in all headers and
  with identical card records (value, formatting, and comments).  The
  purpose of this thask is to allow appending the images using the FITS
  "<TT>inherit</TT>" convention into a multi-extension file.
  <P>
  The set of keywords which are allowed to appear in the global header are
  those in a reference image which are not in the <I>exclude</I> list and
  which have identical card records in all images.  The reference image is
  that specified by the <I>reference</I> parameter.  If the value of that
  parameter is a null string then the first image in the <I>input</I> list
  is used.  The <I>reference</I> image also determines the order of the cards
  including blank cards.
  <P>
  The way the task works is that the header card records are read from
  the reference image.  Keywords in the excluded list are eliminated.
  Then reference card records which are not exactly matched in the input
  headers, independent of position, are eliminated.  Finally any leading
  blank cards are removed and consecutive blank cards are reduced to single
  blank lines.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1.  An initial multi-extension file with inherited global keywords is split
  into separate images.  The headers of the separate images are the union
  of the global and extension headers as is the convention for inheritance.
  After operating on the separate images it is desired to recreate a new
  MEF without having recourse to the original global header.
  <P>
  <PRE>
      cl&gt; type images
      image1
      image2
      cl&gt; mkglbhdr @images newimage
      cl&gt; imcopy image1 newimage[im1,append,inherit]
      cl&gt; imcopy image2 newimage[im2,append,inherit]
  </PRE>
  <P>
  To check the headers separately use the "<TT>noinherit</TT>" flag.
  <P>
  <PRE>
      cl&gt; imhead newimage[0] l+
      cl&gt; imhead newimage[im1,noinherit] l+
  </PRE>
  <P>
  Note that if the global header of the original MEF is available it is
  probably better to use that header instead of <B>mkglbhdr</B> as follows.
  <P>
  <PRE>
      cl&gt; imcopy mefimage[0] newimage
      cl&gt; imcopy image1 newimage[im1,append,inherit]
      cl&gt; imcopy image2 newimage[im2,append,inherit]
  </PRE>
  <P>
  It is important to understand how inheritance works when appending extensions.
  The IRAF FITS "<TT>kernel</TT>" eliminates keywords from the extension header when
  they have the same value as the global header.  If there are common
  keywords but with different values then they are both present and any
  task that read the union of the global and extension headers will see
  the value from the extension.
  <P>
  2. The following example uses an exclusion list.
  <P>
  <PRE>
      cl&gt; type exclude.dat
      CTYPE1
      CTYPE2
      CRVAL1
      CRVAL2
      CRPIX1
      CRPIX2
      CD1_1
      CD1_2
      CD2_1
      CD2_2
      cl&gt; mkglbhdr @images newimage exclude="@exclude.dat"
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  mscsplit, mscjoin
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>