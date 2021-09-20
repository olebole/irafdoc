.. _mkheader:

mkheader: Append/replace header parameters
==========================================

**Package: artdata**

.. raw:: html

  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  mkheader images headers
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>images</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='images' Line='images' -->
  <dd>List of images in which header information is to be added or modified.
  </dd>
  </dl>
  <dl>
  <dt><b>header = <span style="font-family: monospace;">"artdata$stdheader.dat"</span></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='header' Line='header = "artdata$stdheader.dat"' -->
  <dd>List of images or header keyword data files.  If the list is shorter
  than the input image list then the last entry is repeated.
  If an image is given then the image header
  is copied.  If a file is given then the FITS format cards are copied.
  This only applies to new images.   The data file consists of lines
  in FITS format with leading whitespace ignored.  A FITS card must begin
  with an uppercase/numeric keyword.  Lines not beginning with a FITS
  keyword such as comments or lower case are ignored.  The user keyword
  output of <b>imheader</b> is an acceptable data file.
  </dd>
  </dl>
  <dl>
  <dt><b>append = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='append' Line='append = yes' -->
  <dd>Append to existing keywords?  If no then the existing header is replaced.
  </dd>
  </dl>
  <dl>
  <dt><b>verbose = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = no' -->
  <dd>Verbose output?
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  The image headers in the list of input images may be replaced or appended
  with information from images or data files specified by the <i>header</i>
  parameter list.  If the header list is shorter than the list of images
  to be modified the last header file is repeated.  Depending on the
  value of the <i>append</i> parameter, new parameters will be appended
  or replace the existing image header parameters.
  </p>
  <p>
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
  the long output of <b>imheader</b> may be used directly as input.
  </p>
  <p>
  Header files are also used by several of the tasks in the artificial
  data package with a standard default file <span style="font-family: monospace;">"artdata$stdheader.dat"</span>.
  To edit image headers also see <b>hedit</b>.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Add some standard keywords from a file to an image.
  </p>
  <pre>
      ar&gt; type myheader
      # MY header list
      INSTRUME= 'bspec mark II'		/ B Spectrograph
      LENS    =                  3	/ Lens number
      FOCRATIO=                5.2        / Focal ratio
      ar&gt; mkheader *.imh myheader
  </pre>
  <p>
  2. Copy an image header.
  </p>
  <p>
      ar&gt; mkheader new dev$pix append-
  </p>
  <p>
  3. Edit the image header with a text editor and replace the old header
  with the edited header.
  </p>
  <pre>
      ar&gt; imheader myimage l+ &gt; temp
      ar&gt; edit temp
      ar&gt; mkheader myimage temp append-
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  hedit, mkobjects, mknoise, mk1dspec, mk2dspec
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  -->
  
