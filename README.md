First, create a new Unity Project with version 2019.4.36f. This version is important because it's the same that Peaks of Yore uses. Other versions of Unity that builds Asset Bundles are not guaranteed to be compatible with the Level Editor in Peaks of Yore.

Under the Assets folder, create a new folder called Editor. Place the BuildAssetBundle.cs script in the Editor folder.
  <img width="396" height="324" alt="tut_1" src="https://github.com/user-attachments/assets/308363f7-98cb-490b-88f1-1e07360f5779" />

Import your custom mesh into Unity.

<img width="192" height="211" alt="tut_2" src="https://github.com/user-attachments/assets/d95f50f4-3ebc-43b6-87ff-d6508c653f54" />
Set up the material, textures, and collision of your object. If you want the object to be climbable, set the Tag as "Climbable".
<img width="1124" height="715" alt="tut_3" src="https://github.com/user-attachments/assets/7a2b1b6e-4692-4b4c-9900-e182d9c3ba70" />

- Make a prefab out of your custom object once you have set it up.
- Select your prefab and click on the lower double horizontal line found at the bottom to expand the Asset Bundle section.
- Create a new bundle.
- Go to Assets > Build AssetBundles
- New files can be found at Assets > AssetBundles.
- Copy the largest file within AssetBundles to your Compendium Folder (same location as your Custom Level(s).
- You can now use the AssetBundle within the Level Editor. 
- Load Full Bundle allows you to load the entire bundle at once on play. 
- Custom Single Asset allows you to load specific assets within the Asset Bundle.

