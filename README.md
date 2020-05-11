# Simple Open EtherCAT Master Library
[![Build Status](https://travis-ci.org/OpenEtherCATsociety/SOEM.svg?branch=master)](https://travis-ci.org/OpenEtherCATsociety/SOEM)
[![Build status](https://ci.appveyor.com/api/projects/status/bqgirjsxog9k1odf?svg=true)](https://ci.appveyor.com/project/hefloryd/soem-5kq8b)

BUILDING
========


Prerequisites for all platforms
-------------------------------

 * CMake 2.8.0 or later


Windows (Visual Studio)
-----------------------

 * Start a Visual Studio command prompt then:
   * `mkdir build`
   * `cd build`
   * `cmake .. -G "NMake Makefiles"`
   * `nmake`

Linux & macOS
--------------

   * `mkdir build`
   * `cd build`
   * `cmake ..`
   * `make`

ERIKA Enterprise RTOS
---------------------

 * Refer to http://www.erika-enterprise.com/wiki/index.php?title=EtherCAT_Master

Documentation
-------------

See https://openethercatsociety.github.io/doc/soem/


Want to contribute to SOEM or SOES?
-----------------------------------

If you want to contribute to SOEM or SOES you will need to sign a Contributor
License Agreement and send it to us either by e-mail or by physical mail. More
information is available in the [PDF](http://openethercatsociety.github.io/cla/cla_soem_soes.pdf).

Running/Debugging
-----------------

* Recommended VSC extension: CMake, CMake Tools

* Allow **running** on Linux without requiring root privileges: From [link](http://squidarth.com/networking/systems/rc/2018/05/28/using-raw-sockets.html) granting capabilities to an executable (e.g. simple_test)

```sh
sudo setcap cap_net_admin,cap_net_raw=eip simple_test
```

* Enable **debugging** on Linux using VSC: Create a file *gdb-root* with the following content *pkexec /usr/bin/gdb "$@"* and in *lauch.json* specifiy *"miDebuggerPath": "${workspaceFolder}/gdb-root"*.

Local Development
-----------------

* Setup a virtual network connection (net1) between *vetha1* and *vetha2*

```sh
sudo ip link add vetha1 type veth peer name vetha2
ip link list
#sudo ip link delete vetha1
   +------------+
   |            |
   |  Master A  |
   |            |
   +---#----#---+
       |    | vetha2
vetha1 |    |
       |    +------------------------+
       |                             |
       +-------- <no slaves> --------+
                   (net1)
```
