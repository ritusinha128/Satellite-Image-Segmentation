# Satellite-Image-Segmentation

A pipeline for U-Net applied on satellite images as a part of the Kaggle DSTL Satellite Image segmentation challenge. Jaccard score of 0.77

# Dataset

The dataset is available on Kaggle as part of the DSTL Satellite Imagery Feature Detection challenge. It consists of 1km x 1km satellite images in both 3-band and 16-band formats. The 3-band images are the traditional RGB natural color images. The 16-band images contain spectral information by capturing wider wavelength channels. This multi-band imagery is taken from the multispectral (400 – 1040nm) and short-wave infrared (SWIR) (1195-2365nm) range. All images are in GeoTiff format. 

# Object types

The images have labeled 8 different classes:

1)Buildings - large building, residential, non-residential, fuel storage facility, fortified building
2)Misc. Manmade structures 
3)Road 
4)Track - poor/dirt/cart track, footpath/trail
5)Trees - woodland, hedgerows, groups of trees, standalone trees
6)Crops - contour ploughing/cropland, grain (wheat) crops, row (potatoes, turnips) crops
7)Waterway 
8)Standing water

Every object class is described in the form of Polygons and MultiPolygons, which are simply a list of polygons. These polygons are provided in GeoJSON and WKT format as well

# Model

The model is defined in the get_unet() function. The model is a modified implementation of the U-Net, a fully convolutional neural network used typically for biomedical segmentation. The model is called in the train-net() and check_predict() functions

# Evaluation Metric

The evaluation metric used is the Jaccard Index. It can be interpreted as a similarity measure between a finite number of sets. Since image segmentation task can also be considered as a pixel classification problem, we additionally use common classification loss functions.

# Prediction 

This can be done by calling the check_predict() function with the image band as the parameter passed. The output gives the masks of the various object classes on the particular image. The training and validation set split is done using make_val(). 

# Testing

The predict_test() can be called with with the model and trs as inputs. The resultant csv can be created using make_submit() function. The output can thus be obtained
