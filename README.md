# Using Custom Assets with the Peaks of Yore Level Editor

The Peaks of Yore Level Editor allows you to use custom objects for your levels. This tutorial will go through how to make your object ready-for-use in the Level Editor and for your levels.
It is ideal if you have an O.K understanding of using the Unity Editor, as this tutorial will rush through a few things.


1. First, create a new Unity Project with version <b>2019.4.41f1</b>.

This version is important because it's the same that Peaks of Yore uses. Other versions of Unity that builds Asset Bundles are not guaranteed to be compatible with the Level Editor in Peaks of Yore.

Under the Assets folder, create a new folder called <i>Editor</i>.

<p align="center">
<img width="396" height="324" alt="tut_1" src="https://github.com/user-attachments/assets/308363f7-98cb-490b-88f1-1e07360f5779" />
</p>

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

<p align="center">
<img width="192" height="211" alt="tut_2" src="https://github.com/user-attachments/assets/d95f50f4-3ebc-43b6-87ff-d6508c653f54" />
</p>

3. Set up the material, textures, and collision of your object. If you want the object to be climbable, set the Tag as "Climbable". Physics-affected objects will need to be set as "ClimbableRigidbody", but I recommend using the preset physics objects within the Level Editor. 
It is up to you what you want to include on the object in terms of textures, color, collision, tags or layers. 

<p align="center">
<img width="1124" height="715" alt="tut_3" src="https://github.com/user-attachments/assets/7a2b1b6e-4692-4b4c-9900-e182d9c3ba70" />
</p>

4. Make a prefab out of your custom object once you have set it up.

<p align="center">
<img width="1107" height="821" alt="tut_4" src="https://github.com/user-attachments/assets/3e5e5299-8c70-47ea-9411-fbecd3b62c51" />
</p>

You <ins>cannot add scripts to your objects</ins> as Asset Bundles cannot include executable code.

The "Climbable" / "ClimbableRigidbody" tags will only work on collision components. You cannot use Mesh Colliders on physics objects, only Primitive Colliders like Box, Sphere and Capsule will work.
If you want the Player to not be able to stand on anything of the object while still having collision, you can give it a Layer (User Layer 26) called "WindMillWings".

### The following tags can be used for Peaks of Yore Climbables:
- "Climbable" (regular holds)
- "ClimbableRigidbody" (physics objects)
- "ClimbablePitch" (stamina draining)
- "Ice" (for ice axes)
- "PinchHold (small fast stamina-draining hold)

<p align="center">
<img width="716" height="939" alt="tut_5" src="https://github.com/user-attachments/assets/e9ceed9d-741a-4568-aa73-26bfa4a4830e" />
</p>
    
5. Once your prefab is set up and ready to be made into an Asset Bundle, select your prefab and click on the lower double horizontal line found at the bottom to expand the Asset Bundle section.

<p align="center">
<img width="715" height="939" alt="tut_6" src="https://github.com/user-attachments/assets/47e84f35-f894-478d-ad5d-c86006554fec" />
</p>

6. Create a new bundle.

<p align="center">
<img width="629" height="585" alt="tut_7" src="https://github.com/user-attachments/assets/c1c22019-57c0-4c18-9d3b-d90598fa0e73" />
</p>

The name will be all lowercase by default.
You'll need to <ins>rename it to whatever the name of your Custom Level is</ins>. 

<p align="center">
<img width="632" height="302" alt="tut_8" src="https://github.com/user-attachments/assets/70ad3bc2-b1eb-4864-b901-5216bcaa6eb1" />
</p>

Note that you can create multiple prefabs and add them to your Asset Bundle. The Custom Single Asset feature allows you to place specific prefabs from the Asset Bundle associated with your Custom Level. So if a prefab in your Asset Bundle is named "MyRock_A" for example, then the Custom Single Asset feature will need to use that exact name in order to load it. You can only load specific prefabs that associated with Asset Bundle of the Custom Level you are working in.

7. Go to Assets > Build AssetBundles

<p align="center">
<img width="426" height="687" alt="tut_9" src="https://github.com/user-attachments/assets/c4e84138-253b-48b5-9a5f-70b7bf523899" />
</p>

<p align="center">
<img width="426" height="687" alt="tut_9" src="https://github.com/user-attachments/assets/e5e0aa0e-e7ac-4034-9d8f-5b458fe38da7" />
</p>

8. After building finishes, you should see new files at Asset > AssetBundles. 

Typically the largest file should be the actual Asset Bundle that you'll need to copy into your Custom Level's Location. 
<p align="center">
<img width="688" height="650" alt="tut_10" src="https://github.com/user-attachments/assets/510676f5-056d-425b-841c-bdbdfa0d385e" />
</p>

9. If you have saved your current Custom Level, the Asset Bundle should be pasted into your Compendium's Folder. Typically on Windows, this location is within CustomLevels/YourCompendiumName. 
The Asset Bundle name will need to match the level's name, but it doesn't matter if it's capitalized or not - as long as it matches the level's name. To keep it consistent, just copy-paste your level's name to your Asset Bundle file.

<p align="center">
<img width="1648" height="418" alt="image" src="https://github.com/user-attachments/assets/552d0247-0e7e-422e-9565-5e6c9b2f8763" />
</p>

A shortcut to the CustomLevels location can be found below - simply copy and paste it to a folder address bar. You should be able to find your Compendium folder in here, providing you have made one either through the Level Editor - Peak Page setup, or manually. 
```
%USERPROFILE%\AppData\LocalLow\TraipseWare\Peaks of Yore\CustomLevels
```
<p align="center">
<img width="770" height="85" alt="image" src="https://github.com/user-attachments/assets/ec67be00-3c76-46d1-a150-07e488b57bbb" />
</p>


# Using your newly built Asset Bundles

### Load Full Custom Bundle

Toggling Load Full Custom Bundle on will load everything within the Asset Bundle file.

<p align="center">
<img width="324" height="278" alt="image" src="https://github.com/user-attachments/assets/e782b5aa-77e8-4080-9aa8-837a54f1f13a" />
</p>

### Custom Single Asset

This will allow you to specify which prefabs to use from within the Asset Bundle and then place them manually within the scene.

If you intend to use this, I don't recommend using the Load Full Custom Bundle feature, as the Custom Single Asset is intended to be more of a pick-and-choose type of feature, rather than spawning in everything from the Asset Bundle, but this is of course up to you.


<p align="center">
<img width="324" height="282" alt="image" src="https://github.com/user-attachments/assets/425cdd0a-8683-45ef-a48f-6733e73da850" />
</p>

Once you place the Custom Single Asset holder, you'll get the option to specify which prefab it should load from your Asset Bundle. 

<p align="center">
<img width="711" height="645" alt="image" src="https://github.com/user-attachments/assets/5f8abb1c-d25d-4768-9586-a86e625e206f" />
</p>

This should <ins>match the prefab name you want</ins> from the Asset Bundle. So for example, if you have a prefab called <b>bed_prefab</b> inside the Asset Bundle file, the Bundle Asset Name should be <b>bed_prefab</b>. 

<img width="1050" height="700" alt="image" src="https://github.com/user-attachments/assets/aed1d288-4b9c-45ad-8e04-fec375da0a15" />

