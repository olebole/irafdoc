.. _ccdtypes:

ccdtypes — Description of the CCD image types
=============================================

**Package: quadred**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  ccdtypes -- Description of the CCD image types
  </UL>
  <! EndSection:   'NAME'>
  <H3>Ccdtypes</H3>
  <! BeginSection: 'CCDTYPES'>
  <UL>
  The following CCD image types may be specified as the value of the parameter
  <I>ccdtype</I>:
  <P>
  <PRE>
  	""	- (the null string) all image types
  	object	- object images
  	zero	- zero level images such as a bias or preflash
  	dark	- dark count images
  	flat	- flat field images
  	illum	- iillumination images
  	fringe	- fringe correction images
  	other   - other image types defined in the translation file
  	none	- images without an image type parameter
  	unknown - image types not defined in the translation file
  </PRE>
  </UL>
  <! EndSection:   'CCDTYPES'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The <B>ccdred</B> package recognizes certain standard CCD image types
  identified in the image header.  The tasks may select images of a
  particular CCD image type from image lists with the parameter
  <I>ccdtype</I> and also recognize and take special actions for
  calibration images.
  <P>
  In order to make use of CCD image type information the header keyword
  identifying the image type must be specified in the instrument
  translation file.  This entry has the form
  <P>
  	imagetyp keyword
  <P>
  where keyword is the image header keyword.  This allows the package to
  access the image type string.  There must also be a translation between
  the image type strings and the CCD types as recognized by the package.
  This information consists of lines in the instrument translation file
  of the form
  <P>
  	header	package
  <P>
  where header is the exact string given in the image header and package
  is one of the types recognized by the package.  The image header string
  can be virtually anything and if it contains blanks it must be
  quoted.  The package image types are those given above except for
  the null string, "<TT>none</TT>", and "<TT>unknown</TT>".  That is, these types may
  be specified as a CCD image type in selecting images but not as a translations
  of image type strings.
  <P>
  There may be more than one image type that maps to the same package
  type.  In particular other standard CCD image types, such as comparison
  spectra, multiple exposure, standard star, etc., should be mapped to
  object or other.  There may also be more than one type of flat field, i.e. dome
  flat, sky flat, and lamp flat.  For more on the instrument translation
  file see the help for <B>instruments</B>.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. The example entries in the instrument translation file are from the 1986
  NOAO CCD image header format produced by the CAMERA format tape writer.
  <P>
  <PRE>
      imagetyp			data-typ
  <P>
      'OBJECT (0)'		object
      'DARK (1)'			dark
      'PROJECTOR FLAT (2)'	flat
      'SKY FLAT (3)'		other
      'COMPARISON LAMP (4)'	other
      'BIAS (5)'			zero
      'DOME FLAT (6)'		flat
  </PRE>
  <P>
  The image header keyword describing the image type is "<TT>data-typ</TT>".
  The values of the image type strings in the header contain blanks so they
  are quoted.  Also the case of the strings is important.  Note that there
  are two types of flat field images and two types of other images.
  <P>
  2. One way to check the image types is with the task <B>ccdlist</B>.
  <P>
  <PRE>
      cl&gt; ccdlist *.imh
      Zero.imh[504,1][real][zero][1][OT]:FOCUS L98-193
      Flat1.imh[504,1][real][flat][1][OTZ]:dflat 6v+blue 5s
      ccd002.imh[504,504][real][unknown][1][OTZF]:FOCUS L98-193
      ccd003.imh[544,512][short][object][1]:L98-193
      ccd004.imh[544,512][short][object][1]:L98-193
      ccd005.imh[544,512][short][object][1]:L98-193
      oldformat.imh[544,512][short][none][1]:M31 V
  </PRE>
  <P>
  The unknown type has a header image type of "<TT>MUL (8)</TT>".  The old format
  image does not have any header type.
  <P>
  3. To select only images of a particular type:
  <P>
  <PRE>
      cl&gt; ccdlist *.imh ccdtype=object
      ccd003.imh[544,512][short][object][1]:L98-193
      ccd004.imh[544,512][short][object][1]:L98-193
      ccd005.imh[544,512][short][object][1]:L98-193
      cl&gt; ccdlist *.imh ccdtype=unknown
      ccd002.imh[504,504][real][unknown][1][OTZF]:FOCUS L98-193
      cl&gt; ccdlist *.imh ccdtype=none
      oldformat.imh[544,512][short][none][1]:M31 V
  </PRE>
  <P>
  4. To process images with <B>ccdproc</B>:
  <P>
  <PRE>
      cl&gt; ccdproc *.imh
      cl&gt; ccdproc *.imh ccdtype=object
  </PRE>
  <P>
  In the first case all the images will be processed (the default value of
  <I>ccdtype</I> is "<TT></TT>").  However, the task recognizes the calibration
  images, such as zero level and flat fields, and processes them appropriately.
  In the second case only object images are processed and all other images
  are ignored (except if needed as a calibration image).
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  instruments
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'CCDTYPES' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
