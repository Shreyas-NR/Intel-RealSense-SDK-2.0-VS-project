# Intel-RealSense-SDK-2.0-VS-project
C, C++, and Python scripts based on librealsense SDK 2.0 to talk the RealSense Camera

## Required Tools:
1. Intel RealSense D455.
2. Intel RealSense SDK 2.0.
3. Visual Studio Community.

---

## Steps
1. Download the Intel RealSense SDK 2.0 from [here](https://github.com/IntelRealSense/librealsense/releases/tag/v2.53.1) and install in the default installation directory ***C:\Program Files (x86)\Intel RealSense SDK 2.0***.
2. Connect the Camera to USB 3.0 compatible port.
3. Download and install Visual Studio 2022 Community edition with the following settings,

![image](https://user-images.githubusercontent.com/58805235/219552712-f14e609e-3e21-43f9-959a-50e1904e23c3.png)

4. Create a empty project.
5. Go to **View -> other windows -> property manager**
6. In property manager, right click your project, add existing property sheet
Browse to where you installed intel realsense sdk. In my case, is C:\Program Files (x86)\Intel RealSense SDK 2.0
Add the file **"intel.realsense.props"** Project Property File.
7. Create a new Source file **"Source.cpp"** to the Source Files of the project, Paste the source code from [here](https://github.com/Shreyas-NR/Intel-RealSense-SDK-2.0.-VS-project/blob/master/Source.cpp).
8. Add **example.h, example.hpp, example-imgui.hpp, example-utils.hpp** to the Header Files of the project.
9. In Project Properties
    1. VC++ Directories<br>
        Update the Library Directories with the following path ***C:\Program Files %28x86%29\Intel RealSense SDK 2.0\lib\x64;$(LibraryPath)***
	
    2. 	C/C++<br>
        **General**-> Update the Additional Include Directories with the following path	***C:\Program Files %28x86%29\Intel RealSense SDK 2.0\third-party\glfw-imgui\include\GLFW;C:\Program Files %28x86%29\Intel RealSense SDK 2.0\include;%(AdditionalIncludeDirectories)***
	
    3. Linker<br>
        **General**-> Update the Additional Library Directories with the following path	***$(librealsenseSDK)\lib\$(PlatformShortName);%(AdditionalLibraryDirectories)***<br>
        **Input**-> Update the Additional Dependencies with the following path ***C:\Program Files (x86)\Intel RealSense SDK 2.0\lib\x64\realsense2.lib;%(AdditionalDependencies)***<br>
        **System**-> SubSystem Type = ***Console (/SUBSYSTEM:CONSOLE)***
	
    4. Build Events
	      **Post-Build Event**->
	      Update the Command Line with the following command
	      ***xcopy /y "C:\Program Files (x86)\Intel RealSense SDK 2.0\bin\x64\realsense2.dll"  "$(OutDir)"***
	
10. Build the Solution and click execute. (make sure you have connected your Camera to the USB 3.0 port)<br>That's it! you have now successfully created your custom project with Intel RealSense SDK. 
