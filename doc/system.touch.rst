.. _touch:

touch: Change file access and modification times
================================================

**Package: system**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  touch -- change file access and modification times
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  touch files
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>files</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='files' Line='files' -->
  <dd>List of files to be created or touched.
  </dd>
  </dl>
  <dl>
  <dt><b>create = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='create' Line='create = yes' -->
  <dd>If enabled, the file will be created as a zero-length text file if it doesn't
  already exist.
  </dd>
  </dl>
  <dl>
  <dt><b>atime = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='atime' Line='atime = yes' -->
  <dd>Change the access time of the file.  Will not change the modification time
  unless <i>mtime</i> is also set.
  </dd>
  </dl>
  <dl>
  <dt><b>mtime = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='mtime' Line='mtime = yes' -->
  <dd>Change the modification time of the file.  Will not change the access time
  unless <i>atime</i> is also set.
  </dd>
  </dl>
  <dl>
  <dt><b>time = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='time' Line='time = ""' -->
  <dd>Time and date to set for the file.  The format of this string may be any
  of DD/MM/YY or CCYY-MM-DD (in which case time is assumed to be midnight of
  that day), or CCYY-MM-DDTHH:MM:SS[.SSS...] to specify both date and time.
  If not specified, the current system time is used unless the <i>ref_file</i>
  parameter is set.  If specified, <i>ref_file</i> will be ignored.
  </dd>
  </dl>
  <dl>
  <dt><b>ref_file = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='ref_file' Line='ref_file = ""' -->
  <dd>Use the corresponding times of the specified file for modifying the
  times of the <i>input_files</i>.  If not specified, the current time is
  used unless the <i>time</i> parameter is set.
  </dd>
  </dl>
  <dl>
  <dt><b>verbose = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = no' -->
  <dd>Print verbose output of the files and times being reset.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  The <i>touch</i> task sets the access and modification times of each file
  in the <i>files</i> list.  The file will be created if it does not already
  exist when the <i>create</i> parameter is set.  The time used can be
  specified by <i>time</i> parameter or by the corresponding fields of the
  file specified by <i>ref_file</i>, otherwise the current system time will
  be used.  The task will update both the modification and access times of
  the file unless disabled by the <i>atime</i> or <i>mtime</i> parameter.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1.  Update the times of all SPP source files in the current directory:
  </p>
  <p>
  	cl&gt; touch *.x
  </p>
  <p>
  2.  Create an empty file on a remode node:
  </p>
  <p>
  	cl&gt; touch ursa!/data/trigger_file
  </p>
  <p>
  3.  Reset the file modification time to 2:33:45 pm on June 5, 2003:
  </p>
  <p>
  	cl&gt; touch nite1.fits time=<tt>"2003-06-05T14:23:45"</tt>
  </p>
  <p>
  4.  Reset the file modification time to match dev$hosts:
  </p>
  <p>
  	cl&gt; touch nite1.fits ref_file=dev$hosts
  </p>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  -->
  
