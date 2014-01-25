nwfermi
=======

nwfermi is a input driver for NextWindow touchscreens. I just bought a new pc and I intend provide a working version of its touchscreen driver..

## Installation

This instruction hopefully results in a single-touch-screen.

Do:
`git clone git@github.com:DadaMonad/nwfermi.git`

### nwfermi

fermi is a kernel module for NextWindow devices, which is originated from [here](https://launchpad.net/nwfermi/) 

Do `lsusb`:

```
...
Bus 002 Device 003: ID 1926:1843 NextWindow 
...
```

In this case 1926 is the vendor id and 1843 is the product id. There is a chance that fermi doesn't know your product. So you have to add it manually. Move your lazy terminal into the latest version of nwfermi (from my repo) and add it yourself in the nw-fermi.c source file. Just insert it in the fermi_table.
Insert `{ USB_DEVICE(0x1926, 0x006D) },` for vendor id=006D

* install dkms
* copy nwfermi-0.6.x.x to /usr/src/
* dkms build nwfermi/0.6.x.x
* dkms install nwfermi/0.6.x.x
* yay

### nwfermi-daemon

I had to do this. Maybe you can leave this step out.. Me don't know

* install nwfermi-daemon 

start nwfermi-daemon at startup

### xf86-input-nextwindow

evdev xorg driver worked for me too, but it recognizes my touchSCREEN as a touchPAD .. This is why I moved to the older xf86-input-nextwindow. BTW evdev recognized more than one finger ;)

If you are lazy Google this for your distro. Start with 
* [this](http://software.opensuse.org/download.html?project=home%3Adaniel_newton%3Axf86-input-nextwindow&package=xf86-input-nextwindow)
* [this](https://build.opensuse.org/package/show/home:daniel_newton:xf86-input-nextwindow/xf86-input-nextwindow)

and

* [this](https://launchpad.net/~djpnewton/+archive/xf86-input-nextwindow)

Arch provides this in the AUR!



