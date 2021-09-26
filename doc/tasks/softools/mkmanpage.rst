.. _mkmanpage:

mkmanpage: Make a manual page
=============================

**Package: softools**

.. raw:: html

  <section id="s_usage">
  <h3>Usage</h3>
  <p>
  mkmanage module
  </p>
  </section>
  <section id="s_parameters">
  <h3>Parameters</h3>
  <dl id="l_module">
  <dt><b>module</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='module' Line='module' -->
  <dd>The name of the program to be documented, i.e., the name that will appear at
  the top of the manual page, and the root name of the <span style="font-family: monospace;">".hlp"</span> file to be
  created.
  </dd>
  </dl>
  <dl id="l_clformat">
  <dt><b>clformat = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='clformat' Line='clformat = yes' -->
  <dd>Make a CL format manual page template?
  </dd>
  </dl>
  <dl id="l_cltemplate">
  <dt><b>cltemplate = <span style="font-family: monospace;">"doc$mancl.hlp"</span></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='cltemplate' Line='cltemplate = "doc$mancl.hlp"' -->
  <dd>Filename of the template file for a CL manual page.
  </dd>
  </dl>
  <dl id="l_xtemplate">
  <dt><b>xtemplate = <span style="font-family: monospace;">"doc$manx.hlp"</span></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='xtemplate' Line='xtemplate = "doc$manx.hlp"' -->
  <dd>Filename of the template file for a library procedure manual page.
  </dd>
  </dl>
  </section>
  <section id="s_description">
  <h3>Description</h3>
  <p>
  The <i>mkmanpage</i> task is used to create a fill-in-the-blanks type
  template, to be edited to create the manual page for the named help module
  or task.  Depending upon the type of manual page to be created, <i>mkmanpage</i>
  copies the template file to the current directory, creating a new file with
  the name <span style="font-family: monospace;">"module.hlp"</span>, where <i>module</i> is the name entered on the
  command line.  The editor is called up to edit the file and the task exits.
  </p>
  </section>
  <section id="s_examples">
  <h3>Examples</h3>
  <p>
  1. Make a new manual page for task <span style="font-family: monospace;">"page"</span>.
  </p>
  <div class="highlight-default-notranslate"><pre>
  cl&gt; mkmanpage page
  </pre></div>
  <p>
  The task creates a file <span style="font-family: monospace;">"page.hlp"</span> in the current directory, and calls
  up the editor to edit the new file.
  </p>
  </section>
  <section id="s_see_also">
  <h3>See also</h3>
  <p>
  mkhelpdb, help, lroff
  </p>
  
  </section>
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  -->
  
