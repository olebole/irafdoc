.. _istable:

istable: Is a file a table or text database file ?
==================================================

**Package: ptools**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  istable --  determine the status of a file
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  istable infile
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>infile</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='infile' Line='infile' -->
  <dd>The name of the input file whose status is to be determined.
  </dd>
  </dl>
  <dl>
  <dt><b>table = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='table' Line='table = no' -->
  <dd>An output variable which is <tt>"yes"</tt> if <i>infile</i> is an STSDAS table
  and <tt>"no"</tt> otherwise.
  </dd>
  </dl>
  <dl>
  <dt><b>text = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='text' Line='text = no' -->
  <dd>An output variable which is <tt>"yes"</tt> if <i>infile</i> is an APPHOT/DAOPHOT
  text database and <tt>"no"</tt> otherwise.
  </dd>
  </dl>
  <dl>
  <dt><b>other = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='other' Line='other = no' -->
  <dd>An output variable which is <tt>"yes"</tt> if <i>infile</i> is neither of the
  above and <tt>"no"</tt> otherwise.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  ISTABLE is a very simple task which determines whether a specified
  input file is an STSDAS table, an APPHOT/DAOPHOT text database file or 
  neither of the above. ISTABLE first tries to open the input file as an 
  STSDAS table. If successful ISTABLE returns <tt>"yes"</tt> in the
  variable <i>table</i> and <tt>"no"</tt> in <i>text</i> and <i>other</i>. Otherwise
  ISTABLE  tries to open the input file as an APPHOT/DAOPHOT text database
  file by checking for the <tt>"#K IRAF"</tt> keyword.
  If the check is positive ISTABLE return <tt>"yes"</tt> in
  the variable <i>text</i> and <tt>"no"</tt> in <i>table</i> and <i>other</i>. If the input
  file is neither an STSDAS table or an APPHOT/DAOPHOT text database
  ISTABLE returns <tt>"yes"</tt> in the variable <i>other</i> and <tt>"no"</tt> in <i>text</i>
  and <i>table</i>.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Determine whether the file n4147.mag.1 is an STSDAS table.
  </p>
  <pre>
     pt&gt; istable n4147.mag
     pt&gt; =istable.table
  
         ... answer will appear on the screen
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Time requirements</h3>
  <!-- BeginSection: 'TIME REQUIREMENTS' -->
  <!-- EndSection:   'TIME REQUIREMENTS' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <p>
  Users should be wary of running ISTABLE in background as the output
  CL parameters may not be properly updated. 
  </p>
  <!-- EndSection:   'BUGS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  -->
  
