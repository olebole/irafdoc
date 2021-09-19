.. _ccdhedit:

ccdhedit: CCD image header editor
=================================

**Package: quadred**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  ccdhedit -- CCD image header editor
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  ccdhedit images parameter value
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>images</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='images' Line='images' -->
  <dd>List of CCD images to be edited.
  </dd>
  </dl>
  <dl>
  <dt><b>parameter</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='parameter' Line='parameter' -->
  <dd>Image header parameter.  The image header parameter will be translated by
  the header translation file for the images.
  </dd>
  </dl>
  <dl>
  <dt><b>value</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='value' Line='value' -->
  <dd>The parameter value.  If the null string (<tt>""</tt>) is specified then the
  parameter is deleted from the image header, otherwise it is added or
  modified.  If the parameter is <tt>"imagetyp"</tt> then the value string giving
  the CCD image type is translated from the package CCD type to the
  instrument specific string.
  </dd>
  </dl>
  <dl>
  <dt><b>type = <tt>"string"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='type' Line='type = "string"' -->
  <dd>The parameter type.  The parameter types are <tt>"string"</tt>, <tt>"real"</tt>, or <tt>"integer"</tt>.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  The image headers of the specified CCD images are edited to add, modify,
  or delete a parameter.  The parameters may be those used by the <b>ccdred</b>
  package.  The parameter name is translated to an image header parameter by the
  instrument translation file (see <b>instruments</b>) if a translation is
  given.  Otherwise the parameter is that in the image header.  If the parameter
  is <tt>"imagetyp"</tt> the parameter value for the CCD image type may be that
  used by the package; i.e. dark, object, flat, etc.  The value string will be
  translated to the instrument image string in this case.  The translation
  facility allows use of this task in an instrument independent way.
  </p>
  <p>
  The value string is used to determine whether to delete or modify the
  image parameter.  If the null string, <tt>""</tt>, is given the specified parameter
  is deleted.  If parameters are added the header type must be specified
  as a string, real, or integer parameter.  The numeric types convert the
  value string to a number.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  The <b>ccdred</b> package is usable even with little image header information.
  However, if desired the header information can be added to images which
  lack it.  In all the examples the parameters used are those of the package
  and apply equally well to any image header format provided there is an
  instrument translation file.
  </p>
  <pre>
  1.   cl&gt; ccdhedit obj* imagetyp object
  2.   cl&gt; ccdhedit flat* imagetyp flat
  3.   cl&gt; ccdhedit zero* imagetyp zero
  4.   cl&gt; ccdhedit obj0![1-3]* subset "V filter"
  5.   cl&gt; ccdhedit obj0![45]* subset "R filter"
  6.   cl&gt; ccdhedit flat001 subset "R filter"
  7.   cl&gt; ccdhedit obj* exptime 500 type=integer
  </pre>
  <p>
  8. The following is an example of a CL script which sets the CCD image type,
  the subset, and the exposure time simultaneously.  The user may expand
  on this example to include other parameters or other initialization
  operations.
  </p>
  <pre>
      cl&gt; edit ccdheader.cl
  
      ----------------------------------------------------------------
      # Program to set CCD header parameters.
  
      procedure ccdheader (images)
  
      string	images			{prompt="CCD images"}
      string	imagetyp		{prompt="CCD image type"}
      string	subset			{prompt="CCD subset"}
      string	exptime			{prompt="CCD exposure time"}
  
      begin
  	    string	ims
  
  	    ims = images
  	    ccdhedit (ims, "imagetyp", imagetyp, type="string")
  	    ccdhedit (ims, "subset", subset, type="string")
  	    ccdhedit (ims, "exptime", exptime, type="real")
      end
      ----------------------------------------------------------------
  
      cl&gt; task ccdheader=ccdheader.cl
      cl&gt; ccdheader obj* imagetyp=object subset="V" exptime=500
  </pre>
  <p>
  9. The image header may be changed to force processing a calibration image
  as an object.  For example to flatten a flat field:
  </p>
  <pre>
      cl&gt; ccdhedit testflat imagetyp other
      cl&gt; ccdproc testflat
  </pre>
  <p>
  10. To delete processing flags:
  </p>
  <p>
      cl&gt; ccdhedit obj042 flatcor <tt>""</tt>
  </p>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  hedit, instruments, ccdtypes, subsets
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  -->
  
