# Stardust upgrade guide

## Important Note for updating to versions 0.8 and over.

### Add GLTF Shaders to graphics settings.
In this version we changed the supported file format to .glb and because of that we updated the graphics settings.

So make sure you double check your graphics settings by going to Edit -> Project settings -> Graphics and scrolling to **always included shaders** and check if you have 4 slots with GLTF Utilities shaders added. If not follow these steps:

To ensure that Unity includes the GLTFUtility shaders in builds, you must add these shaders to the 'Always Included Shaders' list.

1. Open Edit -> Project Settings
2. Open Graphics
3. Scroll to Always Included Shaders
4. Under Size, increase the value by 4 and hit Enter.
5. In the Project panel, navigate to Packages/GLTFUtility/Materials/Built-in.
6. In this directory are 4 .shader files.
7. Drag and drop each of the 4 files into one of the 4 newly created rows in Always Included 
Shaders.

![GLTF Shaders](_img/GLTFShaders.png ':size=80%')

### Delete Plastic SCM Package
Check and remove the Version Control - Plastic SCM package in the package manager.
Open the Package manager by going to Window -> Package manager. Make sure you're checking packages in project and look for Version Control and remove the package if present.

![Version Control](_img/versionControl.png ':size=100%')


## Upgrade from 0.2/0.3 to 0.5

- Update to Unity 2020.2.x
- Update to ARFoundation 4.1.5 (Unity package)
- Update to AR subsystems 4.1.5 (Unity package)
- Update to Unity ARKit plugin 4.1.5 (Unity package)
- Update to Unity ARCore XR plugin 4.1.5 (Unity package)

### MapRelocationManager major change

- **MatchingPosition** has been renamed to **RelocationResults**
- **MapRelocationManager** __onPositionFound__ event now returns 2 objects: **RelocationResults** and **CoordinateSystem**

## Upgrade from 0.1x to 0.2

### Before importing the package
- Delete the **hobodream-sdk** from your project

### After importing the package
- You can delete the old **StardustComponents** and **StardustComponentsNoAutoLogin** from your project.
- Import the prefab **StardustComponents** from the new SDK in your scene.
- Import the prefab **HobodreamComponents** from the new SDK in your scene.
- Get your developer api key from the [dashboard](https://stardust.neogoma.com/profile).
- Fill the API key into the __Stardust SDK__ script of the **StardustComponents** prefab.
- For better naming conventions **ALL** Uunity events have been renamed with the "on" prefix for example __dataCapturedSucessfully__ has been renamed to __onDataCapturedSucessfully__. Just rename all your event refrences with the prefix "on"

## Updating with a newly released package

In order to update your sdk to a newer release version all you have to do is download the new release version package and import it into unity. You don't need to delete the previous package as Unity replaces only the files that changed.

### Downloading the latest release package

- Go over to our SDK repository [releases](https://github.com/Neogoma/stardust-SDK/releases/latest).
- Click on the latest **.unitypackage** file to download the unity package.

![releases Download](_img/releases.png)

- Then import the package into your Unity project.
- Click "All" and "Import" Unity should replace any files with changes or add new files to the existing package.

![Importing Package](_img/UpdatingPackage.jpg ':size=50%')


### Troubleshooting 

If you're having issues with updating your package or you're using an older version of the package it's recommended that you delete the **Neogoma** folder entirely from your project and then import the package.
