.. _sections:

sections — Expand an image template on the standard output
==========================================================

**Package: imutil**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  sections -- expand an image template
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  sections images
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>images</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='images' Line='images'>
  <DD>Image template or list of images.  There is no check that the names are
  images and any name may be used.  The thing which distinguishes an image
  template from a file template is that the special characters <TT>'['</TT> and
  <TT>']'</TT> are interpreted as image sections rather than a character class
  wildcard unless preceded by the escape character <TT>'!'</TT>.  To explicitly
  limit a wildcard template to images one should use an appropriate
  extension such as "<TT>.imh</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>option = "<TT>fullname</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='option' Line='option = "fullname"'>
  <DD>The options are:
  <DL>
  <DT><B>"<TT>nolist</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='' Line='"nolist"'>
  <DD>Do not print list.
  </DD>
  </DL>
  <DL>
  <DT><B>"<TT>fullname</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='' Line='"fullname"'>
  <DD>Print the full image name for each image in the template.
  </DD>
  </DL>
  <DL>
  <DT><B>"<TT>root</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='' Line='"root"'>
  <DD>Print the root name for each image in the template.
  </DD>
  </DL>
  <DL>
  <DT><B>"<TT>section</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='' Line='"section"'>
  <DD>Print the section for each image in the template.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B>nimages</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nimages' Line='nimages'>
  <DD>The number of images in the image template.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The image template list <I>images</I> is expanded and the images are printed
  one per line on the standard output unless the "<TT>nolist</TT>" option is given.
  Other options allow selection of a portion of the image name.  The number
  of images in the list is determined and stored in the parameter <I>nimages</I>.
  <P>
  This task is used for several purposes:
  <DL>
  <DT><B>(1)</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line='(1)'>
  <DD>To verify that an image template is expanded as the user desires.
  </DD>
  </DL>
  <DL>
  <DT><B>(2)</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line='(2)'>
  <DD>To create a file of image names which include image sections.
  </DD>
  </DL>
  <DL>
  <DT><B>(3)</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line='(3)'>
  <DD>To create a file of new image names using the concatenation feature of the
  image templates.
  </DD>
  </DL>
  <DL>
  <DT><B>(4)</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line='(4)'>
  <DD>To determine the number of images specified by the user in a command language
  script.
  </DD>
  </DL>
  <P>
  There is no check that the names are images and any name may be used.
  The thing which distinguishes an <I>image template</I> from a <I>file
  template</I> is that the special characters <TT>'['</TT> and <TT>']'</TT> are interpreted
  as image sections rather than a character class wildcard unless
  preceded by the escape character <TT>'!'</TT>.  To explicitly limit a wildcard
  template to images one should use an appropriate extension such as "<TT>.imh</TT>".
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Calculate and print the number of images in a template:
  <P>
  <PRE>
  	cl&gt; sections fits*.imh opti=no
  	cl&gt; = sections.nimages
  	cl&gt; 7
  </PRE>
  <P>
  2. Expand an image template:
  <P>
  <PRE>
  	cl&gt; sections fits*![3-9].imh[1:10,*]
  	fits003.imh[1:10,*]
  	fits004.imh[1:10,*]
  	&lt;etc.&gt;
  </PRE>
  <P>
  Note the use of the character class escape, image section appending,
  and explicit use of the .imh extension.
  <P>
  3. Create a new list of image names by adding the suffix "<TT>new</TT>":
  <P>
  <PRE>
  	cl&gt; sections jan18???//new
  	jan18001new
  	jan18002new
  	&lt;etc.&gt;
  </PRE>
  <P>
  Note the use of the append syntax.  Also there is no guarantee that the
  files are actually images.
  <P>
  4. Subtract two sets of images:
  	
  <PRE>
  	cl&gt; sections objs*.imh[100:200,300:400] &gt; objslist
  	cl&gt; sections skys*.imh[100:200,300:400] &gt; skyslist
  	cl&gt; sections %objs%bck%* &gt; bcklist
  	cl&gt; imarith @objslist - @skyslist @bcklist
  </PRE>
  <P>
  Note the use of the substitution syntax.
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
  The  image list is not sorted.           
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  files
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
