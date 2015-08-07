# Stage3DtoPNG
Utility class for rendering out the content of the Stage3D.context3D to a PNG file. It works great for creating image sequences for any phase of your rendering. You can have as many instances of Stage3DtoPNG as you need. Saving files only works with air apps and not with browser plugins. You can develop in air and target the browser later if you need to. This works with all frameworks built on top of the Stage3D API. 

Usage:

For every sequence of images you require, create an instance of the class:

- import com.util.Stage3DtoPNG;
- private var pngRender:Stage3DtoPNG;


You have a few options when first creating the render pertaining to the bitmap ( width, height, useRGBA ). The width and height should be set to your contex3D.backBuffer width and height. Setting your width and height larger will not scale your image, if it is smaller your image will be cropped. By default useRGBA is false for speed, this creates a 24bit image. If useRGBA is set to true then 32bit png will be created. 


For 24bit png use:

- pngRender = new Stage3DPNG( viewWidth, viewHeight );


For a 32bit png use:

- pngRender = new Stage3DtoPNG( viewWidth, viewHeight, true);


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

If you are using a framework built on top of Stage3D such as Away3D, Citrus, Flare, Starling, Zest, etc... You just need to access the context3D that particular framework is using. ( ie. Straling.context )  You may have to do a little digging to find how,where, and when to access your frameworks context3D. In the future I will update the documentation with examples of popular frameworks.

In closing:
Yes you can have multiple pngRenders sending files to different folders with different names. This can be useful if you need to render out different phases of your frame. 

The easiest way to turn off the creation of pngs during development is to comment out the .initRenderFile(...)
An error message will be traced but no file will be created.

When you want to resume png creation you can simply uncomment the line.

You can keep up with any further developments here:
https://github.com/dawsonmv/Stage3DtoPNG.git

If you have not already please contribute to further development here:
http://www.dawsonvaldes.com/Stage3DtoPNG
