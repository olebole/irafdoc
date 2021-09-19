.. _news:

news: Page through the system news file
=======================================

**Package: system**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  news -- print the revisions summary for the current IRAF version
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  news
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  The <i>news</i> task uses the standard IRAF file pager to review a formatted
  summary of the system revisions for the version of IRAF being run.
  The revisions summaries for older versions of the system are also provided:
  use the <i>N</i> and <i>P</i> pager keys to display the next or previous
  system revisions summary.  The revisions summary is given in the file
  <tt>"doc$newsfile"</tt>.
  </p>
  <p>
  For reasons of brevity, only the revisions summary is printed.  For detailed
  information on the revisions made to a particular science package, type
  </p>
  <p>
      cl&gt; help &lt;pkg&gt;.revisions op=sys
  </p>
  <p>
  where <tt>"pkg"</tt> is the name of the CL package for which revisions information
  is desired.  For detailed information on the revisions to the system
  software and programming interfaces, examine the system notes file,
  given in the file <tt>"notes.*"</tt> in the directory <tt>"iraf$local"</tt>.  The system
  notes files for older versions of the system will be found in the <tt>"doc"</tt>
  directory.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <p>
  The revisions summary is often lengthy and may be easier to read if a
  printed copy is made.
  </p>
  <p>
  Redirecting the output of <i>news</i>, e.g., to <i>lprint</i>, doesn't work
  at present.
  </p>
  <!-- EndSection:   'BUGS' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Page the revisions summary for the current IRAF release.
  </p>
  <p>
      cl&gt; news
  </p>
  <p>
  2. Print the revisions summary.
  </p>
  <p>
      cl&gt; lprint doc$newsfile
  </p>
  <p>
  3. Page the system notes file.  Anyone who develops software for IRAF
  should review this file with each new release, to see what has changed.
  Documentation for new system facilities is often given in the system
  notesfile.
  </p>
  <p>
      cl&gt; page iraf$local/notes.*
  </p>
  <p>
  4. Review the revisions summary for the IMAGES package.
  </p>
  <p>
      cl&gt; phelp images.revisions op=sys
  </p>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  help, phelp, page
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'BUGS' 'EXAMPLES' 'SEE ALSO'  -->
  
