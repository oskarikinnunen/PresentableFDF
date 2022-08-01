# FDF

My implementation of the "FDF" project. Simple 3D elevation map renderer written in pure C.

Simple explanation of the project limitations for those "not in the know":
We can only use some allowed functions from the standard C-libraries, in this case:
  - open, read, write, close
  - malloc, free
  - exit
  - Functions defined in the **math.h** header
  - Functions defined in the **mlx.h** header. MLX is a very simple graphics library which only permits drawing images "one pixel at a time".
    This means we had to implement our own DDA or Bresenham algorithm for drawing lines. (And much more of course)

Brief overview of the program:

  - Parse the file that was passed as an argument to the program. This is represented as a "triangle map" (t_tri_map) in the rest of the program.
  https://github.com/oskarikinnunen/PresentableFDF/blob/b6cfa9066d24f16314af8d93e0ba95db707a93e7/include/fdf.h#L72-L79
  - Make a copy of the original untransformed triangle map, apply some rotation matrices to it and save the z-buffer.
  https://github.com/oskarikinnunen/PresentableFDF/blob/59577c687b6b8890072dff99fa5af46af0a475db/src/map_operations.c#L80-L90
  - Split each triangle into two flat-sided subtriangles (flat bottomed triangle and a flat topped triangle) and draw them.
  
      ![bresen](https://user-images.githubusercontent.com/45420297/179927757-46084e1c-e6ed-4fc8-bc58-abbc53ef959f.png)
  *(Image depicting two triangles with the subtriangle dividing line drawn aswell)*
  https://github.com/oskarikinnunen/PresentableFDF/blob/adc59915e25313100e5695eae3d3769832919241/src/z_drawing.c#L33-L47
  - Fill the subtriangles with a scanline, using a bresenham algorithm.
  https://github.com/oskarikinnunen/PresentableFDF/blob/adc59915e25313100e5695eae3d3769832919241/src/z_drawing.c#L16-L31
  - That's pretty much it.


Bonus features:
- Z-buffer implementation
- Multithreading (pthread.h)
- Animation (time.h)
- Compiles for multiple platforms (Linux, OS X)

Gifs:

![fdfds60](https://user-images.githubusercontent.com/45420297/179911355-5eb79608-b708-4231-bf32-67f9faf2de2e.gif)

![fdfmars30fps](https://user-images.githubusercontent.com/45420297/179907145-2e6dbf4d-a7c1-48c9-9812-9253d30d31e3.gif)

(The performance is much better than it seems in these gifs.)
