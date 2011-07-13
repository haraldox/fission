# Fission

## Intro
Fission is a simple command line tool for managing VMware Fusion VMs.


## Install
    gem install fission


## Usage
### Clone
    fission clone existing_vm new_vm [--start]

If you provide '--start', then the new VM will be powered on after cloning

### Start
    fission start my_vm

Starts the VM

### Status
    fission status

Displays the status (running or not) of all of the VMs found

### Stop
    fission stop my_vm

Stops the VM

### Suspend
    fission suspend my_vm

Suspends the VM

### Help
    fission -h

or just

    fission


## Config
By default, fission will use the default VMware Fusion VM directory
(~/Documents/Virtual Machines.localized/) when cloning.  If you want to use a
different directory, you can set this in a config file.

The config file needs to be in yaml format and live at '~/.fissionrc'

    $cat ~/.fissionrc
    ---
    vm_dir: "/vm"


## Other Notable Info
The name of the VM used in the previous examples should be the directory name 
of the VM minus the '.vmwarevm' extension.  Typically the VM name and the 
directory name are the same.

As of now, VMware Fusion doesn't provide an easy, out of
the box, way to modify the personality (hostname, ip, etc.) of a VM.  Because of
this, a clone created by fission is an _exact_ copy of the original (including
hostname, ip address, etc.).  Most likely, this isn't what you want.

One approach is to create a VM which will act as a template.  Create the VM with
the desired install method (ideally with easy install) and settings, but do not
power on the VM.  You can then create clones from this VM 'template'.  When you 
power on the clone, it will start the OS install process (and assign a new ip, etc.).


## Contribute
* Fork the project
* Make your feature addition or bug fix (with tests) in a topic branch
* Bonus points for not mucking with the gemspec or version
* Send a pull request and I'll get it integrated


## License
See LICENSE