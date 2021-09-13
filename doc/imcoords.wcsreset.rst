.. _wcsreset:

wcsreset — Reset the specified image wcs
========================================

**Package: imcoords**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  wcsreset -- reset the image coordinate system
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  wcsreset image wcs
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>image</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='image' Line='image'>
  <DD>The list of images for which the coordinate system is to be reset.  Image
  sections are ignored.
  </DD>
  </DL>
  <DL>
  <DT><B>wcs    </B></DT>
  <! Sec='PARAMETERS' Level=0 Label='wcs' Line='wcs    '>
  <DD>The name of the coordinate system to be reset. The following systems are
  pre-defined:
  <DL>
  <DT><B>physical</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='physical' Line='physical'>
  <DD>Reset the physical coordinate system to the logical coordinate system, but
  leave the default world coordinate system unchanged.  This operation removes
  the history of past image operations such as imcopy, imshift, magnify, etc
  from the definition of the physical coordinate system, but not from the
  definition of the world coordinate system.
  </DD>
  </DL>
  <DL>
  <DT><B>world</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='world' Line='world'>
  <DD>Reset the default world coordinate system to the logical coordinate system.
  This operation removes all world coordinate system information from the
  image header.
  </DD>
  </DL>
  <P>
  In addition to these two reserved world coordinate systems, the name of any
  other defined world coordinate system, for example "<TT>multispec</TT>" may be given.
  In this case WCSRESET resets the named coordinate system to the logical
  coordinate system only if it is present in the image header.
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes'>
  <DD>Print messages about actions taken by the task?
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  WCSRESET resets the coordinate system <I>wcs</I> in the images specified by
  <I>image</I> to the logical coordinate system, and prints messages about the
  actions taken if <I>verbose</I> = "<TT>yes</TT>". Since WCSRESET modifies the
  image headers it should be used with caution.
  <P>
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
  <P>
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
  <P>
  The world coordinate system is the default coordinate system for the
  image. The default world coordinate system is the one named by the
  environment variable "<TT>defwcs</TT>" if defined in the user environment (initially
  it is undefined) and present in the image header; else it is the first
  world coordinate system
  defined for the image (the .imh and .hhh image format support only one wcs
  but the .qp format can support more); else it is the physical coordinate
  system.  Resetting the default coordinate system to the logical
  coordinate system will destroy all coordinate information for that system,
  for that image.
  <P>
  If the user sets the parameter wcs to a specific system, for example
  to "<TT>multispec</TT>", only images with the coordinate system "<TT>multispec</TT>"
  will have their coordinate system reset.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>References</H3>
  <! BeginSection: 'REFERENCES'>
  <UL>
  <P>
  Detailed documentation for the IRAF world coordinate system interface MWCS
  can be found in the file "<TT>iraf$sys/mwcs/MWCS.hlp</TT>". This file can be
  formatted and printed with the command "<TT>help iraf$sys/mwcs/MWCS.hlp fi+ |
  lprint</TT>".  Details of the FITS header world coordinate system interface can
  be found in the document "<TT>World Coordinate Systems Representations Within the
  FITS Format</TT>" by Hanisch and Wells, available from our anonymous ftp
  archive.
  <P>
  </UL>
  <! EndSection:   'REFERENCES'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. The user runs implot on a section of the spectrum outspec with the
  wcs parameter set to "<TT>physical</TT>".
  <P>
  <PRE>
  	implot outsec[30:50] wcs=physical
  </PRE>
  <P>
  To his/her surprise the range of the plot in x produced by implot is
  [129,149] not [30:50] as expected.  The user lists the image header with the
  imheader task and sees the following.
  <P>
  <PRE>
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
  </PRE>
  <P>
  The standard FITS keywords CTYPE1, CRVAL1, CRPIX1, and CDELT1 are present.
  The CD1_1 keyword is part of the new FITS CD matrix notation and in this
  example duplicates the function of CDELT1.  The remaining keywords WCSDIM,
  WAT0_001, WAT1_001, LTV1, and LTM1_1 are IRAF specific keywords. The
  user notes that the LTV1 keyword is -99. not 0. and suddenly remembers that
  outspec was created by extracting a piece of a larger spectrum using the
  imcopy task as shown below.
  <P>
  <PRE>
  	cl&gt; imcopy inspec[100:200] outspec
  </PRE>
  <P>
  The section [30:50] in outspec actually corresponds to the section [129:149]
  in inspec and it is this coordinate system that implot is plotting when
  wcs = "<TT>physical</TT>". The user decides has he/she does not want to know
  about the pixel coordinate system of the original image and runs wcsreset
  to reset the physical coordinate system to the logical coordinate system.
  <P>
  <PRE>
  	wcsreset outspec physical
  </PRE>
  <P>
  The new header of outspec looks like the following.
  <P>
  <PRE>
      WCSDIM  =                    1
      CTYPE1  = 'LINEAR  '
      CRVAL1  =     4953.94775390626
      CRPIX1  =                 -98.
      CDELT1  =   0.0714096948504449
      CD1_1   =   0.0714096948504449
      WAT0_001= 'system=linear                                                    
      WAT1_001= 'wtype=linear label=Wavelength units=Angstroms
      LTM1_1  =                   1.
  </PRE>
  <P>
  It is identical to the header listed above except that the
  LTV1 keyword is not defined and is therefore 0. The user runs
  implot with wcs = "<TT>physical</TT>" as before and sees a plot which extends
  from 30 to 50 as expected.
  <P>
  2. Reset the physical coordinate system of the direct CCD image skypix
  which has a defined sky projection system. Skypix was created by
  copying the central [129:384,129:384] of a 512 square image into a 256
  square image.
  <P>
  The image header is the following.
  <P>
  <PRE>
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
  </PRE>
  <P>
  The user runs implot on skypix wcs = "<TT>physical</TT>"
  <P>
  <PRE>
  	implot skypix wcs=physical
  </PRE>
  <P>
  and sees a plot in x which extends from 129 to 384 which are the coordinates
  of skypix in the original image.
  The user resets the physical coordinate system to the logical coordinate
  system.
  <P>
  <PRE>
  	cl&gt; wcsreset m51 physical
  </PRE>
  <P>
  The new header looks like the following. Note that the LTV1 and LTV2 keywords
  have disappeared, they are 0. but everything else is the same.
  <P>
  <PRE>
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
  </PRE>
  <P>
  When the user runs implot with wcs = "<TT>physical</TT>" he/she sees a plot which
  extends from 1 to 256 as expected.
  <P>
  3. Initialize the world coordinate system of the previous image.
  <P>
  <PRE>
  	cl&gt; wcsreset skypix world
  </PRE>
  <P>
  The header now looks like the following.
  <P>
  <PRE>
  	WCSDIM  =                    2
  	LTM1_1  =                   1.
  	LTM2_2  =                   1.
  	WAT0_001= 'system=physical               
  	WAT1_001= 'wtype=linear
  	WAT2_001= 'wtype=linear
  </PRE>
  <P>
  The world system defaults to the physical coordinates system and the
  physical coordinate system is identical to the logical coordinate system.
  All coordinate information has been destroyed.
  <P>
  4. Initialize the world coordinate system "<TT>spec1</TT>". If the default world
  coordinate
  system "<TT>spec1</TT>" cannot be found in the image header a warning message
  will be issued and nothing will be changed.
  <P>
  <PRE>
  	cl&gt; wcsreset spectrum spec1
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
  rimcursor,listpixels,wcsedit,hedit,hfix
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'REFERENCES' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
