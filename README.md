# Arkham Animation Converter
This plugin generates proper root motion tracks for animations extracted from Rocksteady's Batman: Arkham series, allowing them to function properly within Unreal Engine 4
Blender 2.90+ required.

Forked from Enzio Probst's Mixamo converter.

### It can
* convert single .FBX animations if they are previously imported by the user
* Batch convert all input FBX files from a folder to a new location
* Does not currently support the .psa and .psk formats - these should be exported using Gildor's official ActorX Importer for Autodesk 3DS Max.

## Installation
* Download Blender 2.90 from https://www.blender.org/download/
* Download this repository as a ZIP file
* Open up Blender
* Head over to: Edit -> Preferences -> Addons -> Install from File...
* Select the ZIP you downloaded and click 'install from file'
* Click the check box

## Usage
The Addon UI is located in the UI properties panel, which can be opened using the hotkey "N".

### Options: [Use Z] [On Ground]
Only rotation along the Up Axis is transfered to the root
##### Both Enabled (recommended):
A Root bone which stays on ground except for cases when the Hip moves higher than its restpose location
##### Only [Use Z] Enabled:
the root bone can go below the Ground
this will result in wierd behaviour if one Big Collider is used for the Character in Unreal
##### [Use Z] is Disabled
no Vertical motion at all is transfered to the Root and [On Ground] becomes obsolete

#### Options: [Use X] [Use Y]
Those can be disabled to prevent movement of root on groundplane.
Useful if one doesn't want to use root motion for some Animations but still needs to have the same converted rig. If so just disable Use Vertical, Use X and Use Y.

#### Option [Apply Rotation]
Makes sure, that there are no unneeded rotations on the character or its root bone, which would often cause unexpected rotation behaviour in unreal.

#### Option [Apply Scale]
Applies the scale of the character and its rig, so they have scale 1, but doesn't change the actual size of the character.

#### Option [Scale]
Scaling factor for actually resizing your character.

### Experimental Options

#### Option [Restpose Offset]
Offsets the restpose of your rig without offsetting the animation. Can be used to correct for an offset of the restpose that one might have accidentally added during animation editing or retargeting.

#### Option [Knee Offset]
Very kludgy workaround which can result in bones being out of place in animation.
Can be used to fix rotational flickering occuring in some animations after export (seems to be an exporter bug). (mostly observed on legs but can be used on any bones)
It moves the tip joint of given bones by the given vector in the restpose.

#### Option [Foot Bone Workaround]
Workaround which attempts to fix the twisting of the foot bones (specifically, LeftToeBase/ball_l and RightToeBase/ball_r) of certain meshes,
which may appear rotated by 180 degrees after conversion.

### Batch Conversion:
* Here you can specify an Input- and Outputpath for Batchconversion
* the output files will have the same names as the input files, existing files will be overwritten
* The [force overwrite] option is only for the case where Input- and Outputlocation are the same
* If input and output path are set you can press [Batch Convert] to convert all FBX files from source location and save it to target location
* this takes around 10 seconds per file, there is no progress bar yet so be patient
* The source location should only contain FBX files containing skeletons from Arkham franchise titles
* files not ending with .fbx are ignored and can stay in source directory
