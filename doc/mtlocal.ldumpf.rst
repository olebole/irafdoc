.. _ldumpf:

ldumpf: List the permanent files on a Cyber DUMPF tape
======================================================

**Package: mtlocal**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  ldumpf -- list the permanent files on a Cyber DUMPF tape.
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  ldumpf dumpf_file file_list
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>dumpf_file</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='dumpf_file' Line='dumpf_file' -->
  <dd>The DUMPF data source, i.e., the name of a magtape device or a DUMPF
  format disk file.   If reading from tape, the files to be listed are
  specified by the <i>file_list</i> parameter.
  </dd>
  </dl>
  <dl>
  <dt><b>file_list</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='file_list' Line='file_list' -->
  <dd>A string listing the DUMPF files to be listed from <i>dumpf_file</i>.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  Cyber permanent files stored on DUMPF tapes are listed.  The permanent file
  name, cycle number, owner id, dates of last attach, last alteration and
  the creation date are printed.  Task <b>ldumpf</b> lists the contents of a 
  DUMPF tape;
  to convert IPPS rasters stored on DUMPF tapes to IRAF images, use task
  <b>rdumpf</b>.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  List all permanent files on a DUMPF tape:
  </p>
  <p>
  	cl&gt; ldumpf mta 1-999
  </p>
  <p>
  List information for the 4th permanent file on the tape:
  </p>
  <p>
  	cl&gt; ldumpf mta 4
  </p>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <p>
  The Cyber format readers, including task <i>ldumpf</i>, have not been 
  implemented on SUN/IRAF and AOS/IRAF.
  </p>
  <p>
  The current version of IRAF magtape I/O does not read beyond the first
  volume of a multivolume tape.
  </p>
  <!-- EndSection:   'BUGS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  rdumpf
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  -->
  
