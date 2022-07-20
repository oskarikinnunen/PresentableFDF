# PresentableFDF
Presentable version of my FDF project.

My implementation of the "FDF" project. Simple 3D elevation map renderer written in pure C.

Simple explanation of the project limitations for those "not in the know":
We can only use some permitted functions from the standard C-libraries, in this case:
  - open, read, write, close
  - malloc, free
  - exit
  - Functions defined in the **math.h** header
  - Functions defined in the **mlx.h** header. MLX is a very simple graphics library which only permits drawing images "one pixel at a time".
    This means we had to implement our own DDA or Bresenham algorithm for drawing lines. (And much more of course)

Simplified program flow: 
  Parse the file that was passed as an argument to the program. This is represented as a "triangle map" (t_tri_map) in the rest of the program.
  https://github.com/oskarikinnunen/PresentableFDF/blob/0923fc5dbccb9ca6cd9a09a7fb38ff9cc471084b/include/fdf.h#L72-L78


Bonus features:
- Multithreading (pthread.h)
- Animation (time.h)
- Compiles for multiple platforms (Linux, OS X)

![fdfds60](https://user-images.githubusercontent.com/45420297/179911355-5eb79608-b708-4231-bf32-67f9faf2de2e.gif)

![fdfmars30fps](https://user-images.githubusercontent.com/45420297/179907145-2e6dbf4d-a7c1-48c9-9812-9253d30d31e3.gif)

(The performance is much better than it seems in these gifs.)
