.. _wcscopy:

wcscopy: Copy the wcs from one image to another
===============================================

**Package: immatch**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  wcscopy -- copy the wcs of a reference image to a list of images
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  wcscopy images refimages
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>images</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='images' Line='images' -->
  <dd>The list of input images which will inherit the wcs of the reference image.
  If the image does not exists a dataless image header is created.
  </dd>
  </dl>
  <dl>
  <dt><b>reference</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='reference' Line='reference' -->
  <dd>The list of reference images containing the reference wcs. The number of
  reference images must be one or equal to the number of input images.
  </dd>
  </dl>
  <dl>
  <dt><b>verbose = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes' -->
  <dd>Print messages about the progress of the task?
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  WCSCOPY copies the world coordinate system information in the header of the
  reference image <i>reference</i> to the headers of the input images
  <i>images</i>, replacing any existing world coordinate system information
  in the input image headers in the process. WCSCOPY assumes that the
  world coordinate system information in the header of the reference 
  image is accurate and that all the input images have write permission.
  If the input image does not exist a data-less image header is created.
  The WCS is treated as an independent object and
  there is no check made on the dimensionality and sizes of the images.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>References</h3>
  <!-- BeginSection: 'REFERENCES' -->
  <p>
  Information  on  IRAF  world  coordinate  systems including
  more detailed descriptions of the <tt>"logical"</tt>, <tt>"physical"</tt>, and <tt>"world"</tt>
  coordinate systems can be
  found  in  the  help  pages  for  the  WCSEDIT  and  WCRESET  tasks. 
  Detailed   documentation   for  the  IRAF  world  coordinate  system 
  interface MWCS can be found in  the  file  <tt>"iraf$sys/mwcs/MWCS.hlp"</tt>.
  This  file  can  be  formatted  and  printed  with the command <tt>"help
  iraf$sys/mwcs/MWCS.hlp fi+ | lprint"</tt>.  Information on the spectral
  coordinates systems and their suitability for use with WCSXYMATCH
  can be obtained by typing <tt>"help specwcs | lprint"</tt>.
  Details of  the  FITS  header
  world  coordinate  system  interface  can  be  found in the document
  <tt>"World Coordinate Systems Representations Within  the  FITS  Format"</tt>
  by Hanisch and Wells, available from our anonymous ftp archive.
      
  </p>
  <!-- EndSection:   'REFERENCES' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Make sure that the world coordinates systems of a list of input images
  that have been registered to a reference image with the xregister task
  are identical to the world coordinate system of the reference image.
  </p>
  <pre>
  	cl&gt; xregister @inlist refimage [200:400,200:400] shifts \<br>
  	    output=@outlist xwindow=21 ywindow=21
  	cl&gt; wcscopy @outlist refimage
  </pre>
  <p>
  2.  Create a data-less WCS image by specifying a new image.
  </p>
  <pre>
  	cl&gt; wcscopy new dev$wpix
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Time requirements</h3>
  <!-- BeginSection: 'TIME REQUIREMENTS' -->
  <!-- EndSection:   'TIME REQUIREMENTS' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <!-- EndSection:   'BUGS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  tprecess,imalign,xregister,geomap,register,geotran,wcsmap,wregister,wcsedit
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'REFERENCES' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  -->
  
