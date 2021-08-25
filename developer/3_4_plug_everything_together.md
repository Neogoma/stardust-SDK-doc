# Provide device intrisics

Final step! All providers are setup and running, we now need to link it to the proper modules

## Link everything to the Stardust modules

Now the final step is to link all your previously created classes and link them **BEFORE** using the Stardust modules (so better do it on Start() or Awake()).

You will mostly only have to link it to the ```MapRelocationManager``` in order to relocate and to the ```MapDataUploader```.

If you want to setup the custom providers for relocation.
```cs
using com.Neogoma.Stardust.API.Relocation;
using UnityEngine;

public class BasicRelocationSetup : MonoBehaviour
{
    private void Start()
    {
        MapRelocationManager.Instance.SetDeviceLocationProvider(new CustomPositionProvider());
        MapRelocationManager.Instance.SetupIntrisicsProvider(new CustomIntrisicsProvider());
        MapRelocationManager.Instance.SetupImageProvider(new CustomImageProvider());
    }
}
```

If you want to setup the custom providers for mapping.

```cs
using com.Neogoma.Stardust.API.Mapping;
using UnityEngine;

public class BasicMappingSetup : MonoBehaviour
{

    private void Start()
    {
        MapDataUploader.Instance.SetDeviceLocationProvider(new CustomPositionProvider());
        MapDataUploader.Instance.SetupIntrisicsProvider(new CustomIntrisicsProvider());
        MapDataUploader.Instance.SetupImageProvider(new CustomImageProvider());
    }
}
```