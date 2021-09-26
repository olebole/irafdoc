.. _chkupdate:

chkupdate: Check for an available IRAF update
=============================================

**Package: system**

.. raw:: html

  <section id="s_usage">
  <h3>Usage</h3>
  <p>
  chkupdate
  </p>
  </section>
  <section id="s_parameters">
  <h3>Parameters</h3>
  <dl id="l_interval">
  <dt><b>interval = 0</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='interval' Line='interval = 0' -->
  <dd>Number of days between updates checks.  A value less than zero will disable
  the checks entirely, a value of zero will cause a check to be made with 
  each login.
  </dd>
  </dl>
  <dl id="l_ref_file">
  <dt><b>ref_file = <span style="font-family: monospace;">"iraf$.release_date"</span></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='ref_file' Line='ref_file = "iraf$.release_date"' -->
  <dd></dd>
  </dl>
  <dl id="l_release">
  <dt><b>release = <span style="font-family: monospace;">")_.release"</span></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='release' Line='release = ")_.release"' -->
  <dd>Current IRAF release version.  This value is inherited from the CL 'release'
  parameter by default.
  </dd>
  </dl>
  <dl id="l_baseurl">
  <dt><b>baseurl = <span style="font-family: monospace;">"http://iraf.noao.edu/ftp"</span></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='baseurl' Line='baseurl = "http://iraf.noao.edu/ftp"' -->
  <dd>Base URL to the IRAF release timestamp directory.
  </dd>
  </dl>
  <dl id="l_verbose">
  <dt><b>verbose = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes' -->
  <dd>Print verbose output?
  </dd>
  </dl>
  </section>
  <section id="s_description">
  <h3>Description</h3>
  <p>
  This task compares the currently installed IRAF version with what is
  available from the NOAO servers and will indicate whether an update is
  available.  The task is executed from the login.cl each time you login 
  to the CL, however the comparison is only done if 1) the uparm$update 
  file used to indicate the time of last check does not exist, 2) the 
  <i>interval</i> parameter is zero to indicate the check should be done
  with each login, or 3) more than <i>interval</i> days have passed since
  the last time the servers were contacted.  An <i>interval</i> value less
  that zero may be used to disable the version updates entirely.
  </p>
  <p>
  The update check is done by comparing the file timestamp of the file
  named in the <i>ref_file</i> parameter with a distribution timestamp file
  on the NOAO servers.  The URL to this file is constructed from the 
  <i>baseurl</i> and <i>release</i> parameters in addition to the <i>arch</i>
  environment value, yielding a unique URL for each version and each platform.
  If the contents of the file contain a timestamp more recent than the 
  timestamp of the <i>ref_file</i> value, a message is printed to indicate
  an update is available, otherwise a message is printed indicating the
  installed system is current.
  </p>
  </section>
  <section id="s_examples">
  <h3>Examples</h3>
  <p>
  1. Check whether an IRAF update is available, regardless of when we last
  checked.
  </p>
  <div class="highlight-default-notranslate"><pre>
  cl&gt; chkupdate interval=0
  </pre></div>
  <p>
  2. Check for an IRAF update once a month.
  </p>
  <div class="highlight-default-notranslate"><pre>
  cl&gt; chkupdate.interval = 30
  </pre></div>
  </section>
  <section id="s_notes">
  <h3>Notes</h3>
  <p>
  This task is called automatically from the login.cl file at startup.
  </p>
  <p>
  Modifying the timestamp information of the <i>ref_file</i> parameter, e.g.
  by moving the IRAF tree, may invalidate the output.
  </p>
  </section>
  <section id="s_see_also">
  <h3>See also</h3>
  
  </section>
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'NOTES' 'SEE ALSO'  -->
  
