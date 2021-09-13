.. _mkheader:

mkheader — Append/replace header parameters
===========================================

**Package: artdata**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  mkheader - Append/replace image header
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  mkheader images headers
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>images</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='images' Line='images'>
  <DD>List of images in which header information is to be added or modified.
  </DD>
  </DL>
  <DL>
  <DT><B>header = "<TT>artdata$stdheader.dat</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='header' Line='header = "artdata$stdheader.dat"'>
  <DD>List of images or header keyword data files.  If the list is shorter
  than the input image list then the last entry is repeated.
  If an image is given then the image header
  is copied.  If a file is given then the FITS format cards are copied.
  This only applies to new images.   The data file consists of lines
  in FITS format with leading whitespace ignored.  A FITS card must begin
  with an uppercase/numeric keyword.  Lines not beginning with a FITS
  keyword such as comments or lower case are ignored.  The user keyword
  output of <B>imheader</B> is an acceptable data file.
  </DD>
  </DL>
  <DL>
  <DT><B>append = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='append' Line='append = yes'>
  <DD>Append to existing keywords?  If no then the existing header is replaced.
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = no'>
  <DD>Verbose output?
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The image headers in the list of input images may be replaced or appended
  with information from images or data files specified by the <I>header</I>
  parameter list.  If the header list is shorter than the list of images
  to be modified the last header file is repeated.  Depending on the
  value of the <I>append</I> parameter, new parameters will be appended
  or replace the existing image header parameters.
  <P>
  A header keyword data file consists of lines of FITS format cards.
  Leading whitespace is ignored.  Lines not recognized as FITS cards
  are ignored.  A valid FITS card is defined as beginning with a keyword
  of up to 8 uppercase, digit, hyphen, or underscore characters.  If
  less than 8 characters the remaining characters are blanks.  The
  ninth character may be an equal sign but must be immediately followed
  by a blank.  Such value cards should be in FITS format though no
  attempt is made to enforce this.  Any other ninth character is also
  acceptable and the line will be treated as a comment.  Note that this
  way of recognizing FITS parameters excludes the case of comments
  in which the first 8 characters are blank.  The reason for allowing
  leading whitespace and eliminating the blank keyword case is so that
  the long output of <B>imheader</B> may be used directly as input.
  <P>
  Header files are also used by several of the tasks in the artificial
  data package with a standard default file "<TT>artdata$stdheader.dat</TT>".
  To edit image headers also see <B>hedit</B>.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Add some standard keywords from a file to an image.
  <P>
  <PRE>
      ar&gt; type myheader
      # MY header list
      INSTRUME= 'bspec mark II'		/ B Spectrograph
      LENS    =                  3	/ Lens number
      FOCRATIO=                5.2        / Focal ratio
      ar&gt; mkheader *.imh myheader
  </PRE>
  <P>
  2. Copy an image header.
  <P>
      ar&gt; mkheader new dev$pix append-
  <P>
  3. Edit the image header with a text editor and replace the old header
  with the edited header.
  <P>
  <PRE>
      ar&gt; imheader myimage l+ &gt; temp
      ar&gt; edit temp
      ar&gt; mkheader myimage temp append-
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  hedit, mkobjects, mknoise, mk1dspec, mk2dspec
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
