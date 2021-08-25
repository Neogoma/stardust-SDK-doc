# Provide device intrisics

Almost there! Now that intrinsics and camera images are dispatched the only info we're missing is the position!

## Create a class to provide intrisics
You need to create a class that will implement ```IDeviceLocationProvider```. Here is an example of an implementation using the main camera to represent the device.

```cs

using com.Neogoma.Stardust.API;
using com.Neogoma.Stardust.Datamodel;
using UnityEngine;

public class CustomPositionProvider : IDeviceLocationProvider
{
    private CoordinateSystem system = new CoordinateSystem();
    private Transform mainCamera;


    public CustomPositionProvider()
    {
        mainCamera = Camera.main.transform;
    }

  
    public Vector3 GetPosition()
    {
        //if you're not using the main camera position then calculate the position of your device and return it
        return mainCamera.position;
    }

    public Quaternion GetRotation()
    {

        //if you're not using the main camera position then calculate the rotation of your device and return it
        return mainCamera.rotation;
    }


    public CoordinateSystem GetCurrentCoordinateSystem()
    {
        return system;
    }


    public Vector3 GetRight()
    {
        return system.Right;
    }

    
    public Vector3 GetForward()
    {
        return system.Forward;
    }

   

    public Vector3 GetUp()
    {
        return system.Up;
    }

    public void UpdateCoordinateSystem(CoordinateSystem system)
    {
        this.system = system;
    }
}


```

Alright, we're good to go! Time to plug everything together!