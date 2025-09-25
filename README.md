# Using Custom Assets with the Peaks of Yore Level Editor

First, create a new Unity Project with version <b>2019.4.36f</b>.

This version is important because it's the same that Peaks of Yore uses. Other versions of Unity that builds Asset Bundles are not guaranteed to be compatible with the Level Editor in Peaks of Yore.

Under the Assets folder, create a new folder called <i>Editor</i>.

<img width="396" height="324" alt="tut_1" src="https://github.com/user-attachments/assets/308363f7-98cb-490b-88f1-1e07360f5779" />

In the newly created Editor folder, create a new C# script called BuildAssetBundles. 
Copy and Paste the following code snippet into the newly created C# script and Save.

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

Now import your custom mesh into Unity.

<img width="192" height="211" alt="tut_2" src="https://github.com/user-attachments/assets/d95f50f4-3ebc-43b6-87ff-d6508c653f54" />

Set up the material, textures, and collision of your object. If you want the object to be climbable, set the Tag as "Climbable". Physics-affected objects will need to be set as "ClimbableRigidbody", but I recommend using the preset physics objects within the Level Editor. 
It is up to you what you want to include on the object in terms of textures, color, collision, tags or layers. You cannot make scripts and add them to your objects as Asset Bundles cannot include executable code.

The "Climbable" / "ClimbableRigidbody" tags will only work on collision components.
If you want the Player to not be able to stand on anything of the object while still having collision, you can give it a Layer (User Layer 26) called "WindMillWings". 

### The following tags can be used for Peaks of Yore Climbables:
- "Climbable" (regular holds)
- "ClimbableRigidbody" (physics objects)
- "ClimbablePitch" (stamina draining)
- "Ice" (for ice axes)
- "PinchHold (small fast stamina-draining hold)
 
<img width="1124" height="715" alt="tut_3" src="https://github.com/user-attachments/assets/7a2b1b6e-4692-4b4c-9900-e182d9c3ba70" />


Make a prefab out of your custom object once you have set it up.

<img width="1107" height="821" alt="tut_4" src="https://github.com/user-attachments/assets/3e5e5299-8c70-47ea-9411-fbecd3b62c51" />

- Select your prefab and click on the lower double horizontal line found at the bottom to expand the Asset Bundle section.
- Create a new bundle.
- Go to Assets > Build AssetBundles
- New files can be found at Assets > AssetBundles.
- Copy the largest file within AssetBundles to your Compendium Folder (same location as your Custom Level(s).
- You can now use the AssetBundle within the Level Editor. 
- Load Full Bundle allows you to load the entire bundle at once on play. 
- Custom Single Asset allows you to load specific assets within the Asset Bundle.

