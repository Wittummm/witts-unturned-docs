---
publish: true
---
<u></u><u></u><u></u><u></u>This page will teach you how to make a basic object(building) and get it ready to export for Unturned. It will **not** teach you basics about creating the asset itself, only the barebones of what is needed for you to complete and put the asset in-game.
### What makes up an <u>Object</u>?
> [!tip]
> If you are too lazy to read or simply don't understand, you can find videos on youtube. You can also watch [Nelson's video](https://www.youtube.com/watch?si=JkNXE_ruAle7w1F4&t=2790).*

Each of these listed below is a Prefab, each being in the folder of your object. For example, `MyHouse/Nav`, `MyHouse/Object`, etc
* Nav - is what mobs use for its navigation. 
	* This mesh doesn't need roofs or frames(of windows, doors, etc). The mesh should be simple and the foundation should be expanded to be more of a ramp. Every ledge should be smoothed so that it does not have such a harsh corner like the ledge of a window should be more ramp like. It should exclude places unreachable by mobs. Needs a Mesh Collider. Tag and layer: Navmesh.
* Clip(optional) - is collision box on server, 
	* this collision box is not used for the client. Needs a Collider. Tag and layer: (Large, Medium, Small)
* Skybox(optional) - is rendered when the object is considered a Landmark. 
	* This mesh should be very simple at around 30 triangles. It usually does not include an interior and is a primitive shape. Needs a Mesh Filter, and Mesh Renderer. Tag and layer: Large/Medium/Small
* Object - is the main model which contains the LODs. The name of the LODs should be "Model\_#" with # being the number(starts from zero). 
	* Optionally, you can add Occlusion Areas. The objects in that box will will be culled early. Needs a LOD group, Mesh Filter, Mesh Renderer, and a Mesh Collider(or a primitive collider). The Mesh Collider is usually the LOD_1(second LOD). Tag and layer: (Large, Medium, Small)
* Slots(optional) - consists of Box Colliders. The possible names are Door, Gate, Slot(for barricades like windows, etc). Tag and layer: Logic

#### Making the prefabs
Right-click to create a preset 
`MySize` refers to Small, Medium or Large, choose one that matches your needs.
- Nav - Add component `Mesh Collider`, set the mesh to your nav mesh + Set Tag & Layer to `Navmesh`
- Clip - Add component `Collider`(it can be any type, choose one you intend to use) + Set Tag & Layer to `MySize`
- Skybox - Add component `Mesh Renderer`, set the mesh to your skybox mesh + Set Tag & Layer to `MySize`
- Slots - Add components of `Box Collider`, place it accordingly and name it to one of the recognized names. 
- Objects - Create a Transform and name it like `Model_#` such as `Model_0`.
	- For each `Model_#`, Add component `Mesh Renderer`, set the mesh to your Lod_# mesh + Add some type of `Collider` and configure accordingly.

Now let's put these prefab in the folder `Unity/ModsForMe/TestMod/Bundles/Objects/Large/MyFirstBuilding` in Unity. You can also store the source in `.../Source/...` as opposed to directly in`.../Bundles/...` (This is my personal preference).
The folder should look similar to this.
![[IMG_9263.jpeg|Prefabs, from Nelson]]

### Making the .dat files
`YourObjectName.dat` is where you configure the asset properties.
* **GUID**(**G**lobal **U**nique **ID**entifier) - a random unique id, you can use [online generators](https://www.guidgenerator.com/) to generate it.
* Type - the type of the Object. Small, Medium, Large, Decal, NPC. We are making a building which is Large.
* ~~ID - a unique id ranging from 0 - 65535~~. IDs are not required for Objects(specifically) and have been phased out.
* Landmark\_Quality - Off, Low, Medium, High, Ultra. As this is a building we will use Medium.
* LOD - Area, Mesh. Mesh uses the bounding box of the mesh as the area there are other properties to modify it but it is all numbers and practically impossible to visualize. Area uses the Occlusion Areas named "Occlusion" as the areas to apply the bias on.
* LOD\_Bias - How much to reduce the lod by. The higher the more detailed vice versa.

```title:MyFirstBuilding.dat
// Hypens are not required, it is up to your preference.
GUID 01de685f-0009-418a-ace8-637ad3063a7f

Type Large
Landmark_Quality Medium
LOD Area
LOD_Bias 0.8
```

`SomeLanguage.dat` is where you configure localization 
```title:English.dat
Name My First Building!
```
### What Next?
Now you should have English.dat and MyFirstBuilding.dat. For now, store them somewhere where you can easily access. For the next guide, I will show you how to bundle your assets and use these dat files to finally get your assets in game!

***

(Proofread: 2024/04/24)\
Sources: [Official Documentation: Object Assets](https://docs.smartlydressedgames.com/en/stable/assets/object-asset.html)\
Example Files: .../Objects/Large/Buildings

[^1]: yi
