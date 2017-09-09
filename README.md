Experimental Development Envirnoment for Internet-in-a-Box

Requirements:

 * git
 * vagrant +> 2
 * Vbox (with virtualization support)
 * IDE (Recommend Atom.io with ansible lint and line indents)

Usage:

  * Git checkout submodules recursively (If you would like, you can change the git push settings)
      git clone --recursive [URL to Git repo]


  * vagrant up  (exports your local git checkouts to /opt/iiab/ You need plenty of disk space)
  * vagrant ssh  (hack, hack, hack)
  * vagrant halt
  * commit your code and push away!
