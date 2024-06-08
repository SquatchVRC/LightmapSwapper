# LightmapSwapper
This package contains scripts and prefabs that allow for dynamic switching of baked lightmaps and reflection probes during runtime for VRChat worlds. Built for SDK 3.0 and Unity 2022.
## Install Guide
1. Download and import the .unitypackage found in the [release](https://github.com/SquatchVRC/LightmapSwapper/releases/tag/Release) tab.
   
2. In the ```Prefabs``` folder add the "LightmapManager" prefab to your scene.
   
3. In the Inspector right-click "LightmapManager" > Prefab > Unpack Completely. !["LightmapManager" > Prefab > Unpack Completely](https://github.com/SquatchVRC/LightmapSwapper/blob/main/images/unpack.png)
   
4. In the ```Prefabs``` folder add a "LightmapHolder" per lighting scene you want. For example, if you want day and night lighting for your world, add 2 of the "LightmapHolder".
   
5. For each "LightmapHolder", add the lightmaps associated with the respective lighting. ![Setting Lightmaps](https://github.com/SquatchVRC/LightmapSwapper/blob/main/images/SettingLightmaps.png)
   
6. In "LightmapManager", set the ```Light Map Holders``` array length to the number of lightmap holders you have, then drag the holders into the array. Note the order the holders are in the array is the order they will cycle through.
  
![Assign the LightmapHolders](https://github.com/SquatchVRC/LightmapSwapper/blob/main/images/AssigningLightmaps.png)
   
7. If you would like to use the included lightswitch, in the ```Prefabs``` folder add the "Lightswitch" prefab to your scene.
    
8. Expand the "Lightswitch" object and set a reference to the "LightmapManager" object on both the "PC_Switch" object and the "VR_Switch" object.
  
![Assigning the manager on both objects](https://github.com/SquatchVRC/LightmapSwapper/blob/main/images/PCSwitchManager.png) ![Assigning the manager on both objects](https://github.com/SquatchVRC/LightmapSwapper/blob/main/images/VRSwitchManager.png)
    
9. Setup your Reflection Probes. Any reflection probe that you would like to be updated must be set to ```Type: Realtime```, ```Refresh Mode: Via scripting```, ```Time Slicing: Individual Faces```, and set the ```Culling Mask``` to "Default". ![Setting up reflection probe properties](https://github.com/SquatchVRC/LightmapSwapper/blob/main/images/ProbeSetup.png)
    
10. On the "LightmapManager" object, click the button in the Inspector to populate renderers and reflection probes. This grabs any object with a mesh renderer with the ```Contribute GI``` static flag enabled and any active reflection probes set to realtime. ![Populating the manager](https://github.com/SquatchVRC/LightmapSwapper/blob/main/images/ManagerPopulate.png)

## Implementing your own Lightswitch
If you would rather not use the included lightswitch, you can trigger the swapping function by calling `Apply()` on the LightmapManager script.
