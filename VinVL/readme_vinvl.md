# Image attribute extraction with VinVl

## Link : https://github.com/microsoft/scene_graph_benchmark

VinVL stands for Visual Representations in Vision-Language Models is an improved object detection model to provide object-centric representations of images. Compared to the most widely used bottom-up and top-down model (code), the new model is bigger, better-designed for VL tasks, and pre-trained on much larger training corpora that combine multiple public annotated object detection datasets. Therefore, it can generate representations of a richer collection of visual objects and concepts.

## How to use:

In order to configure VinVL it is better to run it on a Collab environment since it requires a GPU. All the installations needed for a safe execution are on the notebook (!pip install)

Once all the installation is done, mount your drive and correct the link reffering to the data (It must be on your drive, however, you can change it if you want).

Replace the file "demo_image.py" by the one in our repository (just drag and drop the file) in the colab directory. This step is our modification in the VinVL source code in order to extract the boundary.

Run the code and save the dataframe.
