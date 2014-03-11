Information & Contact
=====================

This code was used to compute the results of the following paper:


"Efficient feature extraction, encoding and classification for action recognition",
Vadim Kantorov, Ivan Laptev,
In Proc. Computer Vision and Pattern Recognition (CVPR), IEEE, 2014

If you use this code, please cite our work:

@inproceedings{kantorov2014,
  author = {Kantorov, V. and Laptev, I.},
  title = {Efficient feature extraction, encoding and classification for action recognition},
  booktitle = {Proc. Computer Vision and Pattern Recognition (CVPR), IEEE, 2014},
  year = {2014},
}

For any question or bug report, please contact:
- Vadim Kantorov at vadim.kantorov@inria.fr or vadim.kantorov@gmail.com


Description and usage
=====================

We release two tools in this repository.

1. Extracting motion descriptors using motion vectors available from video compression ("motion_descriptors").
   Command-line options:
     -i $VIDEO_PATH 				specifies the path to the input video
     --hog yes/no (default: yes)		enables/disables HOG descriptor computation
     --hof yes/no (default: yes)		enables/disables HOF descriptor computation
     --mbh yes/no (default: yes)		enables/disables MBH descriptor computation
     -f $BEGIN-$END (default: whole film)	restricts descriptor computation to the frame range [$BEGIN, $END]

   The output format:
     The first two lines of the standard output are comments explaining the format):
     	#descr = hog(96) hof(108) mbh(96 + 96)
        #x y pts StartPTS EndPTS Xoffset Yoffset PatchWidth PatchHeight descr

     "x" and "y" are the normalized frame coordinates of the spatio-temporal patch
     "pts" is the frame number of the spatio-temporal patch center
     "StartPTS" and "EndPTS" are the frame numbers of the first and last frames of the spatio-temporal patch
     "Xoffset" and "Yoffset" are the non-normalized frame coordinates of the spatio-temporal patch
     "PatchWidth" and "PatchHeight" are the non-normalized width and height of teh spatio-temporal patch
     "descr" is the array of floats of concatenated descriptors. The size of this array depends on the enabled descriptor types. All values are from zero to one. The first comment line describes the enabled descriptor types, their order in the array, and the dimension of each descriptor in the array.
     
     Then every line corresponds to an extracted descriptor of a patch. All numbers in the output are floating point in text format and are separated by tabs.
     The standard error contains various debug / diagnostic messages like time measurements and parameters in effect.

2. Fast Fisher vector / VLAD computation using SSE2 vector CPU nstructions ("fv_fast")
Command-line options:


Building from source
====================

Dependencies for "motion_descriptors":
 - ffmpeg
 - opencv

Dependencies for "fv_fast":
 - hdf5
 - opencv