# Windows Minifilter Rust

My attempt to learn rust and build a windows minifilter kernel as in future rust could be the one replacing c++,
depending as we are looking windows also moving towards rust similar to US based projects.

### Building Driver

Step 1: Need to have proper MSVC setup with WDK to be able to build the driver. Take reference from : https://codentium.com/guides/windows-dev/windows-drivers-in-rust-prerequisites/

Step 2: Change the $VC_BUILD_DIR within the hello-world/Makefile.toml

Step 3: Then run the command

> cargo make sign

### Debugging the Driver

I am assuming you are building driver in Rust that means you are pretty much comfortable with building applications in C++ as till current date Windows Applications / Windows APIs are pretty much supported through C++, If not i will ask you to give it a try to first give a basic hello world driver in C++ this will help you get comfortable with Windows APIs regarding driver and Module Structure of a Windows Driver.

Let's move forward

Step 1: Setup Test Signing on for the machine where you will be testing your driver reference: https://learn.microsoft.com/en-us/windows-hardware/drivers/install/test-signing

Step 2: Install DebugView Sysinternals as this will help you get DebugPrint as drivers don't print in console.

Step 3: Create a service with driver path there:
> sc create example binPath=driver.sys type=kernel

Step 4: `sc start example` this will start the driver and print "Hello, World" within the DebugView

Step 4: `sc stop example` this will help you to stop the driver and will print "Bye" within the DebugView

### References: 
* https://github.com/StephanvanSchaik/windows-kernel-rs
