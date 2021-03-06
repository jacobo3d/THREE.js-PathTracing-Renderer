# THREE.js-PathTracing-Renderer
Real-time PathTracing with global illumination and progressive rendering, all on top of the Three.js WebGL framework. <br>

<h2>LIVE DEMOS</h2>
A scene showing different quadric (mathematical) shapes and materials [Quadric Geometry Demo](https://erichlof.github.io/THREE.js-PathTracing-Renderer/ThreeJS_PathTracing_Renderer_QuadricGeometryShowcase.html) <br>
This demo renders the famous [Cornell Box](https://erichlof.github.io/THREE.js-PathTracing-Renderer/ThreeJS_PathTracing_Renderer_CornellBox_DirectLighting.html) <br>
For comparison, here is a real photograph of the original Cornell Box: http://www.graphics.cornell.edu/online/box/measured.jpg <br>
<br>
A demo featuring a [Physical Sky Model](https://erichlof.github.io/THREE.js-PathTracing-Renderer/ThreeJS_PathTracing_Renderer_SkyModel.html) <br>
<h3>Materials Demos</h3>
These demos showcase different materials possibilities: <br>
Refractive (glass/water) and ClearCoat (billiard ball/car paint) materials: [Materials Showcase #1](https://erichlof.github.io/THREE.js-PathTracing-Renderer/ThreeJS_PathTracing_Renderer_MaterialsShowcase_1.html) <br>
Volumetric (smoke/fog/gas) and Metallic (aluminum mirror) materials: [Materials Showcase #2](https://erichlof.github.io/THREE.js-PathTracing-Renderer/ThreeJS_PathTracing_Renderer_MaterialsShowcase_2.html) <br>
Diffuse (matte wall paint/chalk) and Translucent (skin/balloons,etc.) materials: [Materials Showcase #3](https://erichlof.github.io/THREE.js-PathTracing-Renderer/ThreeJS_PathTracing_Renderer_MaterialsShowcase_3.html) <br>
Metallic (Gold) and shiny SubSurface scattering (polished Jade/wax candles) materials: [Materials Showcase #4](https://erichlof.github.io/THREE.js-PathTracing-Renderer/ThreeJS_PathTracing_Renderer_MaterialsShowcase_4.html) <br>
<br>

![](threejsPathTracing.png)

<h2>FEATURES</h2>
* Real-time interactive Path Tracing in your Chrome browser - even on your smartphone! ( What?! )
* First-Person camera navigation through the 3D scene.
* When camera is still, switches to progressive rendering mode and converges on a photo-realistic result!
* The accumulated render image will converge at around 1,000-2,000 samples (lower for simple scenes, higher for complex scenes).
* Direct lighting now makes images render/converge almost instantly!
* Support for: Spheres, Planes, Discs, Quads, Triangles, and quadrics such as Cylinders, Cones, Ellipsoids, Paraboloids, Hyperboloids, Capsules, and Rings/Torii.
* Basic support for loading models in .obj format (triangle and quad faces are supported, but no higher-order polys like pentagon, hexagon, etc.)
* Current material options: Metallic (mirrors, gold, etc.), Refractive (glass, water, etc.), Diffuse(matte, chalk, etc), ClearCoat(cars, plastic, billiard balls, etc.), Translucent (skin, leaves, etc.), Subsurface w/ shiny coat (jelly beans, cherries, white glue, polished Jade, etc.), Volumetric (smoke, dust, fog, etc.)
* Diffuse/Matte objects use Monte Carlo integration (a random process, hence the visual noise) to sample the unit-hemisphere oriented around the normal of the ray-object hitpoint and collects any light that is being received.  This is the key-difference between path tracing and simple old-fashioned ray tracing.  This is what produces realistic global illumination effects such as color bleeding/sharing between diffuse objects and refractive caustics from specular/glass/water objects.
* Camera has Depth of Field with real-time adjustable Focal Distance and Aperture Size settings for a still-photography or cinematic look.
* SuperSampling gives beautiful, clean Anti-Aliasing (no jagged edges!)
* Users will be able to use easy, familiar commands from the Three.js library, but under-the-hood the Three.js Renderer will use this path tracing engine to render the final output to the screen.


<h2>TODO</h2>
* Instead of scene description hard-coded in the path tracing shader, let the scene be defined using the Three.js library
* Allow variable triangle counts in fragment shader due to varying .obj file model complexity.
* Consider splitting up triangle list DataTexture into multiple textures for higher-poly-count models.  Current texture width/size limit is 4096 for Android (that's 4096 / 3 vertices per triangle / 3 floating-point coordinates per vertex = 455 possible triangles.  Need to increase this limit to 100,000 (or more) possible triangles somehow.  Maybe data going in the texture's v direction in addition to the u direction?
* Implement AABB BVH (bounding volume hierarchy) for object/primitive culling, especially to speed up .obj model rendering.
* Dynamic Scene description/BVH updating and streaming into the GPU path tracer via Data Texture.
* Until a decent BVH is implemented, triangle models are not included in the GitHub repo demo (although they load and render perfectly, the frame rate is still too low, especially with models of 100 or more triangles).

<h2>ABOUT</h2>
* This began as a port of Kevin Beason's brilliant 'smallPT' ("small PathTracer") over to the Three.js WebGL framework.  http://www.kevinbeason.com/smallpt/  Kevin's original 'smallPT' only supports spheres of various sizes and is meant to render offline, saving the image to a PPM text file (not real-time). I have so far added features such as real-time progressive rendering on any device with a Chrome browser, FirstPerson Camera controls with Depth of Field, more Ray-Primitive object intersection support (such as planes, triangles, and quadrics), and support for more materials like ClearCoat and SubSurface. 

This project is in the alpha stage.  More examples, features, and content to come...
