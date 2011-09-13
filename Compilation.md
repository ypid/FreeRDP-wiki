Install the suggested base dependencies:

    sudo apt-get install build-essential git cmake libssl-dev libx11-dev libxext-dev libxinerama-dev libxcursor-dev libxv-dev libxkbfile-dev libasound2-dev libcups2-dev

Optionally, you can install the following dependencies:
    sudo apt-get install libcunit1-dev libdirectfb-dev xmlto doxygen

Generate makefiles:
    cmake .

If you are using Eclipse, you can also generate Eclipse project files:
    cmake -G "Eclipse CDT4 - Unix Makefiles" .

    cmake -G "Eclipse CDT4 - Unix Makefiles" -DCMAKE_BUILD_TYPE=Debug -DWITH_SSE2=ON .

make