## 安装OpenGL Library
+ `sudo apt-get install build-essential`
+ `sudo apt-get install libgl1-mesa-dev`

## 安装OpenGL Utilities

+ `sudo apt-get install libglu1-mesa-dev`
> OpenGL Utilities 是一组建构于 OpenGL Library 之上的工具组，提供许多很方便的函式，使 OpenGL 更强大且更容易使用。

## 安装OpenGL Utility Toolkit
+ `sudo apt-get install libglut-dev`
> OpenGL Utility Toolkit 是建立在 OpenGL Utilities 上面的工具箱，除了强化了 OpenGL Utilities 的不足之外，也增加了 OpenGL 对于视窗介面支援。
注意：在这一步的时候，可能会出现以下情况，shell提示：
> 1. Reading package lists... Done
> 2. Building dependency tree
> 3. Reading state information... Done
> 4. E: Unable to locate package libglut-dev

> 将上述
  > `sudo apt-get install libglut-dev` 命令改成 `sudo apt-get install freeglut3-dev` 即可。	 

## 测试

> 示例test.c源码：
```
#include <GL/glut.h>
void init(void)
{
	glClearColor(0.0, 0.0, 0.0, 0.0);
	glMatrixMode(GL_PROJECTION);
	glOrtho(-5, 5, -5, 5, 5, 15);
	glMatrixMode(GL_MODELVIEW);
	gluLookAt(0, 0, 10, 0, 0, 0, 0, 1, 0);
	return;
}

void display(void)
{
	glClear(GL_COLOR_BUFFER_BIT);
	glColor3f(1.0, 0, 0);
	glutWireTeapot(3);
	glFlush();
	return;
}

int main(int argc, char *argv[])
{
	glutInit(&argc, argv);
	glutInitDisplayMode(GLUT_RGB | GLUT_SINGLE);
	glutInitWindowPosition(0, 0);
	glutInitWindowSize(300, 300);
	glutCreateWindow("OpenGL 3D View");
	init();
	glutDisplayFunc(display);
	glutMainLoop();
	return 0;
}
```

## 编译程式时，执行以下指令：
> `gcc -o test test.c -lGL -lGLU -lglut`

## 执行

+ `./test`
