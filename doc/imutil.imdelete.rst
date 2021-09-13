.. _imdelete:

imdelete — Delete a list of images
==================================

**Package: imutil**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  imdelete -- delete a list of images
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  imdelete images
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>images</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='images' Line='images'>
  <DD>List of images to be deleted.
  </DD>
  </DL>
  <DL>
  <DT><B>go_ahead </B></DT>
  <! Sec='PARAMETERS' Level=0 Label='go_ahead' Line='go_ahead '>
  <DD>Delete the image?
  </DD>
  </DL>
  <DL>
  <DT><B>verify = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verify' Line='verify = no'>
  <DD>Verify the delete operation for each image.
  </DD>
  </DL>
  <DL>
  <DT><B>default_action = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='default_action' Line='default_action = yes'>
  <DD>The default action for the verify query.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
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
  <H3>Examples</H3>
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
  <H3>Time requirements</H3>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  </UL>
  <! EndSection:   'TIME REQUIREMENTS'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  imcopy, fcache
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
