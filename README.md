# Nutrition facts chart detection
This GitHub contains a small dataset for the task of detecting the position of the nutritional facts chart of a product in an image.

## Dataset description
##### Size: 
This dataset contains **400** images.
##### Data description:
The images are natural close-up photographs of one side of food products with the nutritional facts box clearly visible.
Most of them are of spanish products.
Only 1 class is considered, which is `nutritional_facts_chart`
##### Data partition:
This dataset is divided into **90%** of the images (360) as the training set and **10%** (40) as the test set.

## Ground truth description
All images have been labeled by hand drawing the bounding box that contains the nutritional information box.
These annotations are provided in two formats:
- `pickle`: 1 `.pickle` file contains all the annotations. It is a `dict` in which the keys are the names of the images and the values are the bounding box associated with said image in the format `[y1,y2,x1,x2]`.
- `csv`: 2 `.csv` files contain the ground truth for the training and testing set, respectively. Each row contains the ground truth for 1 image in the format `[path, x1, y1, x2, y2, class]`

## Data download
You can download the data from [here](https://drive.google.com/file/d/15vnCd0pTIv489j_VpIx_cyTRuQYFTVUC/view?usp=sharing).
As some of the original images are two big, another lighter preprocessed version of the images is provided. In this lighter version of the dataset, all images have been standarized by adding black borders to make all of them squared and then resized to a common size of 512x512px. Of course, the ground truth has been adjusted accordingly. You can download it [here](https://drive.google.com/file/d/1HTX2dD-RGeqVaYgLfnqykPJ9HsUv3ZaM/view?usp=sharing)

## Examples
![Example1](/examples/imgs/ex1.jpg)
![Example2](/examples/imgs/ex2.jpg)
![Example3](/examples/imgs/ex3.jpg)

## Detection task
For this task, we used [fizyr's implementation of RetinaNet](https://github.com/fizyr/keras-retinanet) and [martinzlocha's anchor optimization for RetinaNet](https://github.com/martinzlocha/anchor-optimization/). From here and applying some algorithmic post-processing to the predicted bounding boxes, we achieve a 99.99% mean average precission (mAP) and 83.31% average intersection over union (IOU)
##### Examples
Here we show some examples of the bounding box inferred by the detector (red) against the ground truth (green)
![Example1](/examples/detections/ex1.jpg)
![Example2](/examples/detections/ex2.jpg)
![Example3](/examples/detections/ex3.jpg)

