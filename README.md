PHP Serial
==========

This project was created for a project at my work where a Symfony project needs to communicate to a machine through the COM port on Windows. 
After a long time, surfing the web, I found [PHP-Serial](https://github.com/Xowap/PHP-Serial) made by [Xowap](https://github.com/Xowap).  
However, when I found out that the project wasn't longer maintened and the pull requests weren't accepted, I decided to share some fixes and improvements !
Especially, a Windows fix, a PHP 8.2+ compatibility and a cleaner code (I think so, I don't know, Java is better :P).

I really hope it will help someone !

> Of course, I am not the main author, all credits goes to [Xowap](https://github.com/Xowap).

Example
-------

```php
<?php
include 'PhpSerial.php';

// Let's start the class
$serial = new PhpSerial();

// First we must specify the device. This works on both linux and windows (if
// your linux serial device is /dev/ttyS0 for COM1, etc)
$serial->deviceSet("COM1");

// We can change the baud rate, parity, length, stop bits, flow control
$serial->confBaudRate(2400);
$serial->confParity("none");
$serial->confCharacterLength(8);
$serial->confStopBits(1);
$serial->confFlowControl("none");

// Then we need to open it
$serial->deviceOpen();

// To write into
$serial->sendMessage("Hello !");

// To read
$serial->readLine();
```

State of the project
--------------------

### Bugs

There is **lots** of bugs. I know there is. I just don't know which are they.

### Platform support

* **Linux**: need to be tested !
* **MacOS**: need to be tested !
* **Windows**: it should work, at least on a Windows server, it works :) !

### Concerns

I have a few concerns regarding the behaviour of this code.

* Inter-platform consistency. I seriously doubt that all operations go the same
  way across all platforms.
* Auto-closing the device. There is an auto-close function that is registered
  at PHP shutdown. This sounds quite ridiculous, something has to be done about
  that.
* Use exceptions.

Call for contribution
---------------------

As in all open-source projects, I need people to fit this to their needs and to
contribute back their code.

If you feel like doing any of those, do not hesitate to create an issue or a
pull-request, I'll gladly consider consider it :)
