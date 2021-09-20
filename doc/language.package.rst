.. _package:

package: Define a new package, or print the current package names
=================================================================

**Package: language**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  package -- define a new package
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  package	pkgname
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>pkgname</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='pkgname' Line='pkgname' -->
  <dd>The name of the new package to be created.  If called with no arguments,
  <i>package</i> lists the currently defined packages in task search order.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  The <i>package</i> task creates a new package.
  The newly defined package becomes the current package, and the prompt
  is changed to use the first two characters of the package name.
  The package command does not define any tasks within the package, that
  is done by subsequent <i>task</i> declarations.  Subsequent <i>task</i>
  declarations will add tasks to the task list for the new package.
  </p>
  <p>
  The new package remains the <span style="font-family: monospace;">"current package"</span> until another <i>package</i>
  command is entered, or until the task in which the package command was
  entered is terminated.
  Normally <i>package</i> will be used at the beginning of a script to define
  the package name.  It will be followed by one or more task definitions,
  and then by a <i>cl</i> or <i>clbye</i> to interpret user commands,
  until the command <i>bye</i> is entered by the user, at which time the
  package script task terminates, discarding the package and any associated
  definitions.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. The use of <i>package</i> in a package script task.
  </p>
  <pre>
  	package lists
  
  	set	lists		= "pkg$lists/"
  
  	task	table,
  		tokens,
  		unique,
  		lintran,
  		columns,
  		words		= "lists$x_lists.e"
  
  	task	$gcursor	= "lists$gcursor.cl"
  	task	$imcursor	= "lists$imcursor.cl"
  	task	average		= "lists$average.cl"
  
  	clbye()
  </pre>
  <p>
  2. List the currently defined packages in the order in which they will
  be searched for tasks.
  </p>
  <pre>
  	cl&gt; pack
  	clpackage
  	language
  	user
  	system
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <p>
  All active packages must have unique names.  To eliminate the possibility
  of parameter file name collisions in UPARM, the three character string
  formed by concatenating the first two and final characters of the package
  name should be unique.
  </p>
  <!-- EndSection:   'BUGS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  task, redefine
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  -->
  
