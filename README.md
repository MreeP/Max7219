# Raspberry PI MAX7219 Words Display

Code that allow you to display words on Max7219 8x8 led module.

## Prerequisites

You will need:
* Raspberry Pi 1b+ or newer
* Raspbian installed on it
* Internet connection
* Max7219 Led module
* 5 **female -> female** jumper wires

## Installing

Firstly you should get the newest version of your system
```
sudo apt-get update && sudo apt-get upgrade -y && sudo apt-get dist-upgrade -y
```
Then install python-dev and python-pip
```
sudo apt-get install python3-dev python3-pip
```
If pip is already installed you should run the following command to get it's newest version!!!
```
sudo pip3 install --upgrade pip
```
Next step is installing additional python libraries.
Max7219
```
sudo pip3 install max7219
```
Spidev
```
sudo pip3 install spidev
```
Luma
```
sudo pip3 install luma.led_matrix
```
Then we are ready to clone code from GitHub.
Navigate to your destination and execute the command below.
```
sudo git clone https://github.com/MrRoot-6/Max7219.git
```

## Enabling SPI

By default, we **can't** use SPI communication on Raspbian. 

### raspi-config:
To enable SPI from the terminal run ```sudo raspi-config``` select ```Interfacing Options``` then go to ```SPI```
and confirm enabling SPI interface by clicking ```Yes```.

## Checking if SPI is enabled

After enabling SPI it is good to check whether everything works correctly.
To do so type the following command.
```
ls -la /dev/ | grep -i "spi"
```
The output of this command should be similar to this undermentioned.
```
crw-rw----  1 root spi     153,   0 sie  4 00:42 spidev0.0
crw-rw----  1 root spi     153,   1 sie  4 00:42 spidev0.1
```

## Wiring

As you've got everything installed it's time to connect our max7219 module to Raspberry and test it out.

### Max7219 -> Raspberry Pi Physical Pins
* VCC -> Pin 2  (+5V Power)
* GND -> Pin 6  (Ground)
* DIN -> Pin 19 (Data In)
* CS  -> Pin 24 (Chip Select)
* CLK -> Pin 23 (Clock)

## Testing

**We recomend using python3**

Now your Max7219 is set up so you can run the test.
Go to the folder you've cloned code to and do the following.
```bash
sudo python3 led8x8.py -w test -t 0.5 -r 1
```
## Syntax

### sudo python3 led8x8.py \<arguments>
#### Arguments:
* -w \<word> **TYPE:String**
* -t \<time> **TYPE:Int or Float**
* -r \<rotation> **TYPE:Int from 0 to 3**
* -s \<separator> **TYPE:Float or Int**

Code requires only -w argument to run

## Built with [Python3](https://www.python.org/)
Libraries used:
* [Luma](https://luma-led-matrix.readthedocs.io/)
* [Time](https://docs.python.org/2/library/time.html)
* [Getopt](https://docs.python.org/2/library/getopt.html)
* [Sys](https://docs.python.org/2/library/sys.html)

## License

This project is licensed under the BSD 2-Clause License - see the [LICENSE](LICENSE) file for details

## Author
* [**MrRoot-6**](https://github.com/MrRoot-6)

## Acknowledgments
* [**rm-hull**](https://github.com/rm-hull/luma.led_matrix)
