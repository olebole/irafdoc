.. _ldumpf:

ldumpf — List the permanent files on a Cyber DUMPF tape
=======================================================

**Package: mtlocal**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  ldumpf -- list the permanent files on a Cyber DUMPF tape.
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  ldumpf dumpf_file file_list
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>dumpf_file</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='dumpf_file' Line='dumpf_file'>
  <DD>The DUMPF data source, i.e., the name of a magtape device or a DUMPF
  format disk file.   If reading from tape, the files to be listed are
  specified by the <I>file_list</I> parameter.
  </DD>
  </DL>
  <DL>
  <DT><B>file_list</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='file_list' Line='file_list'>
  <DD>A string listing the DUMPF files to be listed from <I>dumpf_file</I>.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Cyber permanent files stored on DUMPF tapes are listed.  The permanent file
  name, cycle number, owner id, dates of last attach, last alteration and
  the creation date are printed.  Task <B>ldumpf</B> lists the contents of a 
  DUMPF tape;
  to convert IPPS rasters stored on DUMPF tapes to IRAF images, use task
  <B>rdumpf</B>.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  List all permanent files on a DUMPF tape:
  <P>
  	cl&gt; ldumpf mta 1-999
  <P>
  List information for the 4th permanent file on the tape:
  <P>
  	cl&gt; ldumpf mta 4
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  The Cyber format readers, including task <I>ldumpf</I>, have not been 
  implemented on SUN/IRAF and AOS/IRAF.
  <P>
  The current version of IRAF magtape I/O does not read beyond the first
  volume of a multivolume tape.
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  rdumpf
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
