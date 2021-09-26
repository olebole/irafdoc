.. _news:

news: Page through the system news file
=======================================

**Package: system**

.. raw:: html

  <section id="s_usage">
  <h3>Usage</h3>
  <p>
  news
  </p>
  </section>
  <section id="s_description">
  <h3>Description</h3>
  <p>
  The <i>news</i> task uses the standard IRAF file pager to review a formatted
  summary of the system revisions for the version of IRAF being run.
  The revisions summaries for older versions of the system are also provided:
  use the <i>N</i> and <i>P</i> pager keys to display the next or previous
  system revisions summary.  The revisions summary is given in the file
  <span style="font-family: monospace;">"doc$newsfile"</span>.
  </p>
  <p>
  For reasons of brevity, only the revisions summary is printed.  For detailed
  information on the revisions made to a particular science package, type
  </p>
  <div class="highlight-default-notranslate"><pre>
  cl&gt; help &lt;pkg&gt;.revisions op=sys
  </pre></div>
  <p>
  where <span style="font-family: monospace;">"pkg"</span> is the name of the CL package for which revisions information
  is desired.  For detailed information on the revisions to the system
  software and programming interfaces, examine the system notes file,
  given in the file <span style="font-family: monospace;">"notes.*"</span> in the directory <span style="font-family: monospace;">"iraf$local"</span>.  The system
  notes files for older versions of the system will be found in the <span style="font-family: monospace;">"doc"</span>
  directory.
  </p>
  </section>
  <section id="s_bugs">
  <h3>Bugs</h3>
  <p>
  The revisions summary is often lengthy and may be easier to read if a
  printed copy is made.
  </p>
  <p>
  Redirecting the output of <i>news</i>, e.g., to <i>lprint</i>, doesn't work
  at present.
  </p>
  </section>
  <section id="s_examples">
  <h3>Examples</h3>
  <p>
  1. Page the revisions summary for the current IRAF release.
  </p>
  <div class="highlight-default-notranslate"><pre>
  cl&gt; news
  </pre></div>
  <p>
  2. Print the revisions summary.
  </p>
  <div class="highlight-default-notranslate"><pre>
  cl&gt; lprint doc$newsfile
  </pre></div>
  <p>
  3. Page the system notes file.  Anyone who develops software for IRAF
  should review this file with each new release, to see what has changed.
  Documentation for new system facilities is often given in the system
  notesfile.
  </p>
  <div class="highlight-default-notranslate"><pre>
  cl&gt; page iraf$local/notes.*
  </pre></div>
  <p>
  4. Review the revisions summary for the IMAGES package.
  </p>
  <div class="highlight-default-notranslate"><pre>
  cl&gt; phelp images.revisions op=sys
  </pre></div>
  </section>
  <section id="s_see_also">
  <h3>See also</h3>
  <p>
  help, phelp, page
  </p>
  
  </section>
  
  <!-- Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'BUGS' 'EXAMPLES' 'SEE ALSO'  -->
  
