# cyrun
For the Electra iOS 11 Jailbreaks.

cyrun is comprised of an executable and bash script. It will

* Enable/disable the cycriptListenerTweak dylib file (which loads Cyript and runs a CYListenServer on port 8556)
* Write the App bundleIdentifier or Process Executable Name to the tweak filter plist
* Kill and relaunch the App/Process

It is meant to be used alongside [cycriptListenerTweak](https://github.com/tateu/cycriptListenerTweak).

# INSTALLATION

	# From SSH or terminal as root
	cd ~
	# download https://electrarepo64.coolstar.org/debs/ncurses_6.1_iphoneos-arm.deb
	# download http://apt.saurik.com/debs/readline_6.0-8_iphoneos-arm.deb
	# download http://apt.saurik.com/debs/cycript_0.9.594_iphoneos-arm.deb
	# download http://apt.thebigboss.org/repofiles/cydia/debs2.0/applist_1.5.14_iphoneos-arm.deb
	# download http://www.tateu.net/repo/files/net.tateu.cycriptlistenertweak_1.0.0_iphoneos-arm.deb
	# download http://www.tateu.net/repo/files/net.tateu.cyrun_1.0.1_iphoneos-arm.deb
	dpkg -i ncurses_6.1_iphoneos-arm.deb
	dpkg -i readline_6.0-8_iphoneos-arm.deb
	dpkg -i cycript_0.9.594_iphoneos-arm.deb
	dpkg -i applist_1.5.14_iphoneos-arm.deb
	dpkg -i net.tateu.cycriptlistenertweak_1.0.0_iphoneos-arm.deb
	dpkg -i net.tateu.cyrun_1.0.1_iphoneos-arm.deb

And then you can use the bash script to sign the Cycript binaries with the correct Electra entitlements

	cyrun -s

Then you can load Cycript into SpringBoard. SpringBoard will be terminated and auto restart

	cyrun -n SpringBoard -e

Or you can unload Cycript from SpringBoard. SpringBoard will be terminated and auto restart

	cyrun -n SpringBoard -d

Or you can load and auto unloaded Cycript from the iOS Mail App. Mail will be terminated and auto restart. When you ?exit Cycript, it will be killed and unloaded.

	cyrun -n Mail -e -d

The '-n' command takes an AppName as known by AppList. I believe this is usually the same as the icon name.

You can use a bundleIdentifier instead of an App name with `'-b com.apple.springboard'`

You can also turn off the 'ask to continue' prompts with '-f'

	cyrun -b com.apple.mobilemail -e -d -f