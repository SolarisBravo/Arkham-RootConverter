# Batman: Arkham - Root Motion Converter
This plugin generates and bakes proper root motion tracks for animations extracted from Rocksteady's Batman: Arkham series, allowing them to function properly within Unreal Engine 4.
Blender 2.90+ is required.

Forked from Enzio Probst's Mixamo converter.

## Notes
* If you're having issues where the mesh appears "squished", make sure you run the base mesh through my converter.
* Inside UE4, *always* set "Root Motion Root Lock" to "Anim First Frame".

## Installation
* Download Blender 2.90 from https://www.blender.org/download/
* Download this repository as a ZIP file
* Open up Blender
* Head over to: Edit -> Preferences -> Addons -> Install from File...
* Select the ZIP you downloaded and click 'install from file'
* Click the check box

## Usage
The Addon UI is located in the UI properties panel, which can be opened using the hotkey "N".

## Options: 

#### [On Ground]:
Only rotation along the Up Axis is transfered to the root

#### [Use Z]:
Enable for jumping/climbing/anything with a vertical dimension - disable this if you encounter issues with characters dropping below the floor or floating.

#### [Use X] [Use Y]:
Those can be disabled to prevent movement of root on groundplane.
Useful if one doesn't want to use root motion for some Animations but still needs to have the same converted rig. If so just disable Use Vertical, Use X and Use Y.

#### [Apply Rotation]:
Makes sure, that there are no unneeded rotations on the character or its root bone, which would often cause unexpected rotation behaviour in unreal.

#### [Apply Scale]:
Applies the scale of the character and its rig - not reccomended, causes distortion with umodified Arkham models.


## Batch Conversion:
* Here you can specify an Input- and Outputpath for Batchconversion
* the output files will have the same names as the input files, existing files will be overwritten
* The [force overwrite] option is only for the case where Input- and Outputlocation are the same
* If input and output path are set you can press [Batch Convert] to convert all FBX files from source location and save it to target location
* this takes around 10 seconds per file, there is no progress bar yet so be patient
* The source location should only contain FBX files containing skeletons from Arkham franchise titles
* files not ending with .fbx are ignored and can stay in source directory
