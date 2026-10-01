  This project includes a 3D file viewer based on the Babylon.js script. Babylon.js is a free and open‑source 
product distributed under the Apache 2.0 license, therefore the Apache 2.0 license is inherited.

  You can use use this file from-the-box as web 3D-viewer that currently handles GLB, FBX, STL, OBJ formats.
  
  In addition to using it as is, you can use the js-code in the file to create 3D media forms on your web pages.
The 3D-form is implemented as a function that can be called anywhere in the HTML-document and includes the following 
input parameters: width, height, zoom, tilt angle, rotation angle, background color, enabling/disabling UI display, 
and the path to the source 3D-model file, you can also send paths to PNG icon files as parameters of function to display 
them as menu elements.

-----------------
Project contains:
-----------------
.../<br>
offline/scripts/babylon.js<br>
offline/scripts/babylonjs.loaders.min.js<br>
offline/offline_3DViewer.html<br>
3D_media_form.html<br>


-----------
How to use:
-----------
1. Using as 3d-viewer and animation player (GLB, FBX, STL, OBJ).<br>
   
  If you want to use this as offline web 3D-viewer u need to get an offline_3DViewer.html file (or you can change main 
3D_media_form.html's strings:<br>
```
<script src="https://cdn.babylonjs.com/babylon.js"></script>  
<script src="https://cdn.babylonjs.com/loaders/babylonjs.loaders.min.js"></script>  

                                     to  

<script src="scripts/babylon.js"></script><br>
<script src="scripts/babylonjs.loaders.min.js"></script> )<br>
```
And also you need to get "script/" folder to  your project.
  If you want to use this online then you need to get only 3D_media_form.html.
  
2. Using scripted js-function from HTML file at your projects.

  If u want to show 3D models in best racurses on your site. 

- First: You need to launch HTML version of 3D-viewer, open your model, 
then press "rec" trigger button when you find best racurse trough changes 
done by control arrows, and take values from opened data field layer 
( rotation: XXX, elevation: XXX, zoom: XXX).

- Second: You need to copy into your HTML-file <styles>...</styles> block
and main functions block from <body><script>...</script></body> block.

- Third: You can use function in your own HTML file like this:

1) Example of call of an 3D-viewer function with flows up menu and navigation keys:
```   
<body>
<script>...</script> //Main js-functions block just copy it to your project 
```
``` 
<div id="media-form-1"></div>
<script>
  window.mediaForms = window.mediaForms || [];
  window.mediaForms.push(create3DMediaForm(document.getElementById("media-form-1"), {
    size: [480, 300],                 // output window size [w, h]
    zoom: 1.0,                        // camera zoom
    elevationDeg: 30,                 // camera elevation angle above the horizon
    rotationDeg: 0,                   // initial model rotation angle (degrees)
    backgroundColor: "000000",        // form background color, hex "XXXXXX"
    showUI: true,                     // true = full interface, false = bare 3D form without the UI
    // input model (GLB). If there is no internet access, choose a file via the bottom menu.
    modelUrl: "https://raw.githubusercontent.com/KhronosGroup/glTF-Sample-Assets/main/Models/CesiumMan/glTF-Binary/CesiumMan.glb",
    pics: window.M3D_PICS //you can add 20x20 pixels PNG-files at folder "pics/" (optional)
  }));
</script>
...
</body>
```
Optional: You can add directory "pics/" (current path could be changed at the end of main functions block)
that includes:<br>

  forward:     "pics/Arrow_button_forward_pic.png",  // png pictures with alpha channel<br>
  backward:    "pics/Arrow_button_backward_pic.png", // (built-in placeholders are used if missing)<br>
  left:        "pics/Arrow_button_left_pic.png",<br>
  right:       "pics/Arrow_button_right_pic.png",<br>
  up:          "pics/Arrow_button_up_pic.png",<br>
  down:        "pics/Arrow_button_down_pic.png",<br>
  modelArrow:  "pics/Context_model_browse_menu_arrow_pic.png",<br>
  animArrow:   "pics/Context_animation_menu_arrow_pic.png",<br>
  play:        "pics/Play_animation_button_pic.png",<br>
  stop:        "pics/Stop_animation_button_pic.png"<br>

2) Example of call of an 3D-media form function at table layouts (you can only rotate
your model that showns when drag mouse left or right with presed left mouse button):
```
<body>
<script>...</script> //Main js-functions block just copy it to your project 
```
```
<table class="m3d-demo">
  <tr>
    <td>
      <div id="media-form-2"></div>
      <script>
        window.mediaForms.push(create3DMediaForm(document.getElementById("media-form-2"), {
          size: [480, 300],           //size in pixels  of 3D-media form [Width, Height]
          zoom: 1.0,                  //put here value that you saved from zoom: XXX field and divided by 100
          elevationDeg: 30,           //put here value that you saved from elevation: XXX field
          rotationDeg: 0,             //put here value that you saved from rotation: XXX field
          backgroundColor: "000000",  //Color of background to show 
          showUI: false,              //turns off menus and all information, leaves only 3D model shown on background
          modelUrl: "https://url.of.your/glb_file.glb",
          pics: window.M3D_PICS
        }));
      </script>
    </td>
  </tr>
</table>
```
```
...
</body>
```
</body>
**/
