<img src="https://img.shields.io/badge/C-A8B9CC?style=flat&logo=C&logoColor=white"/> <img src="https://img.shields.io/badge/C++-00599C?style=flat&logo=C++&logoColor=white"/> <img src="https://img.shields.io/badge/OpenGL-5586A4?style=flat&logo=OpenGL&logoColor=white"/>
# solar_system
This repository is about the fourth assignment of SKKU's 2021 Introduction to Computer Graphics. This project further developed the [moving_planets](https://github.com/dipreez/moving_planets) and implemented a more sophisticated solar system simulation program. The satellites and rings of each planet were rendered, the texture of the planets was loaded and bound to a sphere, and the sun was set as a light source to implement shading.

# Algorithms and data structures
## Dwarf planets
Some planets have dwarf planets orbiting around them. The number of dwarf
planets was made by referring to the example program presented on the course
website. The satellite's motion was simply implemented by applying the
translation matrix and rotation matrix one more time before applying the model
matrix.
## Shading
Planets are affected by point light source in (0,0,0). The part that looks at the
light source is bright, and the part that looks behind the light source is dark. It
was implemented using the Blin-Phong model learned during the lecture.
However, the sun is not shaded.
## Texturing
The planets have been textured. Used texture files from the site presented in
the assignment pdf (http://planetpixelemporium.com/planets.html). It is
implemented to bind a new texture when each time the planet is render.
Therefore, only two textures are bound at most at the same time.
## Ring system
Implemented a ring around Saturn. The ring is rotating at the same speed as
Saturn. Like planets, the ring has a texture. As suggested in the assignment pdf,
the ring is applied with alpha blending, making it looks translucent. The vertex
array of ring system is implemented as shown in the figure below.
More specifically, it is implemented by overlapping two rings, one with triangles
facing up and one with triangles facing down.
# Discussions
1. When implementing Saturn's ring, I first tried to make the normal vector of
the vertex of the ring the same as the normal vector of the triangle
(something like (0,0,1)). However, the normal vector became perpendicular
to the position of the light source, causing the ring to be almost unaffected
by light. To solve this problem, I set the normal vector as a vector from the
center of the ring to the corresponding vertex. Then the ring was properly
influenced by light, but I'm not sure if this is the right way.
2. Because this assignment uses textures, the program will not run normally
unless the texture file is in the correct path ("../bin/images/").
