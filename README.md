# How to install on Windows
- You should use MSYS2 after it is installed you would use it in x64 mode.
- Upgrade package list.
  ```
   pacman -Syu
   pacman -Su
   ```
- Install dependencies.
  ```
  pacman -S mingw-w64-x86_64-toolchain git make libtool pkg-config autoconf automake texinfo mingw-w64-x86_64-libusb mingw-w64-x86_64-hidapi
  ```
- Clone the repository and build it.
  ```
  $ git clone https://github.com/raspberrypi/openocd.git --branch rp2040 --depth=1
  $ cd openocd
  $ ./bootstrap
  $ ./configure --disable-werror --enable-cmsis-dap
  $ make -j4
  ```
- Finally run your openocd server.
  ```
  src/openocd -f interface/cmsis-dap.cfg -c "adapter speed 5000" -f target/rp2040.cfg -s tcl
  ```
- Connect GDB to test.
  ```
  target remote localhost:3333
  ```