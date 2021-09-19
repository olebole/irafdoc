.. _imdelete:

imdelete: Delete a list of images
=================================

**Package: imutil**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  imdelete -- delete a list of images
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  imdelete images
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>images</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='images' Line='images' -->
  <dd>List of images to be deleted.
  </dd>
  </dl>
  <dl>
  <dt><b>go_ahead </b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='go_ahead' Line='go_ahead ' -->
  <dd>Delete the image?
  </dd>
  </dl>
  <dl>
  <dt><b>verify = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='verify' Line='verify = no' -->
  <dd>Verify the delete operation for each image.
  </dd>
  </dl>
  <dl>
  <dt><b>default_action = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='default_action' Line='default_action = yes' -->
  <dd>The default action for the verify query.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  IMDELETE takes as input a list of IRAF images specified by <i>images</i> and
  deletes both the header and pixel files. In <i>verify</i> mode IMDELETE
  queries the user for the appropriate action to be taken for each IRAF image.
  </p>
  <p>
  If the <i>images</i> parameter is a URL, it will be accessed and put into 
  the file cache, then immediately deleted.  To simply remove a file from
  the cache, use the <i>fcache</i> command instead.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Delete a list of images
  </p>
  <pre>
      cl&gt; imdelete fits*
  </pre>
  <p>
  2. Delete a list of images using verify
  </p>
  <pre>
      cl&gt; imdel fits* ver+
      cl&gt; Delete file <i>'fits1'</i> ? (yes): yes
      cl&gt; Delete file <i>'fits2'</i> ? (yes): yes
      cl&gt; Delete file <i>'fits3'</i> ? (yes): yes
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Time requirements</h3>
  <!-- BeginSection: 'TIME REQUIREMENTS' -->
  <!-- EndSection:   'TIME REQUIREMENTS' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <!-- EndSection:   'BUGS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  imcopy, fcache
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  -->
  
