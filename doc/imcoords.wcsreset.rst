.. _wcsreset:

wcsreset: Reset the specified image wcs
=======================================

**Package: imcoords**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  wcsreset -- reset the image coordinate system
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  wcsreset image wcs
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>image</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='image' Line='image' -->
  <dd>The list of images for which the coordinate system is to be reset.  Image
  sections are ignored.
  </dd>
  </dl>
  <dl>
  <dt><b>wcs    </b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='wcs' Line='wcs    ' -->
  <dd>The name of the coordinate system to be reset. The following systems are
  pre-defined:
  <dl>
  <dt><b>physical</b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='physical' Line='physical' -->
  <dd>Reset the physical coordinate system to the logical coordinate system, but
  leave the default world coordinate system unchanged.  This operation removes
  the history of past image operations such as imcopy, imshift, magnify, etc
  from the definition of the physical coordinate system, but not from the
  definition of the world coordinate system.
  </dd>
  </dl>
  <dl>
  <dt><b>world</b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='world' Line='world' -->
  <dd>Reset the default world coordinate system to the logical coordinate system.
  This operation removes all world coordinate system information from the
  image header.
  </dd>
  </dl>
  In addition to these two reserved world coordinate systems, the name of any
  other defined world coordinate system, for example <tt>"multispec"</tt> may be given.
  In this case WCSRESET resets the named coordinate system to the logical
  coordinate system only if it is present in the image header.
  </dd>
  </dl>
  <dl>
  <dt><b>verbose = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes' -->
  <dd>Print messages about actions taken by the task?
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  WCSRESET resets the coordinate system <i>wcs</i> in the images specified by
  <i>image</i> to the logical coordinate system, and prints messages about the
  actions taken if <i>verbose</i> = <tt>"yes"</tt>. Since WCSRESET modifies the
  image headers it should be used with caution.
  </p>
  <p>
  Logical coordinates are coordinates relative to the current image.  The
  logical coordinate system is the one used by the image input/output routines
  to access the image on disk.  In an image raster logical coordinate system,
  the coordinates of the pixel centers must lie within the following
  range: 1.0 &lt;= x[i] &lt;= nx[i], where x[i] is the coordinate in dimension i,
  nx[i] is the size of the image in dimension i, and the current maximum
  number of image dimensions is 7. In the case of an image section of an image
  raster, the nx[i] refer to the dimensions of the section, not the dimensions
  of the full image. The logical coordinate system cannot by definition be
  reset.
  </p>
  <p>
  The physical coordinate system is the coordinate system in which the
  coordinates of an object are invariant to successive linear transformations
  of the image. In this coordinate system, the pixel coordinates of an object
  in an image raster remain the same, regardless of any imcopy, imshift,
  rotate, etc operations on the image. The most common reason for desiring to
  reset the physical coordinate system to the logical coordinate system is to
  make the new image independent of its history by removing the effects of
  these linear transformation operations from its physical coordinate system.
  Resetting the physical coordinate system to the logical coordinate system,
  does not alter the default world coordinate system. If for example the input
  image is a spectrum, with a defined dispersion solution, resetting the
  physical coordinate system will not alter the dispersion solution.
  Similarly if the input image is a direct CCD image with a defined sky
  projection world coordinate system, resetting the physical coordinate system
  will not alter the sky projection.
  </p>
  <p>
  The world coordinate system is the default coordinate system for the
  image. The default world coordinate system is the one named by the
  environment variable <tt>"defwcs"</tt> if defined in the user environment (initially
  it is undefined) and present in the image header; else it is the first
  world coordinate system
  defined for the image (the .imh and .hhh image format support only one wcs
  but the .qp format can support more); else it is the physical coordinate
  system.  Resetting the default coordinate system to the logical
  coordinate system will destroy all coordinate information for that system,
  for that image.
  </p>
  <p>
  If the user sets the parameter wcs to a specific system, for example
  to <tt>"multispec"</tt>, only images with the coordinate system <tt>"multispec"</tt>
  will have their coordinate system reset.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>References</h3>
  <!-- BeginSection: 'REFERENCES' -->
  <p>
  Detailed documentation for the IRAF world coordinate system interface MWCS
  can be found in the file <tt>"iraf$sys/mwcs/MWCS.hlp"</tt>. This file can be
  formatted and printed with the command <tt>"help iraf$sys/mwcs/MWCS.hlp fi+ |
  lprint"</tt>.  Details of the FITS header world coordinate system interface can
  be found in the document <tt>"World Coordinate Systems Representations Within the
  FITS Format"</tt> by Hanisch and Wells, available from our anonymous ftp
  archive.
  </p>
  <!-- EndSection:   'REFERENCES' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. The user runs implot on a section of the spectrum outspec with the
  wcs parameter set to <tt>"physical"</tt>.
  </p>
  <pre>
  	implot outsec[30:50] wcs=physical
  </pre>
  <p>
  To his/her surprise the range of the plot in x produced by implot is
  [129,149] not [30:50] as expected.  The user lists the image header with the
  imheader task and sees the following.
  </p>
  <pre>
          WCSDIM  =                    1
          CTYPE1  = 'LINEAR  '
          CRVAL1  =     4953.94775390626
          CRPIX1  =                 -98.
          CDELT1  =   0.0714096948504449
          CD1_1   =   0.0714096948504449
          WAT0_001= 'system=linear
          WAT1_001= 'wtype=linear label=Wavelength units=Angstroms 
          LTV1    =                 -99.
          LTM1_1  =                   1.
  </pre>
  <p>
  The standard FITS keywords CTYPE1, CRVAL1, CRPIX1, and CDELT1 are present.
  The CD1_1 keyword is part of the new FITS CD matrix notation and in this
  example duplicates the function of CDELT1.  The remaining keywords WCSDIM,
  WAT0_001, WAT1_001, LTV1, and LTM1_1 are IRAF specific keywords. The
  user notes that the LTV1 keyword is -99. not 0. and suddenly remembers that
  outspec was created by extracting a piece of a larger spectrum using the
  imcopy task as shown below.
  </p>
  <pre>
  	cl&gt; imcopy inspec[100:200] outspec
  </pre>
  <p>
  The section [30:50] in outspec actually corresponds to the section [129:149]
  in inspec and it is this coordinate system that implot is plotting when
  wcs = <tt>"physical"</tt>. The user decides has he/she does not want to know
  about the pixel coordinate system of the original image and runs wcsreset
  to reset the physical coordinate system to the logical coordinate system.
  </p>
  <pre>
  	wcsreset outspec physical
  </pre>
  <p>
  The new header of outspec looks like the following.
  </p>
  <pre>
      WCSDIM  =                    1
      CTYPE1  = 'LINEAR  '
      CRVAL1  =     4953.94775390626
      CRPIX1  =                 -98.
      CDELT1  =   0.0714096948504449
      CD1_1   =   0.0714096948504449
      WAT0_001= 'system=linear                                                    
      WAT1_001= 'wtype=linear label=Wavelength units=Angstroms
      LTM1_1  =                   1.
  </pre>
  <p>
  It is identical to the header listed above except that the
  LTV1 keyword is not defined and is therefore 0. The user runs
  implot with wcs = <tt>"physical"</tt> as before and sees a plot which extends
  from 30 to 50 as expected.
  </p>
  <p>
  2. Reset the physical coordinate system of the direct CCD image skypix
  which has a defined sky projection system. Skypix was created by
  copying the central [129:384,129:384] of a 512 square image into a 256
  square image.
  </p>
  <p>
  The image header is the following.
  </p>
  <pre>
  	CRPIX1  =               129.75
          CRPIX2  =               130.93
          CRVAL1  =      201.94541667302
          CRVAL2  =             47.45444
          CTYPE1  = 'RA---TAN'
          CTYPE2  = 'DEC--TAN'
          CDELT1  =        -2.1277777E-4
          CDELT2  =         2.1277777E-4
          WCSDIM  =                    2
          CD1_1   =  -2.1277777000000E-4
          CD2_2   =  2.12777770000000E-4
          LTV1    =                -128.
          LTV2    =                -128.
          LTM1_1  =                   1.
          LTM2_2  =                   1.
          WAT0_001= 'system=image
  	WAT1_001= 'wtype=tan axtype=ra
  	WAT2_001= 'wtype=tan axtype=dec
  </pre>
  <p>
  The user runs implot on skypix wcs = <tt>"physical"</tt>
  </p>
  <pre>
  	implot skypix wcs=physical
  </pre>
  <p>
  and sees a plot in x which extends from 129 to 384 which are the coordinates
  of skypix in the original image.
  The user resets the physical coordinate system to the logical coordinate
  system.
  </p>
  <pre>
  	cl&gt; wcsreset m51 physical
  </pre>
  <p>
  The new header looks like the following. Note that the LTV1 and LTV2 keywords
  have disappeared, they are 0. but everything else is the same.
  </p>
  <pre>
  	CRPIX1  =               129.75
          CRPIX2  =               130.93
          CRVAL1  =      201.94541667302
          CRVAL2  =             47.45444
          CTYPE1  = 'RA---TAN'
          CTYPE2  = 'DEC--TAN'
          CDELT1  =        -2.1277777E-4
          CDELT2  =         2.1277777E-4
          WCSDIM  =                    2
          CD1_1   =  -2.1277777000000E-4
          CD2_2   =  2.12777770000000E-4
          LTM1_1  =                   1.
          LTM2_2  =                   1.
          WAT0_001= 'system=image
  	WAT1_001= 'wtype=tan axtype=ra
  	WAT2_001= 'wtype=tan axtype=dec
  </pre>
  <p>
  When the user runs implot with wcs = <tt>"physical"</tt> he/she sees a plot which
  extends from 1 to 256 as expected.
  </p>
  <p>
  3. Initialize the world coordinate system of the previous image.
  </p>
  <pre>
  	cl&gt; wcsreset skypix world
  </pre>
  <p>
  The header now looks like the following.
  </p>
  <pre>
  	WCSDIM  =                    2
  	LTM1_1  =                   1.
  	LTM2_2  =                   1.
  	WAT0_001= 'system=physical               
  	WAT1_001= 'wtype=linear
  	WAT2_001= 'wtype=linear
  </pre>
  <p>
  The world system defaults to the physical coordinates system and the
  physical coordinate system is identical to the logical coordinate system.
  All coordinate information has been destroyed.
  </p>
  <p>
  4. Initialize the world coordinate system <tt>"spec1"</tt>. If the default world
  coordinate
  system <tt>"spec1"</tt> cannot be found in the image header a warning message
  will be issued and nothing will be changed.
  </p>
  <pre>
  	cl&gt; wcsreset spectrum spec1
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
  rimcursor,listpixels,wcsedit,hedit,hfix
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'REFERENCES' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  -->
  
