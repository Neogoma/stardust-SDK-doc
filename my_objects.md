# Uploading an object

## GLB Format

GLB is a 3D file format that's used in Virtual Reality (VR), Augmented Reality (AR), games, and web applications because it supports motion and animation. GLB files are a binary version of the GL Transmission Format (glTF) file,

- Go to the [object list page](https://stardust.neogoma.com/object_list) and click create new object.
- Once you're on the object upload page select [create a new object](https://stardust.neogoma.com/add_bundle)
- Fill in the name
- check the "Public object" checkbox if you want to share with other users of the platform
- Browse and choose your .GLB file to upload.ee (max size 80 mb). **The name should NOT contain spaces!**
- Click on "Create object"

### Interactive objects
Since we no longer support bundles you have to rely on using metadata to enable interactivity with objects. The scripts and interactivity will be local to your build so you have to apply this logic when the object is instantiated on the scene.
Check out [this tutorial](https://youtu.be/ez_dbPhejZs) on how to use objects metadata in your favour.  

#### Hobodream AR SDK
- Import the latest release of the Hobodream AR SDK in your project
- Import the latest release of the Hobodream AR SDK in your bundle project

#### Notes
- Shaders and textures can be exported without the need to be on the Stardust project.

## Local content

If you don't want to use the cloud solution and make your objects locally, please follow [this tutorial](developer/1_1_setup_project.md).