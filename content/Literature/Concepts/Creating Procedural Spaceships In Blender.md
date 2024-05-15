---
tags:
  - blender
  - spaceship
  - space
  - procedural
  - programming
  - python
  - code
  - userguide
---

## Basic User Guide
1. Create Base Shape with MetaBalls
2. Convert Metaball to Mesh
3. Add Modifiers in this order
	1. Cast modifier
	2. Simple Deform modifier
	3. Remesher modifier (Blocks)
	4. Subsurface modifier (Simple, detail 1)
	5. Smooth modifier
	6. Bevel modifier (set angle to 15 degrees)
	7. Mirror modifier (check the axis that fits the best)
4. Play with the modifiers, mainly the deformers, like the CAST or Simple Deform. (1st 2 modifiers that we added)
5. For more organic ships, you can turn off the subdivision surface modifiers and check on smooth on the remesher modifier
6. KEY TIP
	1. if you want more variation to your ships, you can add more modifiers, they need to be placed between the first CAST modifier and the REMESH modifier
7. Check the vertex boxes to see the changes live while in edit mode
8. OPTIONAL
	1. you can now add more meshes or move the mesh around in edit mode and instantly see the changes previewed live
	2. Don't worry about weird uvs or odd shapes, the remesh modifier will work it out
9. TIP
	1. you can turn off all overlays for a clean, minimal experience, by clicking the arrow icon here
	2. Use proportional editing for faster iteration, do e key to extrude or g key to grab it and move it around

#### User Properties
We need to give users more controls over the spaceship as well as the generation of the initial shape. For the initial shape, the user should be able to randomly generated a set number of metaballs with different sizes and shapes to get different starting configurations for the spaceship.

There should be 3 options above the generate spaceship button.
1. A switcher
	1. to swap between sphere, cube, cone, or cylinder as the base frame (bounds) to generate meta balls inside of
2. a slider
	1. to control the amount of metaballs to be generated within the bounds of the above chosen bounds mesh
3. a slider
	1. to dictate the scale of the spaceship to work on. from 1m to 1000m extents. (this controls the size of the bounds mesh and in turn, the metaballs generation within those bounds)

Also, we need to expand the current user properties from only having meta_size, cast_strength, simple_deform_angle, and bevel angle, to including these
1. Cast
	1. should have easy access to swap shape
	2. axis switching
	3. factor control
2. Simple Deform
	1. Control for switching between twist, bend, taper, and stretch
	2. control for angle degree
	3. control for switching axis
3. Mirror
	1. control for easy switching axis
		(rest of mirror controls can be accessed directly through modifier panel already, so no need to include those at the moment)