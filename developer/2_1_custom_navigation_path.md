# Customize the navigation path rendering

Besides changing the prefab used you can now access to the calculated path and decide yourself how to render the path. In this tutorial we will explain you how to customize the rendering.

## Create your own Path renderer.
You first need to create your own renderer that will extend AbstractNonMonoInteractive and IPathRenderer.

```cs
using com.Neogoma.HoboDream.Impl;
using com.Neogoma.Octree;
using com.Neogoma.Stardust.Navigation;
using System.Collections.Generic;

public class CustomPathRenderer : IPathRenderer
{
    public void ClearPath()
    {
        //Write what needs to be done here to clear the path
    }

    public void DisplayPath(List<IOctreeCoordnateObject> allNavigationsPoint)
    {
        //Write needs to be done here to display the path

        //You can get the coordnate of each point via the function IOctreeCoordnateObject.GetCoordinates()
    }
}
```

You can customize the class as much as you want but you need to fill in both methods:
- ClearPath() is called when the path is recalculated and cleans the path view
- DisplayPath(List<IOctreeCoordnateObject> allNavigationsPoint) is called when the path has been calculated and needs to be displayed. This is where you instanciate your prefabs or models for showing the path. Each ```IOctreeCoordnateObject``` represents a point and has a method ```Vector3 GetCoordinates()```to get the coordnates. 

 **NOTE**: we only provide the list of navigation points! You can use it to decide where to position your models!

## Setup your custom render

After setting up your custom renderer your just have to assign it to the pathfinder manager by just making the following call
```cs
PathFindingManager.Instance.SetPathRenderer(new CustomPathRenderer());

```

After this your renderer should take over the default one and you should be able to see the rendering you setup happen!
