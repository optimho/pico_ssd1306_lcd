# pico_ssd1306

make a build directory in the folder 
edit the CmakeList.txt file, make sure that the pico-sdk is in the correct path.

cd into the build directory and run cmake ..
that chould build with out a problem.
If not check the cmake file for the correct paths

also from with in the build directory 
run the following in linux 

    export PICO_SDK_PATH=~/pico/pico-sdk
    
then run 
    
    cmake ..
    
If that all builds then run 

    make 
    
If that works you can try connect your editor to the project.


