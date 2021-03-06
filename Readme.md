*This repository is a mirror of the [component](http://component.io) module [scottcorbett/histogram](http://github.com/scottcorbett/histogram). It has been modified to work with NPM+Browserify. You can install it using the command `npm install npmcomponent/scottcorbett-histogram`. Please do not open issues or send pull requests against this repo. If you have issues with this repo, report it to [npmcomponent](https://github.com/airportyh/npmcomponent).*
# histogram

  A CommonJS module written for component(1) to create image histograms from images or canvas objects. [Example](http://hexhour.com/toys/histogram/)

## Installation

    $ component install scottcorbett/histogram

## Example

   Simple example using a DOM image  
   
    var histogram = require("histogram");  
    var result = histogram().forImg(document.getElementById("source_img"));  
    var img = document.createElement("img");
    img.src = result;  

   Calling setRGB manually to keep count of tone values
   
    var histogram = require("histogram");  
    ...
    histogram().setRGB({r: 255, g:128, b:64});
    histogram().setRGB({r: 128, g:128, b:128});
    ...
    var result = histogram().draw();  
    var img = document.createElement("img");
    img.src = result;  

## API

###histogram([conf])
   Optional configuration object with any of the following values. Defaults are shown
   
    {       
      width : 255, // width of the resulting image.
      height : 128, // height of the resulting image.
      red: #d55, // colour used for red in the graph.
      green: #5d5, // colour used for green in the graph. 
      blue: #55d, // colour used for blue in the graph.
      black: #555 // colour used for portions of the graph overlapped by all colours  
    }
    
###.setConf(conf)
   Sets configuration used for drawing, expects an object the same as the constructor conf.
   
###.forImg(source)
   Creates an image histogram based off the img object passed in and returns a data url.
   
###.forCanvas(source)
   Creates an image histogram based off the canvas object passed in and returns a data url.
  
###.clearRGB()
   Clears the rgb values used to generated the histogram.
   
###.setRGB(val)
   Increments the RGB tone counts based off the object passed in. Expects an object in the this format; 
   
    {       
      r : 255,  
      g : 128,  
      b : 64  
    }
  
###.draw()
   Generates the histogram based off the RGB tone counts set and returns a data url for the resulting image.
   
## License

  MIT
