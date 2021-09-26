.. _gripes:

gripes: Send suggestions, complaints, etc. to the system
========================================================

**Package: system**

.. raw:: html

  <section id="s_usage">
  <h3>Usage</h3>
  <p>
  gripes subject
  </p>
  </section>
  <section id="s_parameters">
  <h3>Parameters</h3>
  <dl id="l_subject">
  <dt><b>subject</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='subject' Line='subject' -->
  <dd>The subject of the gripe; any string, usually the name of package or task
  to which the gripe refers.
  </dd>
  </dl>
  <dl id="l_verbose">
  <dt><b>verbose = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes' -->
  <dd>Print instructions on how to enter text whenever <i>gripes</i> is run.
  </dd>
  </dl>
  </section>
  <section id="s_description">
  <h3>Description</h3>
  <p>
  The <b>gripes</b> task is used to post complaints, suggestions, or any other
  formal or informal comments regarding the IRAF system.  Each gripe is
  appended to the system gripesfile <span style="font-family: monospace;">"hlib$gripesfile"</span>, a public file which
  can be read by anyone by simply typing <span style="font-family: monospace;">"page hlib$gripesfile"</span> within IRAF.
  Use <b>tail</b> instead of <b>page</b> to read only the most recent gripes.
  A copy of each gripe is also sent immediately to one or members of the IRAF
  group via electronic mail, to insure that the gripe gets read promptly (this
  feature is not available on all host systems).
  </p>
  <p>
  Gripe text is read from the standard input.  A line containing only a period
  terminates the gripe, as does the end of file character (e.g., &lt;ctrl/z&gt;).
  If the line containing only <span style="font-family: monospace;">"~e"</span> is entered a text editor will be called up
  to edit the text of the gripe.
  </p>
  <p>
  Users are encouraged to use the gripe facility at will.  Be assured that
  someone will at least read the gripe, although there is no guarantee that
  any action will be taken.  In many cases there will be no response from the
  system, but nonetheless the gripe will be seen and it may well influence
  the direction in which the system evolves.  Do not avoid posting gripes for 
  fear that you do not understand something about the system; if enough users
  find some aspect of the system or a program confusing then that is more
  than sufficient reason for a gripe.
  </p>
  </section>
  <section id="s_examples">
  <h3>Examples</h3>
  <p>
  1.  The user has discovered some nasty features of the <i>imdelete</i> task
  and enters the following gripe.  Note the use of the <span style="font-family: monospace;">"."</span> to terminate
  the text.
  </p>
  <div class="highlight-default-notranslate"><pre>
  cl&gt; gripe
  Subject: image deletion
  Enter text of gripe.  Type &lt;eof&gt; or <span style="font-family: monospace;">'.'</span> to quit:
  
  IMDEL * will delete non image files as well as images!
  It should be possible to delete images with the normal
  DELETE command.
  cl&gt;
  </pre></div>
  </section>
  <section id="s_bugs">
  <h3>Bugs</h3>
  <p>
  There is currently no provision for communicating gripes from a remote site
  back to the site that wrote the software, unless some person manually mails
  a gripe (or the accumulated gripesfile).
  </p>
  </section>
  <section id="s_see_also">
  <h3>See also</h3>
  <p>
  news
  </p>
  
  </section>
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  -->
  
