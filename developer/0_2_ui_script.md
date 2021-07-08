# Setting up the script to interact with the UI

Now that the project is setup we just have to write one class to manage all the data initialization for the map. We will start connecting our script with the [MapRelocationManager](developer/comp_map_relocation_manager.md). 

## Initialize the script

First we need to prepare the script that will initialize the relocation manager.

1. Create a new script called **RelocationExample** 

2. Now delete the ```void Update()``` method and the attribute ```public string id;``` your class should now look like this

3. Create a method ```private void MapDownloaded(Session session, GameObject map)```. It will be called once the SDK finishes downloading the map from the server. Leave it empty for now.

```cs
using com.Neogoma.Stardust.API.Relocation;
using com.Neogoma.Stardust.Datamodel;
using UnityEngine;


public class RelocationExample : MonoBehaviour
{
    public string id;

    // Start is called before the first frame update
    void Start()
    {
       
    }

    private void MapDownloaded(Session session, GameObject map)
    {
        
    }
}
```

## Listen to MapRelocationManager

1. Set the ```private void MapDownloaded()``` function as a listener of **MapRelocationManager.onMapDownloadedSucessfully** in the ```void Start()``` function. Now your class should look like that

```cs
using com.Neogoma.Stardust.API.Relocation;
using com.Neogoma.Stardust.Datamodel;
using UnityEngine;

public class RelocationExample : MonoBehaviour
{
    public string id;

    // Start is called before the first frame update
    void Start()
    {
        //Adding the listener
        MapRelocationManager.Instance.onMapDownloadedSucessfully.AddListener(MapDownloaded);
    }

    private void MapDownloaded(Session session, GameObject map)
    {
        
    }
}
```

2. Now keep in mind that you should **NOT RELOCATE BEFORE A MAP HAS BEEN DOWNLOADED**. This is why we listen to the **MapRelocationManager.onMapDownloadedSucessfully** event. Now you can add an button ```public GameObject locateButton;``` attribute and enable it when map has been downloaded!

```cs
using com.Neogoma.Stardust.API.Relocation;
using com.Neogoma.Stardust.Datamodel;
using UnityEngine;

public class RelocationExample : MonoBehaviour
{
    public string id;

    public GameObject locateButton;

    // Start is called before the first frame update
    void Start()
    {
        //Safety here, make sure the button is not enabled until the map download is done
        locateButton.SetActive(false);

        //Adding the listener
        MapRelocationManager.Instance.onMapDownloadedSucessfully.AddListener(MapDownloaded);
    }

    private void MapDownloaded(Session session, GameObject map)
    {
        //The map is downloaded we can relocate now
        locateButton.SetActive(true);
    }
}
```

## Request the map download

Now we just have to request the map on start using the id with a call from ```MapRelocationManager.Instance.GetDataForMap``` (for more details check the [class overview](developer/comp_map_relocation_manager.md)). Your class will now look like this:

```cs
using com.Neogoma.Stardust.API.Relocation;
using com.Neogoma.Stardust.Datamodel;
using UnityEngine;

public class RelocationExample : MonoBehaviour
{
    public string id;

    public GameObject locateButton;

    // Start is called before the first frame update
    void Start()
    {
        //Safety here, make sure the button is not enabled until the map download is done
        locateButton.SetActive(false);

        //Adding the listener
        MapRelocationManager.Instance.onMapDownloadedSucessfully.AddListener(MapDownloaded);

        //Start downloading the map
        MapRelocationManager.Instance.GetDataForMap(id);
    }

    private void MapDownloaded(Session session, GameObject map)
    {
        //The map is downloaded we can relocate now
        locateButton.SetActive(true);
    }
}
```

What will happen ?
* The script will download the map on start (you can edit the map directly on the dashboard).
* Once the map is downloaded it will activate the __locate__ button to allow the user to relocate.

Now it's time to put everyting together!



