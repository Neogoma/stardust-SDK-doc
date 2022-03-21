# Uploading an object

- Go to the [object list page](https://stardust.neogoma.com/object_list) and click create new object.
- Once you're on the object upload page, select [create a new object](https://stardust.neogoma.com/add_bundle)

Then you will have the choice between 2 formats:

## GLB Format

GLB is a 3D file format that's used in Virtual Reality (VR), Augmented Reality (AR), games, and web applications because it supports motion and animation. GLB files are a binary version of the GL Transmission Format (glTF) file,
- Fill in the name
- Browse and choose your .GLB file to upload.ee (max size 80 mb). 
- Click on "Create object"

## Image Format
We had a lot of request to support different images for different usages (floor plans, NFT, arts..). We decided that the most flexible way for users to use pictures in our app would be to allow people to directly link from external sources ([Imgur](https://imgur.com/), [Imgbb](https://imgbb.com/), user own server...). 
- Fill in the name
- Fill in the URL of the image (example: https://neogoma.com/images/logoneogoma.png). 
- Click on "Create object"

### Interactive objects
Since we no longer support bundles you have to rely on using metadata to enable interactivity with objects. The scripts and interactivity will be local to your build so you have to apply this logic when the object is instantiated on the scene.
Check out [this tutorial](https://youtu.be/ez_dbPhejZs) on how to use objects metadata in your favour.  





- Select the option "Upload a picture"
- Fill in the name
- Fill in the picture URL.
- Click on "Create object".

#### Notes
- Shaders and textures can be exported without the need to be on the Stardust project.

## Local content

If you don't want to use the cloud solution and make your objects locally, please follow [this tutorial](developer/1_1_setup_project.md).