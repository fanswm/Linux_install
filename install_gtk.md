## 安装GTK开发环境：
+ `sudo apt-get install libgtk2.0-dev`

## 查看 2.x 版本
+ `pkg-config --modversion gtk+-2.0` 
> 有可能需要`sudo apt-get install pkg-config`

## 查看是否安装了gtk
+ `pkg-config --list-all | grep gtk`

## 测试: hello_gtk.c
```
#include<gtk/gtk.h>
int main(int argc,char *argv[])
{
  GtkWidget    *window;
  gtk_init(&argc,&argv);
  window=gtk_window_new(GTK_WINDOW_TOPLEVEL);
	gtk_window_set_title(GTK_WINDOW(window),"hello!GTK");
	gtk_widget_show(window);
	gtk_main();
	return 0;
}
```

## 编译:
+ `gcc hello_gtk.c -o hello_gtk ``pkg-config --libs --cflags gtk+-2.0``
