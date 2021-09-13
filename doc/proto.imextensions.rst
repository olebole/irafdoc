.. _imextensions:

imextensions — Make a list of image extensions
==============================================

**Package: proto**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  imextensions -- make a list of image extensions
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage   </H3>
  <! BeginSection: 'USAGE   '>
  <UL>
  <PRE>
  imextensions input
  </PRE>
  </UL>
  <! EndSection:   'USAGE   '>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>List of input files containing image extensions to be listed.  This list
  may not contain any image kernel but it can contain an image section.  The
  image filename extension, such as "<TT>.fits</TT>", is optional in the same way as
  with other IRAF image tasks.
  </DD>
  </DL>
  <DL>
  <DT><B>output = "<TT>file</TT>" (none|list|file)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output = "file" (none|list|file)'>
  <DD>Output type for the list of image extensions.  The choices are:
  <P>
  <PRE>
      none - no output
      list - a list as a single line
      file - a list of one image extension per line
  </PRE>
  <P>
  The "<TT>none</TT>" output is used to just set the number of image extensions in the
  <I>nimages</I> parameter.  The "<TT>list</TT>" output is used for a short list that
  can be scanned into a CL variable.  The "<TT>file</TT>" output is used for a long
  list and to be redirected to a file for use as an "<TT>@file</TT>".  If "<TT>list</TT>"
  output is selected and the list length exceeds 255 characters (the
  size of a CL string) the task will abort with an error.
  </DD>
  </DL>
  <DL>
  <DT><B>index = "<TT>1-</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='index' Line='index = "1-"'>
  <DD>Extension index range list.  The range list syntax is specified under the
  help topic <B>ranges</B>.  Note that the range list may be specified that
  includes 0 to select the primary image header in FITS files.
  </DD>
  </DL>
  <DL>
  <DT><B>extname = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='extname' Line='extname = ""'>
  <DD>Extension name pattern.  If a null string is specified then there is
  no check on the extension name.  If a pattern is specified then only
  image extensions with an extension name matching the pattern will be
  selected.  The pattern syntax is described under the help topic <I>match</I>.
  </DD>
  </DL>
  <DL>
  <DT><B>extver = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='extver' Line='extver = ""'>
  <DD>Extension version range list.  If a null list is specified then there is
  no check on the extension version.  If a list is given then only image
  extensions with extension versions in the list will be selected.
  The range list syntax is described under the help topic <B>ranges</B>.
  </DD>
  </DL>
  <DL>
  <DT><B>lindex = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lindex' Line='lindex = yes'>
  <DD>List the image extensions with the extension index?  If the value is
  "<TT>no</TT>" then the extension index will not be listed if the extension
  name and/or the extension version is listed.  If there is no
  extension name or extension version then the extension index is
  always listed regardless of the value of this parameter.
  </DD>
  </DL>
  <DL>
  <DT><B>lname = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lname' Line='lname = no'>
  <DD>List the image extensions with the extension name if there is one?
  </DD>
  </DL>
  <DL>
  <DT><B>lver = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lver' Line='lver = no'>
  <DD>List the image extensions with the extension version if there is one?
  </DD>
  </DL>
  <DL>
  <DT><B>ikparams = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ikparams' Line='ikparams = ""'>
  <DD>Include the specified image kernel parameters in the image extension
  names.  The image kernel parameters are specific to the various
  IRAF image formats.
  </DD>
  </DL>
  <P>
  <DL>
  <DT><B>nimages</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nimages' Line='nimages'>
  <DD>This is an output parameter which is set to the number of image extensions
  selected in the last execution of the task.  Note that if the task
  is run as a background job this parameter will not be set in the
  disk parameter file though it can be made available in a background
  script using this task by caching the parameter set; i.e. 
  include the command "<TT>cache imextensions</TT>" at the beginning of the script.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <B>Imextensions</B> selects and lists image extensions in files.  Image
  extensions currently occur in multi-extension FITS files and multi-group
  Geiss (STF format) files.  The image extension names are given in proper
  syntax for IRAF image names for use in tasks expecting image names.
  The output format type may be a one line list, a list of one image
  extension name per line, or no output.  These options allow capturing
  the expanded list in a CL string variable, in a file for use as
  an "<TT>@file</TT>", or to simply count the number of image extensions matching
  the selection criteria.  Note that if the "<TT>list</TT>" output type is selected
  and the list of image extensions exceeds 255 characters (the limit
  for a CL string) then the task aborts with an error.
  <P>
  Image extensions may be selected by index value (the position in the file),
  by extension name (keyword EXTNAME used in FITS image extensions), and by
  extension version number (keyword EXTVER).  The numeric selection uses
  range lists and the extension name selection uses pattern matching.  The
  primary image in a multi-extension FITS file may also be selected by
  including an index value of 0 in the index range list.
  <P>
  The output image extension names may be given with the index value and/or
  the image kernel specification.  The image kernel specification, which is
  image type dependent, may include the extension name, extension version,
  and other kernel parameters.  Note that if the image does not have an
  extension name or version then the index value is always given whether or
  not the <I>lindex</I> parameter is set to insure that a proper image name is
  generated.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1.  Get a list of image extensions in a CL string and use it to select
  header keywords.  This illustrates the use of the "<TT>list</TT>" output and
  a CL variable.
  <P>
  <PRE>
      cl&gt; imext obj001 output=list | scan (s1)
      cl&gt; = s1
      obj001[1],obj001[2],obj001[3]
      cl&gt; if (imext.nimages &gt; 0)
      &gt;&gt;&gt; hselect (s1, "$I,title", yes)
      obj001[1]   Alpha Leo
      obj001[2]   Beta Leo
      obj001[3]   Gamma Leo
  </PRE>
  <P>
  2.  Do the same thing as in the first example using an "<TT>@file</TT>".
  <P>
  <PRE>
      cl&gt; imext obj001 output=file &gt; list.dat
      cl&gt; type list.dat
      obj001[1]
      obj001[2]
      obj001[3]
      cl&gt; if (imext.nimages &gt; 0)
      &gt;&gt;&gt; hselect @list.dat $I,title yes
      obj001[1]   Alpha Leo
      obj001[2]   Beta Leo
      obj001[3]   Gamma Leo
  </PRE>
  <P>
  3.  Create a list selecting only the first and third extension and using the
  image extension name, version, and an image kernel section.
  <P>
  <PRE>
      cl&gt; imext obj*[1:100,1:100] index=1,3 lindex- lname+ lver+ ikparams=expand
      obj001.fits[aleo,1,expand][1:100,1:100]
      obj003.fits[gleo,1,expand][1:100,1:100]
      obj002.fits[im1,1,expand][1:100,1:100]
      obj002.fits[im3,1,expand][1:100,1:100]
      cl&gt; = imext.nimages
      4
  </PRE>
  <P>
  4.  List only the primary images in a set of multi-extension FITS files.
  A primary image need not contain image data; i.e. this will select
  global headers with NDIM=0 as well as headers with image data.
  <P>
  <PRE>
      cl&gt; imext *.fits index=0
      abc.fits[0]
      def.fits[0]
      ghi.fits[0]
  </PRE>
  <P>
  5.  Use this task in a script to test on the existence of extension name
  "<TT>joy</TT>".  This example shows the use of the pattern matching and of the
  <B>cache</B> command to insure the script works as a background task.
  <P>
  <PRE>
      procedure example (image)
  <P>
      file    image   {prompt="Image"}
  <P>
      begin
  	    file    im
  <P>
  	    cache imextensions
  	    im = image
  <P>
  	    imextensions (im, output="none", extname="joy")
  	    if (imextensions.nimages == 0)
  		call printf ("No joy found with %s\n", im) 
      end
  </PRE>
  <P>
  Note that proper script programming would make all the hidden parameters
  explicit.
  <P>
  <P>
  6.  Example of the extension name pattern matching.
  <P>
  <PRE>
      cl&gt; imext obj.fits extname=joy lindex- lname+
      obj.fits[joy]
      obj.fits[nojoy]
      obj.fits[joyfull]
      cl&gt; imext obj.fits extname="^joy$" lindex- lname+
      obj.fits[joy]
      cl&gt; imext obj.fits extname="{joy}$" lindex- lname+
      obj.fits[joy]
      obj.fits[Joy]
      obj.fits[nojoy]
  </PRE>
  <P>
  The first example matches "<TT>joy</TT>" anywhere in the extension name, the
  second requires an exact match with the begin and end string characters,
  and the last example ignores the case and requires the name end with
  joy.
  <P>
  7.  An example with a Geiss file.
  <P>
  <PRE>
      cl&gt; imext y00vk102r.d0h index="x5"
      y00vk102r.d0h[1]
      y00vk102r.d0h[6]
      y00vk102r.d0h[11]
      y00vk102r.d0h[16]
      y00vk102r.d0h[21]
      y00vk102r.d0h[26]
      y00vk102r.d0h[31]
      y00vk102r.d0h[36]
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Revisions</H3>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B>IMEXTENSIONS V2.11.?</B></DT>
  <! Sec='REVISIONS' Level=0 Label='IMEXTENSIONS' Line='IMEXTENSIONS V2.11.?'>
  <DD>Image sections are now allowed in the input names.
  </DD>
  </DL>
  <DL>
  <DT><B>IMEXTENSIONS V2.11</B></DT>
  <! Sec='REVISIONS' Level=0 Label='IMEXTENSIONS' Line='IMEXTENSIONS V2.11'>
  <DD>This task is new in this release.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'REVISIONS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  <PRE>
  files, sections, ranges, match
  </PRE>
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE   ' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'REVISIONS' 'SEE ALSO'  >
  
