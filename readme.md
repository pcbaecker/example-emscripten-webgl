# Emscripten and WebGL example

This small project demonstrates a simple application that runs as normal Desktop application as well as WASM script in the browser.

For opening the window and creating an OpenGL context, the framework GLFW is used.

The following command builds the emscripten files:

    mkdir cmake-build-emscripten
    cd cmake-build-emscripten
    emcmake cmake ..
    make
    
To start the generated WASM in the Browser, open the .html file in the cmake-build-emscripten/ folder