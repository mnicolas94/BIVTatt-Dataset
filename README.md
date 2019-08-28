# BIVTatt-Dataset

Dataset name: BIVTatt

The BIVTatt dataset contains 210 original images of tattoos, and 4200 generated images after applying 20 different types of transformations to the original images.

## Structure
The dataset is structured in the following folders:

[-images:](images) Contains the tattoo images. Each image file is named in the way "label_number<_transformation>.jpg", where "label" is the subject id, "number" is just a number to differentiate images from the same subject, and "transformation" is used in generated images to indicate the type of transformation and can be one of the following:

 - [a1; a2; a3; a4]: different configurations of affine transformations  	
 - [ar1; ar2; ar3; ar4]: different configurations of aspect ratio transformations  	
 - [b1; b2]: different configurations of blurring transformations  	
 - [c1; c2; c3; c4]: different configurations of color transformations  	
 - [i1; i2]: different configurations of illumination transformations  	
 - [r1; r2; r3; r4]: different configurations of rotation transformations
	
The dataset augmentation was done using the [Imgaug](https://github.com/aleju/imgaug) library.

[-bounding_boxes:](bounding_boxes) Contains files with the bounding boxes of each tattoo. Each file have the same name of the corresponding image. Each line of a file corresponds to a bounding box of a tattoo in the image. Each line is composed of four numbers separated by a space in the following way:  
x1 y1 x2 y2  
, where [x1, y1] is the coordinate of the top-left corner of the bounding box, and [x2, y2] is the coordinate of the bottom-right corner.

The identification protocol we use with this dataset is as follows. We use the cropped tattoos, not the entire image. The probe set consists of the transformed images and for each one, the gallery is composed of all the original images, except for the image that originate that transformed image. Thus, we simulate a real scenario of forensic identification. Specifically, the probe set consists of 1540 images and the gallery of 209 images. Note that exists a total of 4200 transformed images, but only 1540 were used in the probe set. This is due to the fact that not all tattoo original images have a matching original image pair. So, for their transformed images, there is not a matching pair either in the gallery. Also, for images that contain more than one tattoo, we just use the first annotated tattoo, i.e., the tattoo that has its bounding box annotated first in the bounding boxes file (the first annotated tattoo is the most relevant tattoo in the image).

## NOTES
-The bounding boxes for some generated images are not accurate. This is because the boxes where calculated from the transformation configuration. This the case for some images that were generated from affine and rotation transformations.

If you use this dataset, we recommend you to reference the following paper:

BibTeX:
@inproceedings{miguel19,
author={Nicolás-Díaz, Miguel, and Morales-González, Annette and Méndez-Vázquez, Heydi },
title={Deep Generic Features for Tattoo Identification},
booktitle={Iberoamerican Congress on Pattern Recognition},
year={2019},
organization={Springer}
}

If you have any doubt, please contact:  
Miguel Nicolás, mnicolas@cenatav.co.cu  
or  
Annette Morales, amorales@cenatav.co.cu  
or  
Heydi Méndez, hmendez@cenatav.co.cu
