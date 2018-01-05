# Bone Age Prediction
## Main Purpose
The main purpose of this project is to predict bone age of children based on hand x-ray images, using deep neural network. The data set comes from a children hospital, which has thousands of hand x-ray images. We also download the public data from the pediatric bone age assessment challenge held by RSNA. Data from RSNA has preciser ground truth (the label from this data set has the month unit), while ours is coarser (the unit of label is year).
We treat it as a regression problem. The input is a x-ray image of hand, the output is its bone age.
## Data format
Images from hospital are formated as DICOM (original data is compressed DICOM image), and data from RSNA are formated as PNG.
In our data set, there are about 7,000 male patients and 17,000 female patients. 
The training set given by RSNA is consist of 6833 male patients and 5778 female patients.
All the data has chronological age, gender and bone age (from the exam report) information.
## Main methods
In the 1st round, data without preprocessing was fed into CaffeNet. It seemed that the model could not converge. Loss was about 5~9.
======to be continued====
## Data preprocessing
Data directly from the PACS may include many noisy images, such as x-ray images of elbow, hand images with non-hand part. We should delete these images to increase our performance.
1. We firstly decompress the DICOM images using the gdcm library in Linux. Detail information can be seen in preprocess.py.
2. Convert these decompressed DICOM images into PNG files in batches, with an useful image management tool called [IrfanView](http://deanvaughan.org/wordpress/2013/05/how-to-batch-convert-dicom-to-jpeg/)
