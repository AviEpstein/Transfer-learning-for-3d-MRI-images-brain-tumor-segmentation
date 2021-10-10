# Transfer-learning-for-3d-MRI-images-brain-tumor-segmentation by Avi Epstein and Tomer shimshi

Brain tumor segmentation is a critical task for patient’s disease management.
Currently MRI’s are hand annotated by a neurologist which is highly time consuming and
sometimes prone to mistakes. In this article we attempt to solve the task of brain tumor
segmentation. Given the Multimodal Brain Tumor Segmentation Challenge (BraTS) 2019
training dataset. To achieve this goal we have used the backbone of a pretrained resnet
nammed Med3Dl net(link) this pretrained network was trained on a diverse set of medical 3d
images acquired from x-ray CT and MRI to generally segment internal body parts. We use this
backbone for transfer learning on our 4 different types of MRI input images (T1,T1ce,T2,Flair)
each one of these input images is inserted to the mednet and concatenated at the output. Doing
this achieves good global segmentation of the different parts of the brian but is not specific
enough to segment the exact tumor. Hence we have combined this system to a unet inspired
network (Unets are known for their high results in segmentation problems especially for medical
purposes) we then take our initial 4 3d inputs and down convolve them to the size of output of
the med3Dnet and concatenate,we then upconvlove and cancatinat again. repeating this
process 3 times until we reached the label size containing the segmentation of the tumor(4
segmentations :ET - Enhanced Tumor, TC - Tumor Tore, WT - Whole Tumor and background).
Doing this we try to combine the best of both Resnet and Unet network architectures.
