# PongGameRUST
Ping Pong Game with RUST

The Rust Programming Language
This is the main source code repository for Rust. It contains the compiler, standard library, and documentation.

Quick Start
Read "Installation" from The Book.

Building from Source
Building on *nix
Make sure you have installed the dependencies:

g++ 4.7 or later or clang++ 3.x or later
python 2.7 (but not 3.x)
GNU make 3.81 or later
cmake 3.4.3 or later
curl
git
Clone the source with git:

$ git clone https://github.com/rust-lang/rust.git
$ cd rust
Build and install:

$ git submodule update --init --recursive --progress
$ ./x.py build && sudo ./x.py install
Note: Install locations can be adjusted by copying the config file from ./config.toml.example to ./config.toml, and adjusting the prefix option under [install]. Various other options, such as enabling debug information, are also supported, and are documented in the config file.

When complete, sudo ./x.py install will place several programs into /usr/local/bin: rustc, the Rust compiler, and rustdoc, the API-documentation tool. This install does not include Cargo, Rust's package manager, which you may also want to build.

Building on Windows
There are two prominent ABIs in use on Windows: the native (MSVC) ABI used by Visual Studio, and the GNU ABI used by the GCC toolchain. Which version of Rust you need depends largely on what C/C++ libraries you want to interoperate with: for interop with software produced by Visual Studio use the MSVC build of Rust; for interop with GNU software built using the MinGW/MSYS2 toolchain use the GNU build.

MinGW
MSYS2 can be used to easily build Rust on Windows:

Grab the latest MSYS2 installer and go through the installer.

Run mingw32_shell.bat or mingw64_shell.bat from wherever you installed MSYS2 (i.e. C:\msys64), depending on whether you want 32-bit or 64-bit Rust. (As of the latest version of MSYS2 you have to run msys2_shell.cmd -mingw32 or msys2_shell.cmd -mingw64 from the command line instead)

From this terminal, install the required tools:

# Update package mirrors (may be needed if you have a fresh install of MSYS2)
$ pacman -Sy pacman-mirrors

# Install build tools needed for Rust. If you're building a 32-bit compiler,
# then replace "x86_64" below with "i686". If you've already got git, python,
# or CMake installed and in PATH you can remove them from this list. Note
# that it is important that you do **not** use the 'python2' and 'cmake'
# packages from the 'msys2' subsystem. The build has historically been known
# to fail with these packages.
$ pacman -S git \
            make \
            diffutils \
            tar \
            mingw-w64-x86_64-python2 \
            mingw-w64-x86_64-cmake \
            mingw-w64-x86_64-gcc
Navigate to Rust's source code (or clone it), then build it:

$ ./x.py build && ./x.py install
MSVC
MSVC builds of Rust additionally require an installation of Visual Studio 2013 (or later) so rustc can use its linker. Make sure to check the “C++ tools” option.

With these dependencies installed, you can build the compiler in a cmd.exe shell with:

> python x.py build
Currently, building Rust only works with some known versions of Visual Studio. If you have a more recent version installed the build system doesn't understand then you may need to force rustbuild to use an older version. This can be done by manually calling the appropriate vcvars file before running the bootstrap.

CALL "C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\bin\amd64\vcvars64.bat"
python x.py build
Specifying an ABI
Each specific ABI can also be used from either environment (for example, using the GNU ABI in PowerShell) by using an explicit build triple. The available Windows build triples are:

GNU ABI (using GCC)
i686-pc-windows-gnu
x86_64-pc-windows-gnu
The MSVC ABI
i686-pc-windows-msvc
x86_64-pc-windows-msvc
The build triple can be specified by either specifying --build=<triple> when invoking x.py commands, or by copying the config.toml file (as described in Building From Source), and modifying the build option under the [build] section.
