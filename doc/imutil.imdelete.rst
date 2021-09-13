imdelete — Delete a list of images
==================================

**Package: imutil**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>imdelete (Dec85)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>images.imutil</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>imdelete (Dec85)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>imdelete</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  imdelete -- delete a list of images
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  imdelete images
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_images">images</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='images' Line='images'>
  <DD>List of images to be deleted.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_go_ahead">go_ahead </A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='go_ahead' Line='go_ahead '>
  <DD>Delete the image?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_verify">verify = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verify' Line='verify = no'>
  <DD>Verify the delete operation for each image.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_default_action">default_action = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='default_action' Line='default_action = yes'>
  <DD>The default action for the verify query.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  IMDELETE takes as input a list of IRAF images specified by <I>images</I> and
  deletes both the header and pixel files. In <I>verify</I> mode IMDELETE
  queries the user for the appropriate action to be taken for each IRAF image.
  <P>
  If the <I>images</I> parameter is a URL, it will be accessed and put into 
  the file cache, then immediately deleted.  To simply remove a file from
  the cache, use the <I>fcache</I> command instead.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Delete a list of images
  <P>
  <PRE>
      cl&gt; imdelete fits*
  </PRE>
  <P>
  2. Delete a list of images using verify
  <P>
  <PRE>
      cl&gt; imdel fits* ver+
      cl&gt; Delete file <I>'fits1'</I> ? (yes): yes
      cl&gt; Delete file <I>'fits2'</I> ? (yes): yes
      cl&gt; Delete file <I>'fits3'</I> ? (yes): yes
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
  imcopy, fcache
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>