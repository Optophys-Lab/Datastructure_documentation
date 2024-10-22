# SurgeryPlanner
This is a tool designer for planning injection/implantation surgeries in rodents.

One can enter the desired coordinates and angles and the tool will calculated the entry point and visualize the path.
The tool requires [atlas files](AdminCommander.md#copy-brain-atlases) to work properly. Mouse and Rat atlas files are available.

Available atlases:
- Waxholm Space Atlas of the Sprague Dawley Rat Brain (39um resolution)
- Waxholm Rat Atlas modified to fit the stereotactic atlas (Rotated such that bregma and lambda are flat, 39um resolution)
- AllenMouse10 Atlas (10 um resolution)
- AllenMouse10 IBL Adjustments (10 um see <https://github.com/petersaj/neuropixels_trajectory_explorer>)

Atlas information can also be accessed from DB via DB.BrainAtlas and DB.BrainRegionAnnotation.BrainRegion 
region delineations are available there.

:::{note}Start
From the datastructure_tools directory run
~~~bash
python ./SurgeryPlanner.py
~~~
:::

:::{error}
The Tool is very experimental atm. If anybody is interested in using it, please contact Artur. 
:::

todo pics
~~~~
written by: Artur
last modified: 2024-10-22
~~~~