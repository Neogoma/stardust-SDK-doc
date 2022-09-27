# Role of the class
This class is in charge of setting up the structures and data for the offline mapping.

**Note** This feature is a premium feature that only SME and above tiers can use.

The Offline Mapper controller is a singleton that can be called via:
```cs
OfflineMapper offlineMapper=OfflineMapper.Instance();
```

# Mapping

## Start a new offline map
To create a new session you need to call the __StartNewMap(string mapName)__. The name can not be null.

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
After recording your session you should save the mapping data on device using __SaveMapData()__. 
If your don't save the datas, you will never be able to upload them.

## Get the list of maps on device
The Offline Mapper also has a method __GetOfflineMapsOnDevice()__ to retrieve the list of maps on device. It will only return the names of the maps that you can use for the upload method.

**NOTE** Only maps that have been saved with __SaveMapData()__ method will be available.

```cs
public void Start()
{
    string[] existingMaps = OfflineMapper.Instance.GetOfflineMapsOnDevice();
}
```

## Upload map
In order to upload your map you just have to call the __UploadMapDatas(string mapName)__ of the __OfflineMapper__ class.

**NOTE** Once the map has been uploaded online, all the data on your phone will be destroyed.

```cs
//Uploads the data online
public void UploadData(string mapName)
{
    OfflineMapper.Instance.UploadMapDatas(mapName);
}
```

# Update
## Start a new update
To create a new session you need to call the __StartMapUpdate(Session session)__. You can easily get the session object via the [map setup](developer/classes_overview/comp_map_relocation_manager?id=setup-the-map-first-cloud-content-only) or via the [list of sessions](developer/classes_overview/comp_session_controller?id=get-the-list-of-session).

```cs
public void StartSessionUpdate(Session session)
{
    OfflineMapper.Instance.StartMapUpdate(session);
}
```

For capturing data you can still use:
*  __StartCapturingDatas()__ to start taking pictures
*  __StopCapturingDatas()__ to stop taking pictures

## Upload update
In order to upload your update you just have to call the __UploadMapUpdate(Session session)__ of the __OfflineMapper__ class.

**NOTE** Once the map has been uploaded online, all the data on your phone will be destroyed.

```cs
//Uploads the data online
public void UploadUpdate(Session session)
{
    OfflineMapper.Instance.UploadMapUpdate(session);
}
```

## Get the list of updates on device
The Offline Mapper also has a method __GetOfflineUpdatesOnDevice()__ to retrieve the list of updates on device. It will only return the names of the maps.

**NOTE** Only maps that have been saved with __SaveMapData()__ method will be available.

```cs
public void Start()
{
    string[] existingMaps = OfflineMapper.Instance.GetOfflineMapsOnDevice();
}
```

# Delete

## Delete all data
```cs
//Uploads the data online
public void DeleteAllLocalData()
{
    OfflineMapper.Instance.DeleteAllLocalDatas();
}
```

## Delete map using name
```cs
//Deletes the local mapping data for a map
public void DeleteMapWithName(string name)
{
    OfflineMapper.Instance.DeleteAllLocalDatas(string name);
}
```



# Events
The offline mapper has multiple events depending on the situation
```cs
public void Start(){
    //Get instance
    OfflineMapper offlineMapper = OfflineMapper.Instance;
    
    //This event when data will be captured on device
    offlineMapper.onFrameCaptured.AddListener(OnDataCaptured);
    
    //This event will be called when data was successfully sent to server
    offlineMapper.onCurrentPackageUploadFinishedEvent.AddListener(OnDataSentSuccess);
    
    //This event will be called if you reach your data limit
    offlineMapper.datalimitReached.AddListener(OnDataLimitReached);

    //This event will be called when the data progresses further
    offlineMapper.onRequestProgress.AddListener(OnDataUploadProgress);

    //This event will be called when the map has been saved
    offlineMapper.onMapSaved.AddListener(OnMapSaved);

    //This event will be called when the global upload status is updated
    //The upload progress (between 0 and 1  ) is calculated based on the number of maps on device
    offlineMapper.onGlobalUploadUpdateEvent.AddListener(OnGlobalUploadUpdate);


}

private void OnMapSaved(float uploadProgress)
{
    Debug.Log("Upload progress");
}

private void OnMapSaved(int datacount)
{
    Debug.Log("Map saved");
}

private void OnDataCaptured(int datacount)
{
    Debug.Log("Data captured" + datacount);
}

private void OnDataSentSuccess(int uploadCount)
{
    Debug.Log("Data captured" + uploadCount);
}

private void OnDataLimitReached()
{
    Debug.Log("Maximum pictures for map reached");
}

private void OnDataUploadProgress(float uploadProgress)
{
    Debug.Log("Current upload progress" + uploadProgress);
}
```