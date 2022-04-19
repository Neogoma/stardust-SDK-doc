# Role of the class
This class is in charge of setting up the structures and data for the offline mapping.

**Note** This feature is a premium feature that only SME and above tiers can use.

The Offline Mapper controller is a singleton that can be called via:
```cs
OfflineMapper offlineMapper=OfflineMapper.Instance();
```

# Mapping

## Start a new offline map
To create a new session you need to call the __StartNewMap(mapName)__. The name can not be null.

Then once the name is set you can call the method:
*  __StartCapturingDatas()__ to start taking pictures
*  __StopCapturingDatas()__ to stop taking pictures

```cs
public void Start(){

    //Creating the new map
    OfflineMapper.Instance().StartNewMap("New map");    
  
}

//Start the data capture
public void StartDataCapture()
{
    OfflineMapper.Instance().StartCapturingDatas();    
}

//Start the data capture
public void StopDataCapture()
{
    OfflineMapper.Instance().StopCapturingDatas();    
}
```

## Save datas
After recording your session you should save the mapping data on device using __SaveMapData(mapName)__. 
If your don't save the datas, you will never be able to upload them.

## Get the list of maps on device
The Offline Mapper also has a method __GetOfflineMapsOnDevice()__ to retrieve the list of maps on device. It will only return the names of the maps that you can use for the upload method.

**NOTE** Only maps that have been saved with __SaveMapData(mapName)__ method will be available.

```cs
public void Start()
{
    string[] existingMaps = OfflineMapper.Instance.GetOfflineMapsOnDevice();
}
```

## Upload map
In order to upload your map you just have to call the __UploadMapDatas(mapName)__ of the __OfflineMapper__ class.

**NOTE** Once the map has been uploaded online, all the data on your phone will be destroyed.

```cs
//Uploads the data online
public void UploadData(string mapName)
{
    OfflineMapper.Instance.UploadMapDatas(mapName);
}
```

# Update



# Events
