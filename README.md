# Python 3.4.3 port to RosBE and ReactOS

## Build

*** WARN*** Tested with rosBE for Unix only!

* Clone or extract to <reactos_source>/modules.
* Add remove_definitions(-Werror) and add_subdirectory(ros-python3) to CMakeLists.txt of the modules dir.
* Run RosBE and invoke ninja python3.
Now python3.dll appears in <reactos_source>/output-MinGW-i386/reactos/modules/ros-python3

## Testing

* Install fresh reactOs build
* Install Python 3.4.3 from application manager
* Replace python34.dll in C:\ReactOSsystem32\ to compiled one.

## Limitations

Currently it contains modules to get run. No launcher, zip, pickle, sqlite, multiprocessing, expat and PYDs. Also a lot of warnings during compilation. Tha is why remove_definitions(-Werror) needed.
