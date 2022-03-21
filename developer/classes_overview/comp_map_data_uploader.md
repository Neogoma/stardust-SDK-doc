# Role of the class 
The MapDataUploader class is in charge of sending the mapping datas to the server. It manages all the functions to send datas and generate map.
The Map data uploader is a singleton that can be called via 
```cs
MapDataUploader dataUploader = MapDataUploader.Instance;
```

## Events
The map data uploader has multiple events depending on the situation
```cs
public void Start(){
    //Get instance
    MapDataUploader dataUploader = MapDataUploader.Instance;
    
    //This event when data will be captured on device
    dataUploader.dataCapturedSucessfully.AddListener(OnDataCaptured);
    
    //This event will be called when data was successfully sent to server
    dataUploader.dataSentSucessfully.AddListener(OnDataSentSuccess);
    
    //This event will be called if you reach your data limit
    dataUploader.datalimitReached.AddListener(OnDataLimitReached);

    //This event will be called when the data progresses further
    dataUploader.onRequestProgress.AddListener(OnDataUploadProgress);

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

## Start/Stop uploading datas
You can easily control when you send datas or when you stop sending datas via the methods provided by the singleton.

Please note that if you stop the capture, the datas that are stored on device but not sent will still be sent to server.
```cs
//Start sending data to server
public void StartCapturingData(){
    MapDataUploader.Instance.StartCapturingDatas();
}

//Stops sending data to server
public void StopCapturingData(){
    MapDataUploader.Instance.StopCapturingDatas();
}
```

## Run generation (new map)
If you run a generation, be aware that the generation will be done on **UPLOADED DATAS ONLY**.

```cs
public void GenerateMap(){
    MapDataUploader.Instance.GenerateMap();
}
```

## Run update (existing map)
In order to update a map you need to setup the session first and create the batch first.
```cs

public void Start(){
    //Listen to the batch setup
    MapDataUploader.Instance.onBatchReadyToUpdate.AddListener(OnBatchReady);
}

//Sets the current session and prepares the batch on server
public void SetActiveSession(Session session){
    MapDataUploader.Instance.SetSession(selectedSession);
    MapDataUploader.Instance.SetUpdateBatch();
}

public void OnBatchReady(){
    //You can start mapping starting from here 
}
```

You can get the Session object directly from the [Session manager](my_objects.md).


Once the active session has been setup you can start uploading datas. Once the needed datas have been uploaded you can call the update with the following call

```cs
public void UpdateMap(){
    MapDataUploader.Instance.UpdateMap();
}
```
