# Stage3DtoPNG
Utility class for rendering out the content of the Stage3D.context3D to a PNG file. It works great for creating image sequences for any phase of your rendering. You can have as many instances of Stage3DtoPNG as you need. 

Usage:

For every sequence of images you require, create an instance of the class:

- import com.util.Stage3DtoPNG;
- private var pngRender:Stage3DtoPNG;


You have a few options when first creating the render pertaining to the bitmap ( width, height, transparency, fill ). Transparency defaults to true and the fill defaults to 0x00000000. The width and height should be set to your view width and height, if it is not your image will be cropped.


To preserve alphas do this:

- pngRender = new Stage3DPNG( viewWidth, viewHeight );


For no transparency and a black fill use:

- pngRender = new Stage3DtoPNG( viewWidth, viewHeight, false, 0xffffff);


Next you must initialize where the png sequence will be saved. A new directory will automatically be created inside the documents folder. To compress the png files set the last option to true. Compression takes a while so it is off by default.

!!!CAUTION!!! 
*** if you do not change the folder name or filename your files will be over written ***


By default the files will be saved in "/Documents/Stage3D_ouput", file name "RenderedFrame_x.png”, no compression:

- pngRender.initRenderToFile();


Here the files are saved to "/Documents/MyRenders" with the name "output_frame_x.png”:

- pngRender.initRendertoFile("MyRenders","output_frame");


Here the files are saved to "/Documents/small_renders" , as "frame_x.png” , and compression on:

- pngRender.initRenderToFiles("small_renders","frame",true);


Placing the function call to render the png is up to you. The png is created from the back buffer. It must be called before your context3D.present() is called because this clears out the back buffer. You must pass a context3D to render the file, the back buffer of the context3D will be rendered in its current state:

- pngRender.renderToFile( context3D );


In closing:
Yes you can have multiple pngRenders sending files to different folders with different names. This can be useful if you need to render out different phases of your frame. 

The easiest way to turn off the creation of pngs during development is to comment out the .initRenderFile(...)
An error message will be traced but no file will be created.

When you want to resume png creation you can simply uncomment the line.

You can keep up with any further developments here:
https://github.com/dawsonmv/Stage3DtoPNG.git

If you have not already please contribute to further development here:
http://www.dawsonvaldes.com/Stage3DtoPNG
