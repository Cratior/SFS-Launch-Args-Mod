
# Spaceflight simulator launch argument mods

## what does the mod do
When the mod is instaled many launch arguments can be added to a sfs shortcut to run functions.

## What arguments are there
- `--NoMods` Runs sfs without any mods (includes this mod) - **This is not a security feature it can be bypassed, only acts as a safe mod for fixing problems**
-  `--loadSave="World Name".hub/build/world` launches a world on load instantly, can load either into the hub, build space or the world

## How to run
1. Create a shortcut for Spaceflight Simulator.exe.
2. Right-click the shortcut and select "Properties".
3. In the "Target" field, append the following:
   "C:\Users\Path\To\SpaceFlight Simulator\Spaceflight Simulator.exe" --loadSave="Test".world
   Replace "C:\Users\Path\To\SpaceFlight Simulator\Spaceflight Simulator.exe" with your actual file path and adjust --loadSave="Test".world to specify your desired argument.

## For Developers Automating Spaceflight Simulator Startup on build

To automatically start Spaceflight Simulator when building a mod project, follow these steps:

1. Navigate to your project's properties. <br>
  ![image](https://github.com/Cratior/SFS-Launch-Args-Mod/assets/55932656/82bd2c3f-00d1-4420-9fae-cfcd171d5502)

2. Add the following script to the build events. **Note: Use this script only if you understand its purpose.**
   ```bat
   move "$(TargetDir)##MODFILENAME##" "##OUTPUT PATH##"
   tasklist /FI "IMAGENAME eq Spaceflight Simulator.exe" 2>NUL | find /I /N "Spaceflight Simulator.exe">NUL
   if "%ERRORLEVEL%"=="0" taskkill /IM "Spaceflight Simulator.exe" /F

   start "" "##SFS .exe FILE PATH##"
   ```
   <br>
![Screenshot 2024-06-30 191724](https://github.com/Cratior/SFS-Launch-Args-Mod/assets/55932656/db4b8814-232f-41b4-ae21-04c21e272fa5)


   Replace ##MODFILENAME##, ##OUTPUT PATH##, and ##SFS .exe FILE PATH## with the respective values:
   - ##MODFILENAME##: Name of your mod file (e.g., MyMod.dll)
   - ##OUTPUT PATH##: Path to your mods folder (e.g., C:\Path\To\Mods\)
   - ##SFS .exe FILE PATH##: Path to Spaceflight Simulator.exe (e.g., C:\Path\To\Spaceflight Simulator.exe)

Note: This setup might currently produce an error, but it's a functional method I personally use for my projects.

Feel free to adjust paths and filenames according to your specific setup and preferences.
