http://blog.petrockblock.com/forums/topic/raspbian-retropie-xbmc/
run retropi and xbmc


http://lifehacker.com/5929913/build-a-xbmc-media-center-with-a-35-raspberry-pi
xbmc setup

http://supernintendopi.wordpress.com/
retro pi install guide




ssh pi@10.0.0.14

Once I removed my keyboard, reboot with:

		ssh pi@10.0.0.14
		sudo reboot

Boot up from command line:
		cd
		emulationstation

Edit roms.  I commented out apple][ and a few others, changed order.
		vim .emulationstation/es_systems.cfg

Edit configs
		vim ~/RetroPi/configs/all/retroarch.cfg

Configure keys
		~/RetroPie/emulators/RetroArch/tools/retroarch-joyconfig >> ~/RetroPie/configs/all/retroarch.cfg




Roms
	Sync snes roms
			rsync -v *.smc pi@10.0.0.14:/home/pi/RetroPie/roms/snes/

	Sync nes roms
			rsync -v *.nes pi@10.0.0.14:/home/pi/RetroPie/roms/nes/

	Patch mario adventure rom
		Download patch files
		Download Patch Program
				http://projects.sappharad.com/tools/multipatch.html

			cd nes
			cp Super\ Mario\ Bros.\ 3.nes _Mario3Adventure.nes
			# Do patch in the gui
			rsync -v -d --delete *.nes pi@10.0.0.14:/home/pi/RetroPie/roms/nes/

