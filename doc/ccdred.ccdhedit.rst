.. _ccdhedit:

ccdhedit — CCD image header editor
==================================

**Package: ccdred**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  ccdhedit -- CCD image header editor
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  ccdhedit images parameter value
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>images</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='images' Line='images'>
  <DD>List of CCD images to be edited.
  </DD>
  </DL>
  <DL>
  <DT><B>parameter</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='parameter' Line='parameter'>
  <DD>Image header parameter.  The image header parameter will be translated by
  the header translation file for the images.
  </DD>
  </DL>
  <DL>
  <DT><B>value</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='value' Line='value'>
  <DD>The parameter value.  If the null string ("<TT></TT>") is specified then the
  parameter is deleted from the image header, otherwise it is added or
  modified.  If the parameter is "<TT>imagetyp</TT>" then the value string giving
  the CCD image type is translated from the package CCD type to the
  instrument specific string.
  </DD>
  </DL>
  <DL>
  <DT><B>type = "<TT>string</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='type' Line='type = "string"'>
  <DD>The parameter type.  The parameter types are "<TT>string</TT>", "<TT>real</TT>", or "<TT>integer</TT>".
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The image headers of the specified CCD images are edited to add, modify,
  or delete a parameter.  The parameters may be those used by the <B>ccdred</B>
  package.  The parameter name is translated to an image header parameter by the
  instrument translation file (see <B>instruments</B>) if a translation is
  given.  Otherwise the parameter is that in the image header.  If the parameter
  is "<TT>imagetyp</TT>" the parameter value for the CCD image type may be that
  used by the package; i.e. dark, object, flat, etc.  The value string will be
  translated to the instrument image string in this case.  The translation
  facility allows use of this task in an instrument independent way.
  <P>
  The value string is used to determine whether to delete or modify the
  image parameter.  If the null string, "<TT></TT>", is given the specified parameter
  is deleted.  If parameters are added the header type must be specified
  as a string, real, or integer parameter.  The numeric types convert the
  value string to a number.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  The <B>ccdred</B> package is usable even with little image header information.
  However, if desired the header information can be added to images which
  lack it.  In all the examples the parameters used are those of the package
  and apply equally well to any image header format provided there is an
  instrument translation file.
  <P>
  <PRE>
  1.   cl&gt; ccdhedit obj* imagetyp object
  2.   cl&gt; ccdhedit flat* imagetyp flat
  3.   cl&gt; ccdhedit zero* imagetyp zero
  4.   cl&gt; ccdhedit obj0![1-3]* subset "V filter"
  5.   cl&gt; ccdhedit obj0![45]* subset "R filter"
  6.   cl&gt; ccdhedit flat001 subset "R filter"
  7.   cl&gt; ccdhedit obj* exptime 500 type=integer
  </PRE>
  <P>
  8. The following is an example of a CL script which sets the CCD image type,
  the subset, and the exposure time simultaneously.  The user may expand
  on this example to include other parameters or other initialization
  operations.
  <P>
  <PRE>
      cl&gt; edit ccdheader.cl
  <P>
      ----------------------------------------------------------------
      # Program to set CCD header parameters.
  <P>
      procedure ccdheader (images)
  <P>
      string	images			{prompt="CCD images"}
      string	imagetyp		{prompt="CCD image type"}
      string	subset			{prompt="CCD subset"}
      string	exptime			{prompt="CCD exposure time"}
  <P>
      begin
  	    string	ims
  <P>
  	    ims = images
  	    ccdhedit (ims, "imagetyp", imagetyp, type="string")
  	    ccdhedit (ims, "subset", subset, type="string")
  	    ccdhedit (ims, "exptime", exptime, type="real")
      end
      ----------------------------------------------------------------
  <P>
      cl&gt; task ccdheader=ccdheader.cl
      cl&gt; ccdheader obj* imagetyp=object subset="V" exptime=500
  </PRE>
  <P>
  9. The image header may be changed to force processing a calibration image
  as an object.  For example to flatten a flat field:
  <P>
  <PRE>
      cl&gt; ccdhedit testflat imagetyp other
      cl&gt; ccdproc testflat
  </PRE>
  <P>
  10. To delete processing flags:
  <P>
      cl&gt; ccdhedit obj042 flatcor "<TT></TT>"
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  hedit, instruments, ccdtypes, subsets
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
