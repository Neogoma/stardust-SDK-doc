# Provide device intrisics

The next step is to provide the [camera instrisics datas](https://en.wikipedia.org/wiki/Camera_resectioning#Intrinsic_parameters).

## Overview of IntrisicsData class
The ```IntrisicsData``` class is used to dispatch the data of the **CURRENT** image intrisics to the other stardust modules.

You will create the object with the following constructor:
```cs
public IntrisicsData(float fx, float fy, float cx, float cy, float lx, float ly);
```

The different parameters are:
* fx : camera width (pixel)
* fy : camera height (pixel)
* cx : central point x
* cy : central point y
* lx : focal lenght x
* ly : focal lenght y

**Note** You need to make SURE that the data match your camera orientation otherwise the training AND the point cloud generation could produce wrong results.

## Create a class to provide intrisics
You need to create a class that will implement ```ICameraImageIntrisicsProvider```.

There is only one method that will return an ```IntrisicsData``` object

```cs
using com.Neogoma.Stardust.API;
using com.Neogoma.Stardust.Datamodel;

public class CustomIntrisicsProvider : ICameraImageIntrisicsProvider
{
    public IntrisicsData GetCameraInstrinscs()
    {
        //For the example create a dummy intrisics data with fake datas and return it
        //Provide the datas from your device instead
        IntrisicsData datas = new IntrisicsData(0, 0, 0, 0, 0, 0);

        return datas;
    }
}
```



Now that the basic structure is set for getting the image the next step will be to get the device position!
