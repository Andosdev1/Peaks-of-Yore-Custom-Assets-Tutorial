# Using Custom Assets with the Peaks of Yore Level Editor

The Peaks of Yore Level Editor allows you to use custom objects for your levels. This tutorial will go through how to make your object ready-for-use in the Level Editor and for your levels.
It is ideal if you have an O.K understanding of using the Unity Editor, as this tutorial will rush through a few things.


1. First, create a new Unity Project with version <b>2019.4.36f</b>.

This version is important because it's the same that Peaks of Yore uses. Other versions of Unity that builds Asset Bundles are not guaranteed to be compatible with the Level Editor in Peaks of Yore.

Under the Assets folder, create a new folder called <i>Editor</i>.

<img width="396" height="324" alt="tut_1" src="https://github.com/user-attachments/assets/308363f7-98cb-490b-88f1-1e07360f5779" />

In the newly created Editor folder, create a new C# script called BuildAssetBundles. 
Copy and Paste the following code snippet into the newly created C# script and then Save it.

```cs
using UnityEditor;
using UnityEngine;
using System.IO;

public class BuildAssetBundles : MonoBehaviour
{
    [MenuItem("Assets/Build AssetBundles")]
    static void BuildAllAssetBundles()
    {
        string assetBundleDirectory = "Assets/AssetBundles";
        if (!Directory.Exists(assetBundleDirectory))
        {
            Directory.CreateDirectory(assetBundleDirectory);
        }
        BuildPipeline.BuildAssetBundles(assetBundleDirectory, BuildAssetBundleOptions.None, BuildTarget.StandaloneWindows);
    }
}

```

2. Now import your custom mesh into Unity.

<img width="192" height="211" alt="tut_2" src="https://github.com/user-attachments/assets/d95f50f4-3ebc-43b6-87ff-d6508c653f54" />

3. Set up the material, textures, and collision of your object. If you want the object to be climbable, set the Tag as "Climbable". Physics-affected objects will need to be set as "ClimbableRigidbody", but I recommend using the preset physics objects within the Level Editor. 
It is up to you what you want to include on the object in terms of textures, color, collision, tags or layers. 
 
<img width="1124" height="715" alt="tut_3" src="https://github.com/user-attachments/assets/7a2b1b6e-4692-4b4c-9900-e182d9c3ba70" />

4. Make a prefab out of your custom object once you have set it up.

<img width="1107" height="821" alt="tut_4" src="https://github.com/user-attachments/assets/3e5e5299-8c70-47ea-9411-fbecd3b62c51" />

You <ins>cannot add scripts to your objects</ins> as Asset Bundles cannot include executable code.

The "Climbable" / "ClimbableRigidbody" tags will only work on collision components. You cannot use Mesh Colliders on physics objects, only Primitive Colliders like Box, Sphere and Capsule will work.
If you want the Player to not be able to stand on anything of the object while still having collision, you can give it a Layer (User Layer 26) called "WindMillWings".

### The following tags can be used for Peaks of Yore Climbables:
- "Climbable" (regular holds)
- "ClimbableRigidbody" (physics objects)
- "ClimbablePitch" (stamina draining)
- "Ice" (for ice axes)
- "PinchHold (small fast stamina-draining hold)

<img width="716" height="939" alt="tut_5" src="https://github.com/user-attachments/assets/e9ceed9d-741a-4568-aa73-26bfa4a4830e" />

5. Once your prefab is set up and ready to be made into an Asset Bundle, select your prefab and click on the lower double horizontal line found at the bottom to expand the Asset Bundle section.

<img width="715" height="939" alt="tut_6" src="https://github.com/user-attachments/assets/47e84f35-f894-478d-ad5d-c86006554fec" />

6. Create a new bundle.

<img width="629" height="585" alt="tut_7" src="https://github.com/user-attachments/assets/c1c22019-57c0-4c18-9d3b-d90598fa0e73" />

The name will be all lowercase. 

<img width="632" height="302" alt="tut_8" src="https://github.com/user-attachments/assets/70ad3bc2-b1eb-4864-b901-5216bcaa6eb1" />

Note that you can create multiple prefabs and add them to your Asset Bundle. The Custom Single Asset feature allows you to place specific prefabs from the Asset Bundle associated with your Custom Level. So if a prefab in your Asset Bundle is named "MyRock_A" for example, then the Custom Single Asset feature will need to use that exact name in order to load it. You can only load specific prefabs that associated with Asset Bundle of the Custom Level you are working in.

7. Go to Assets > Build AssetBundles

<img width="426" height="687" alt="tut_9" src="https://github.com/user-attachments/assets/c4e84138-253b-48b5-9a5f-70b7bf523899" />

<img width="426" height="687" alt="tut_9" src="https://github.com/user-attachments/assets/e5e0aa0e-e7ac-4034-9d8f-5b458fe38da7" />


- New files can be found at Assets > AssetBundles.
- Copy the largest file within AssetBundles to your Compendium Folder (same location as your Custom Level(s).
- You can now use the AssetBundle within the Level Editor. 
- Load Full Bundle allows you to load the entire bundle at once on play. 
- Custom Single Asset allows you to load specific assets within the Asset Bundle.

