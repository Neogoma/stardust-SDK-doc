# Provide device intrisics

The next step is to provide teh [camera instrisics datas](https://en.wikipedia.org/wiki/Camera_resectioning#Intrinsic_parameters).

## Create an event
First of all you need to create the event to communicate the picture to the differents stardust modules. You need to create a class that will extend ```BaseInteractionEvent``` and implement ```IPictureDataReady```. This event will hold the pictures datas as a byte array (coming from the ``Texture2D.EncodeToJPG()`` function).

```cs
using com.Neogoma.HoboDream;
using com.Neogoma.HoboDream.Impl;
using com.Neogoma.Stardust.API;

public class PictureEvent : BaseInteractionEvent, IPictureDataReady
{
    private byte[] data;

    public PictureEvent(IInteractiveElement source) : base(source, InteractiveEventAction.ARRIVED)
    {
    }

    public void SetData(byte[] data)
    {
        this.data = data;
    }

    public byte[] GetPictureDatas()
    {
        return data;
    }
}
```

## Create a camera image provider

Now we need to setup the class that will compute the image for the rest of the stardust components. You need to create a class that will extend ```AbstractNonMonoInteractive``` and implement ```ICameraImageProvider```. This class will compute the pictures datas and convert them into a byte array (coming from the ``Texture2D.EncodeToJPG()`` function) to then dispatch them to the different modules.


```cs
using com.Neogoma.HoboDream.Impl;
using com.Neogoma.Stardust.API;

public class CustomImageProvider : AbstractNonMonoInteractive, ICameraImageProvider
{
    public void ComputeImageData()
    {
        //Create a new event
        PictureEvent picEvent=new PictureEvent(this);

        //Initialize a new array
        byte[] imageDatas=new byte[0];

        //Write the code to fill in the imageDatas array here with your own data feed

        //Update the event with the array
        picEvent.SetData(imageDatas);

        //Dispatch the event
        NotifyListeners(picEvent);

    }

    public void InitializeCamera()
    {
        //Do what you need to initialize the camera here (for example: select the front/back camera )
    }

    public void SetQuality(ImageQuality quality)
    {
        //Do what you need to setup the right quality of the camera here (for example: select the resolution)
    }
}
```

Now that the basic structure is set for getting the image the next step will be to get the intrisics!
