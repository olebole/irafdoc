.. _phelp:

phelp: Paged HELP: collects and pages the output of HELP
========================================================

**Package: system**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  phelp -- page the output of the HELP task
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  phelp template
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <p>
  The <i>phelp</i> parameters are the same as for <i>help</i> except that
  the <i>page</i> and <i>nlpp</i> parameters are omitted.
  </p>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  The <i>phelp</i> task is a front end to <i>help</i> which spools the output
  of <i>help</i> in a scratch file, then calls the file pager <i>page</i> to
  view the output text.  The advantage is that while <i>help</i> pages its
  output, one can only move forward through the output text.  By using
  <i>phelp</i> it is possible to randomly scan the spooled help text, e.g.,
  skipping forward to get a quick overview and then backing up to read the
  details more carefully.  This capability is especially useful when viewing
  large multipage help pages, or when viewing a number of related help pages
  all at once.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Page the help page for the <i>mkpkg</i> task.
  </p>
  <p>
      cl&gt; phelp mkpkg
  </p>
  <p>
  2. View the help pages for all the tasks in the IMAGES package.
  </p>
  <p>
      cl&gt; phelp images.*
  </p>
  <p>
  When viewing multiple help pages as in this last example, note that the
  <span style="font-family: monospace;">'N'</span> and <span style="font-family: monospace;">'P'</span> keystrokes in the pager may be used to move to the next or
  previous help page.  <span style="font-family: monospace;">"."</span> will return to the first help page (the start
  of the spooled help text) and <span style="font-family: monospace;">'G'</span> will skip to the end of file.  Type <span style="font-family: monospace;">'?'</span>
  while in the pager to get a summary of the most often used keystrokes.
  </p>
  <p>
  3. Format and page the Lroff (IRAF HELP) format document <span style="font-family: monospace;">"MWCS.hlp"</span> in
  the system directory <span style="font-family: monospace;">"mwcs"</span>.
  </p>
  <pre>
      cl&gt; cd mwcs
      cl&gt; phelp MWCS.hlp fi+
  </pre>
  <p>
  In this case the text being viewed is not part of the on-line help system,
  but is a technical document describing one of the IRAF programming interfaces.
  Any .hlp file may be viewed in this way.
  </p>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Time requirements</h3>
  <!-- BeginSection: 'TIME REQUIREMENTS' -->
  <p>
  <i>phelp</i> is not quite as fast as <i>help</i> since it must fully format
  the help text into a temporary file before the file can be viewed.  For
  small help pages, or to view only the first few screens of a help page,
  the <i>help</i> task will be faster.
  </p>
  <!-- EndSection:   'TIME REQUIREMENTS' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <!-- EndSection:   'BUGS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  page, help, references
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  -->
  
