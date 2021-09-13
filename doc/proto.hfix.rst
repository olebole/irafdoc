.. _hfix:

hfix — Fix image headers with a user specified command
======================================================

**Package: proto**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  hfix -- fix image headers with a user specified command
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  hfix images
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>images</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='images' Line='images'>
  <DD>List of images whose headers are to be fixed.  If <I>update</I> is yes then
  the user must have write permission on the image headers.
  </DD>
  </DL>
  <DL>
  <DT><B>command = "<TT>edit $fname</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='command' Line='command = "edit $fname"'>
  <DD>Command to be applied to a file containing the image header.  The command
  may be any CL command which includes escapes to host commands.  The file
  containing the header in text form is specified by the special string
  "<TT>$fname</TT>".  The command should modify this file to the desired form.  The
  default is to invoke a text editor but there are many other possibilities.
  The image name may also be specified with "<TT>$image</TT>".  See the EXAMPLES
  section for some ideas.
  </DD>
  </DL>
  <DL>
  <DT><B>update = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='update' Line='update = yes'>
  <DD>Update the image header with the modified header.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  This task allows you to extract the image headers into a text file,
  modify this file with a specified command, and update the image header
  with the modified file.  The command to be applied is specified with
  the <I>command</I> parameter.  In this command the text file containing
  the header to be acted upon is referenced with the string "<TT>$fname</TT>".
  If it is desired to update the image header with the modified file
  the <I>update</I> switch must be set.  You must have write permission
  to update the image headers.
  <P>
  A common command, which is the default, is to use a text editor.
  Other possibilities are to save the file, use a non-interactive host
  command such as <B>sed</B> in UNIX, or write your own program or
  script.
  <P>
  This task does very little processing on the header after you are finished
  editing.  It checks for legal FITS characters in the first 8 columns and if
  there is an <TT>'='</TT> in column 9 then there must be a <TT>' '</TT> (blank) in column 10.
  Lines violating these checks are skipped.  It also sets each line in the
  header to the correct length.  Because you have total freedom to change the
  header parameters while in the text editor, you must make sure that the
  header has a legal format after you are through editing it. In particular,
  be sure each field in the header parameters that you add or change begin in
  the proper columns.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Edit the header of the image test.imh:
  <P>
  <PRE>
  	cl&gt; hfix test.imh
  	&lt;Edit the header text&gt;
  </PRE>
  <P>
  2. Get the header of a single image and save the file:
  <P>
  <PRE>
  	cl&gt; hfix myim command="copy $fname save" update-
  </PRE>
  <P>
  3. A image header was created with an incorrect format such that the
  equal sign is in column 10 instead of 9:
  <P>
  <PRE>
  	cl&gt; hfix *.imh \<BR>
  	&gt;&gt;&gt; command="!sed 's/ =/=/' $fname &gt;temp;mv temp $fname"
  </PRE>
  <P>
  Note that this example should not be tried on a valid header where the
  equal sign is in column 9.
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  images.hedit noao.artdata.mkheader
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
