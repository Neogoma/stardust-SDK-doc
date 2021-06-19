## Running the mapping 
- You first need to make sure that your phone **SLAM** is stable enough to send proper datas to the server.
- Then when you start mapping a place you need to make sure that you walk **at a normal pace**.

## How to map

First start on the data capture, from there it will start

If you use the mapper you will notice on the top that you have 2 numbers:
![Picture taken](_img/pic_upload.png)
* Pictures taken: represents the frames taken on your phone. They __*DO NOT*__ represent the final status of your map
* Pictures uploaded: represents the frame sucessfully sent to server. __All these pictures will be part of the training.__

Once you start mapping your data are uploaded on the server by batch of 5. The datas are around 6 mb each so if you are using mobile data, __make sure you have enough data in your plan__.

__You don't have to fill in all your picture quota to train the map (remember to keep some for the [update](update_instructions.md)).__

Once you think you uploaded enough pictures for your space (try to cover as much area as necessary), you can click on the __TRAIN__ button.

If you didn't fully fill in your quota you can [update](update_instructions.md) your map later.

## How does it work
Unlike previous versions our mapping strategy is focused on collecting good quality data rather than a maximum of datas.
As a result the frames will be captured when we detect you moved in a significant way rather than at regular intervals.





## How to relocate
Go to a place or near a place that you already mapped then try to relocate there. Make sure you stand still in order to avoid frame blurriness.

## Examples
### Good mapping example
The following video is a simple example of **GOOD MAPPING**.

[Good mapping](_videos/good_mapping.mp4  ':include :type=video')

The user walk slowly and turns the camera slowly during rotations. 

### Bad mapping example
The following video is a simple example of **BAD MAPPING**


**What is wrong ?**
1. The user turned the camera fast so some frames will be low quality
2. The user was running while mapping which made frame inconsistent in quality
3. Because of the fast movements, maybe the SLAM datas of the phones are also

[Bad mapping](_videos/bad_mapping.mp4 ':include :type=video')
