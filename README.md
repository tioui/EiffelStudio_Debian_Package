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

	bzr dh-make eiffelstudio15.01 15.01.9.6535 PorterPackage_15.01_96535.tar # Using "m" for multiple binary
	cp -rp debian/* eiffelstudio15.01/debian/
	cp -rp patches eiffelstudio15.01/
	bzr add eiffelstudio15.01/patches
	cd eiffelstudio15.01/debian
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
	dput ppa:eiffelstudio-team/ppa eiffelstudio15.01_15.01.9.6535-0ubuntu1~trusty1_source.changes

***

