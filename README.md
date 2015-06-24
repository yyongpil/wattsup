# wattsup.py
## A logging program for Watts Up? .Net/Pro meters.
`wattsup.py` is a simple python program for logging Watts Up? .Net/Pro meter values.

## Requirements
* Watts Up? .Net or Pro meters connected using USB (<https://www.wattsupmeters.com>)
* Linux or Mac OS X
* Python 2.7 (Python 3 is not supported yet)
* PySerial (<http://pyserial.sourceforge.net/>)
* FTDI drivers for Mac OS X (<http://www.ftdichip.com/Drivers/VCP.htm>)

## How to Run
### Mac OS X
__See options:__

	$ ./wattsup.py -h
or

	$ python2.7 ./wattsup.py -h

__Realtime external logging with the following options:__

* Read values from the meters `/dev/tty.usbserial-AB1234CD` and `/dev/tty.usbserial-EF5678GH` 
* Log for `10` minutes
* Set the meter-reading interval to `1` second
* Save as files with the filenames starting with `mylog01`

		$ ./wattsup.py -p /dev/tty.usbserial-AB1234CD /dev/tty.usbserial-EF5678GH -t 10 -i 1 -o mylog01
	
All the read values will be saved in `mylog01-tty.usbserial-AB1234CD.csv` and `mylog01-tty.usbserial-EF5678GH.csv`.

__Clear the internal memory of the meter and start internal logging:__

	$ ./wattsup.py -p /dev/tty.usbserial-AB1234CD -c
	
or just (when all the usbserial devices are Watts Up! meters)

	$ ./wattsup.py -c

__Fetch the saved data from the internal memory :__

	$ ./wattsup.py -p /dev/tty.usbserial-AB1234CD -f
	
or just (when all the usbserial devices are Watts Up! meters)

	$ ./wattsup.py -f

### Linux
The user has to be a member of `dialout` group in order to access `/dev/ttyUSBx`.
To add the user account to the `dialout` group,

	# adduser myuser dialout

or

	$ sudo adduser myuser dialout
	
Everything else is the same as Mac OS X.