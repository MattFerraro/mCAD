# mCAD

This is an experiment to see if I can create a new open source 3D CAD program that includes CAD, CAM, and FEA.

# Vision

## User Experience

The main idea is that the interface should be highly discoverable. Anyone who has even the tiniest amount of experience modeling in any 3D CAD software should immediately be able to hit the ground running, discovering the right buttons as they go. Any mechanical engineer should be able to open the editor, design a simple part, run FEA and see the outputs, then patch the design and finally create toolpaths. Ideally the UI makes this so easy to do that you don't even need to watch a tutorial. You do need to have experience with what those concepts are.

The UI will be written in Javascript using a 3D rendering library like three.js. It may be necessary to use something much lower level such as webGL or webGPU directly.

## File Interoperability

It is a requirement that mCAD be able to read and write a few major file formats:
- step
- stl
- obj
- whatever freeCAD supports

## Local vs Cloud

The codebase shall be runnable locally. Anyone with node should be able to clone the repo, perform the setup, and get modeling immediately. Perhaps docker will be required.

There will also be a version packaged up using something like Electron so that non-coders will be able to run it. This version shall be runnable even without an internet connection.

Lastly I will run a cloud-hosted version which anyone will be able to access online.

## User Accounts and Data Hosting

The code shall be runnable by anyone without requiring them to register as a user. If someone does want to register as a user, they will be able to sync their files to the cloud and access the files anywhere just by signing in.

For people with extra-secret data, I will build an integration with AWS/GCP/Azure to enable "bring your own cloud" support.

If you are using the electron client or running the code locally, all files required for storing the 3D parts and assemblies will be stored locally in an appropriate format. There will be no need to "download as file".


# Implementation

## UI

Javascript, React, three.js. Make this as standard and modern as possible because there are so many more programmers who are proficient with this stack than with Qt or anything like that.

## 3D kernel

FreeCAD uses [open-cascade](https://www.opencascade.com/open-cascade-technology/). I believe this is a great choice.

## CAM

Not sure yet. There are many [open source CAM options](https://www.reddit.com/r/CNC/comments/aizatc/free_and_open_source_camcnc_software/).

## FEA

There are several [open source FEA options](https://en.wikipedia.org/wiki/List_of_finite_element_software_packages).

One standout is [Calculix](https://en.wikipedia.org/wiki/Calculix) which is capable of producing its own meshes given stl files. Many solvers, for example NASTRAN, need to use a third party library to go from solid object to mesh.