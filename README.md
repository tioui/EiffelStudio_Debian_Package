EiffelStudio Debian package
===========================



Building the package
--------------------

  * I use Linux Ubuntu to build the package.
  * First download the EiffelStudio PorterPackage from http://sourceforge.net/projects/eiffelstudio/files/ .
  * Install packages packaging-dev and dh-make
  * Be sure that the Bazaar (command bzr) is correctly set. See: http://packaging.ubuntu.com/html/getting-set-up.html .
  * Use the following command line to build :

***

	bzr dh-make eiffelstudio16.05 16.05.9.8814 eiffelstudio-16.05.tar # Using "m" for multiple binary
	cp -rp debian/* eiffelstudio16.05/debian/
	cp -rp patches eiffelstudio16.05/
	bzr add eiffelstudio16.05/patches
	cd eiffelstudio16.05/debian
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
	dput ppa:eiffelstudio-team/ppa eiffelstudio16.05_16.05.9.8814-0ubuntu1~trusty1_source.changes

***

