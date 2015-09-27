EiffelStudio Debian package
===========================



Building the package
--------------------

  * I use Linux Ubuntu to build the package.
  * First download the EiffelStudio PorterPackage from http://sourceforge.net/projects/eiffelstudio/files/ .
  * Install packages packaging-dev and dh-make
  * Be sure that the Bazaar (command bzr) is correctly set. See http://developer.ubuntu.com/packaging/html/getting-set-up.html#configure-bazaar .
  * Use the following command line to build :

***

	bzr dh-make eiffelstudio15.08 15.08.9.7862 PorterPackage_15.08_97862.tar # Using "m" for multiple binary
	cp -rp debian/* eiffelstudio15.08/debian/
	cp -rp patches eiffelstudio15.08/
	bzr add eiffelstudio15.08/patches
	cd eiffelstudio15.08/debian
	rm *.ex *.EX
	bzr add postinst
	bzr add prerm
	bzr builddeb -- -us -uc

***

To send to PPA
--------------

***

	bzr builddeb -S # Changing the changelog file to send in another series (precise, trusty, etc.)
	cd ../../build-area
	dput ppa:eiffelstudio-team/ppa eiffelstudio15.08_15.08.9.7862-0ubuntu1~trusty1_source.changes

***

