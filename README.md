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

	bzr dh-make eiffelstudio18.01 18.01.10.1424 eiffelstudio-18.01.10.1424.tar # Using "s" for binary
	cp -rp debian/* eiffelstudio18.01/debian/
	cp -rp patches eiffelstudio18.01/
	bzr add eiffelstudio18.01/patches
	cd eiffelstudio18.01/debian
	rm *.ex *.EX
	bzr add postinst
	bzr add prerm
	bzr builddeb -- -us -uc # Test build on local machine (optionnal)

***

To send to PPA
--------------

***

	bzr builddeb -S # Changing the changelog file to send in another series (precise, trusty, etc.)
	cd ../../build-area
	dput ppa:eiffelstudio-team/ppa eiffelstudio18.01_18.01.10.1424-0ubuntu1~trusty1_source.changes

***

To be sure that the package does not resend the orig file, you can pass the -sd the the deb builder.

***

	bzr builddeb -S -- -sd # not for use when generating the first serie

***
