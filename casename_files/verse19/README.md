these train/test sets are split w.r.t. patients

The abbreviation "w.r.t." stands for "with respect to." 
In this context, it means that the split is done in such a way that all images or data 
from a single patient are entirely in either the training set or the test set, but not both.

In medical imaging, ensuring that the train/test split is done with respect to patients is crucial.

If images from the same patient were included in both the training and test sets, 
the model might simply memorize patient-specific features rather than learning generalizable patterns. 
