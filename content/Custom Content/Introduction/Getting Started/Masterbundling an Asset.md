---
{"publish":true,"created":"2025-08-19T20:18:18.000+07:00","modified":"2025-08-19T20:18:18.000+07:00","cssclasses":""}
---

Create a folder in Unity for mod contents to go in. In this example, `Assets/MyMods/TestMod/Bundles`
## Marking folder to Bundle
By default, the inspector window should be opened on the right side. If not, go to the menu bar and click **Window** > **General** > **Inspector**.
Navigate to the parent of Bundles(in this case **TestMod**), and select **Bundles**. Open the dropdown in **Asset Labels** and select **New...** Pick your desired bundle name suffixed with “.masterbundle”, I'll do `testmodbundles.masterbundle`.The name should not contain spaces, underscores/dashes, capital letters, or special characters.
## Setting up folders for export
Create a folder to export your assets into. This is also where your .dat and .asset files will be. If you're doing this for a map, it must be in the **Bundles** folder for global mod testing use **Sandbox**. Here you will create a file named **MasterBundle.dat**. If you haven't already, enable file name extensions to allow you to create the file easier. Note that the extensions must be correct or else Unturned wont recognize it(.txt does not work).
## Examples
```title:MasterBundle.dat
Asset_Bundle_Name testmodbundles.masterbundle 
// the directory in unity of everything before the bundle
Asset_Prefix Assets/MyMods/TestMod/Bundles
// Unity version: 2021 -> 5 | 2020 -> 4 | 2019/2018.4 -> 3 | 2017.4 -> 2 | 5.5 -> 1
Asset_Bundle_Version 5
```
## Masterbundling
Open the master bundling tool via **Window** > **Unturned** > **Master Bundle Tool**. Expand the Asset Bundle and tick your label(in this case `testmodbundles.masterbundle`). Expand the master bundle click the “…” and select your folder(in this case …/Maps/DemoMap/Bundles/TestMod). You can optionally check the multi-platform for the published version of the mod, for testing purposes it does not need to be checked.

**Your file structure should look something like this:**
```
.../DemoMap/Bundles/MyFirstMod
    MasterBundle.dat
    testmodbundles.masterbundle
    Objects/Large/MyFirstBuilding (Must match 1:1 with Unity hierachy)
        MyFirstBuilding.dat
        English.dat
```
All you need to do now is move `MyFirstBuilding.dat` and `English.dat` into the `MyFirstBuilding` folder like shown above.

Launch Unturned and go into the map and place your first building in! If it does not work be sure to check **Workshop** > **Error Logs**.

---
(Proofread: 2025-08-18)
Sources: [A Steam guide on MasterBundling](https://steamcommunity.com/sharedfiles/filedetails/?id=2976338845)

```button
name Back
type link
action obsidian://open?vault=Unturned%20Docs&file=Modding%2FGetting%20Started%2FUnitying%20an%20asset
```
^button-nqcv