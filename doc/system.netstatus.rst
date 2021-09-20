.. _netstatus:

netstatus: Print the status of the local network
================================================

**Package: system**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  netstatus -- print the status of the local network
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  netstatus
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <p>
  None.
  </p>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  <i>Netstatus</i> prints the status of the local network as perceived by the
  system process x_system.e (the network status may differ for each subprocess).
  The status output identifies the local node, lists all nodes in the local
  network, and lists all the aliases (recognized names) for each node.
  A message will be printed if networking is disabled on the local machine.
  The local network is defined by the table files <span style="font-family: monospace;">"dev$hosts"</span>, <span style="font-family: monospace;">"dev$uhosts"</span>,
  and <span style="font-family: monospace;">"dev$hostlogin"</span>.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <pre>
  cl&gt; netstatus
  Local node `draco' (5), default node `draco', 12 nodes in local network
  
      NODE SERVER NREFS STATUS  ALIASES
         1      0     0  00000  aquila vax1 a 1 class1 plot print
         2      0     0  00000  lyra vax2 b 2 class2
         3      0     0  00000  vela vax3 3 v class3
         4      0     0  00000  carina vax5 c 5 class5
         5      0     0  00000  draco vax6 6 d class6 0
         6      0     0  00000  tucana sun1 t
         7      0     0  00000  hydra sun2 h
         8      0     0  00000  mensa pc1 m
         9      0     0  00000  pictor pc2
        10      0     0  00000  octans sun3 o
        11      0     0  00000  pavo mvax1 p
        12      0     0  00000  volans lsi1
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  -->
  
