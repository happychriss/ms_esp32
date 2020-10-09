How to build/extract Tensorflow Light Files from Tensorflow for ESP32 on Arduino Platform
========================================================================================

All information and full credit goes to following webpages:

https://towardsdatascience.com/tensorflow-meet-the-esp32-3ac36d7f32c7
https://eloquentarduino.github.io/2020/01/easy-tinyml-on-esp32-and-arduino/


Build Library
------
The objective is not to build an actual binary, but to extract the right c-files, defines and 
headerfiles for the relevant platform.
1) Clone Tensorflow libary and build example
```bash
git clone https://github.com/tensorflow/tensorflow.git
cd tensorflow
make -f tensorflow/lite/micro/tools/make/Makefile TARGET=esp generate_projects
```

Prepare library (error on build)
------------------------------
When getting *build-error* on an example, just exclude from build by removing the Makefile.inc in the relevant example folder and rerun make.

```bash
mv tensorflow/lite/micro/benchmarks/Makefile.inc Makefile.inc.bak 
```
Adjust file to Platformio.io folder structure and make buildable for Arduino
---------------------------------------------------------------
The generates files are available per project in below folder and need to be copied the platformio. structure
as in this example project
Copy/update files from: 
```bash
Projects/ML/tensorflow/tensorflow/lite/micro/tools/make/gen/esp_xtensa-esp32/prj/micro_speech/esp-idf
```
            