.. _names:

names — Generate a list of image names from a string
====================================================

**Package: irs**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  names -- Generate image names from a root and a range descriptor
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  names input records
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>The root file name for the input records to be calibrated.
  </DD>
  </DL>
  <DL>
  <DT><B>records</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='records' Line='records'>
  <DD>The range of spectra to be included in the calibration operation.
  Each range item will be appended to the root name to form an
  image file name.
  </DD>
  </DL>
  <DL>
  <DT><B>append = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='append' Line='append = ""'>
  <DD>If not a null string, this character string will be appended to
  all the generated image names. This allows for a specification of
  image sections.
  </DD>
  </DL>
  <DL>
  <DT><B>check = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='check' Line='check = no'>
  <DD>If set to yes, a check is made that each name implied by the range
  specification has at least an image header. The pixel file is not
  checked. If set to no, then all possible image names are generated
  even if no image exists.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  A sequence of image names is generated from the input root file name
  and the range description by appending the possible range values to
  the root in the form "<TT>root.nnnn</TT>". At least four digits will follow the
  root.
  <P>
  If an append string is specified, this is added to the image name as well.
  <P>
  The generated image names are written to STDOUT, but may be redirected
  to a file for further use.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  The following will generate names of the form nite1.0001, nite1.0002 ...
  nite1.0010 and place the list in the file nite1.lst.
  <P>
  <PRE>
  	cl&gt; names nite1 1-10 &gt;nite1.lst
  </PRE>
  <P>
  The next example uses the append option to specify that only the
  first 512 pixels of each image (spectrum) are to used in the image name.
  <P>
  <PRE>
  	cl&gt; names nite1 1-10 append="[1:512]" &gt;nite1.lst
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Revisions</H3>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B>NAMES V2.10</B></DT>
  <! Sec='REVISIONS' Level=0 Label='NAMES' Line='NAMES V2.10'>
  <DD>This task is unchanged.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'REVISIONS'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  The append option is only useful for adding image sections since it is
  added after the ONEDSPEC name is generated.  Appending other strings
  produces names such as root.0012str which are not recognized by
  the package.
  </UL>
  <! EndSection:    'BUGS'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'REVISIONS' 'BUGS'  >
  
