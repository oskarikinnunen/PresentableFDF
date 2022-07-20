# PresentableFDF
Presentable version of my FDF project.

My implementation of the "FDF" project. Simple 3D elevation map renderer written in pure C.
Simple explanation of the project limitations for those "not in the know":
We can only use some permitted functions from the standard c-libraries, in this case:
  - open, read, write, close
  - malloc, free
  - exit
  - Functions defined in the **math.h** header
  - Functions defined in the **mlx.h** header. MLX is a very simple graphics library which only permits drawing images "one pixel at a time".
    This means we had to implement our own DDA or Bresenham algorithm for drawing lines.

Bonus features:
- Multithreading (pthread.h)
- Animation (time.h)
- Compiles for multiple platforms (Linux, OS X)

![fdf42](https://user-images.githubusercontent.com/45420297/179907128-cbcf6c52-0e44-473e-9c39-92b2f6c06beb.gif)

![fdfmars30fps](https://user-images.githubusercontent.com/45420297/179907145-2e6dbf4d-a7c1-48c9-9812-9253d30d31e3.gif)

(The performance is much better than it seems in these gifs.)
