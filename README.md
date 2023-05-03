Download Link: https://assignmentchef.com/product/solved-cs180-assignment6-rendering-image-by-ray-tracing
<br>
In the second half of the class, we will focus on rendering image by ray tracing. One of the most important operations in ray tracing program is to find the ray-object intersection. Once we find an intersection of one ray, we can perform the shading and return the pixel color. In this assignment, we need to implement two parts: ray generation and ray-triangle intersection. The general work flow of the current code base is:

<ol>

 <li>Start from main We define the parameters of our scene. Add objects (spheres or triangles) to our scene, and set their material. Add the light sources to the scene.</li>

 <li>Call Render(scene) Inside a loop which iterates through all the pixels, generate rays, and save the returned color inside a framebuffer. Finally the framebuffer is saved inside an image.</li>

 <li>Later, we generate a ray through the pixel and call the CastRay function, which calls trace to find the intersection of ray and the closest object in the scene.</li>

 <li>Then we perform shading at this shading point. We have three different shading cases, and already provide the code for you.</li>

</ol>

The functions you should modify are:

<ul>

 <li>Render() <strong>in the Renderer.cpp</strong>: You need to generate one ray for each pixel here, and call the function castRay(), which will return the color, and store the color in the corresponding pixel of the framebuffer.</li>

 <li>rayTriangleIntersect() <strong>in the Triangle.hpp</strong>: v0, v1, v2 are the three vertices of the triangle, orig is the origin of the ray, dir is the direction(normalized) of the ray. tnear, u, v are the parameters (t, b1 and b2, respectively) that you need to update as the output of the Moller-Trumbore algorithm we derived in the class.</li>

</ul>

<h1>1           Getting started</h1>

In this assignment, you will have a new code base, the only dependency of the start code is CMake. We believe all of you are able to work on your own machine now.

Please download the project’s skeleton code, and build the project by using the following commands:

$ mkdir build $ <strong>cd </strong>./ build $ cmake . .

$ make −j4

After this, you should be able to run the given code by using <strong>./Raytracing</strong>.

There a few classes in our code base now. Some general introductions are:

<ul>

 <li>hpp: Some functions or variables we use across the classes.</li>

 <li>hpp: Since we no longer use the Eigen library, we provide the common vector operation here, such as: dotProduct, crossProduct, normalize.</li>

 <li>hpp: The parent class of a primitive we can render. Triangle and Sphere classes are inherit from this base class.</li>

 <li>hpp: Define the scene to be rendered. Including setting options and object list and lights list.</li>

 <li>hpp: The main renderer class, which implements all ray tracing operations.</li>

</ul>